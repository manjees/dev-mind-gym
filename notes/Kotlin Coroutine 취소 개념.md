# Kotlin Coroutine 취소 개념

### 1. 기본 개념 Job vs CoroutineScope
- Job : 개별 coroutine 하나를 나타냄, launch나 async로 생성되며, 이 코루틴 하나만 제어 가능 (취소, 상태 확인, 대기 등)
- CoroutineScope : 여러 개의 코루틴을 포함하는 "컨테이너" 역할을 함. 내부에는 Job이 포함되어 있어서, 전체 스코프의 생명주기를 관리
> "CoroutineScope = 매니저 (관리자)"  "Job = 직원 (개별 작업자) -> 매니저(스코프)를 해고하면 모든 직원(코루틴)이 종료됨

### 2. 예제
```kotlin
// 단일 Job 취소 (job.cancel())
/*
* jobA는 취소되고
* jobB는 그대로 실행됨
* scope는 여전히 살아있고, 다른 코루틴도 계속 만들 수 있음
*/

val scope = CoroutineScope(Dispatchers.Default)

val jobA = scope.launch {
  delay(5000)
  println("Job A done")
}

val jobB = scope.launch {
  delay(10000)
  println("Job B done")
}

jobA.cancel()
```
```kotlin
// 스코프 전체 취소
/*
* jobA, jobB 모두 취소됨
* 스코프가 비활성화됨 -> 이후 launch {}는 실행되지 않음
* 내부 Job이 취소 상태로 들어감
*/

val scope = CoroutineScope(Dispatcher.Default)

val jobA = scope.launch { ... }
val jobB = scope.launch { ... }

(scope.coroutineContext[Job] ?: error("No Job")).cancel()
// 또는 MainScope() 또는 ViewModelScope에서는
scope.cancel()
```
> 주의: CoroutineScope 자체는 cancel() 메소드를 정의하지 않음.  -> Job을 가져와서 직접 cancel() 하거나, MainScope처럼 노출된 API 사용

### 3. 스코프가 취소된 후의 동작
- 새로운 코루틴은 실행되지 않음
- 스코프는 비활성 상태
- Android에서는 Activity/Fragment/ViewModel 생명주기에 따라 스코프가 자동으로 취소됨

### 4. 현실적인 비유
- Job.cancel() -> "안나(직원)야, 지금 하던 일 그만해"
- Scope의 Job을 cancel() -> "공장 문 닫자, 모든 사람 퇴근!"

### 5. 언제 어떤 걸 써야할까?
- 특정 코루틴만 취소하고 싶을 때 -> job.cancel()
- 전체 작업 중단 및 스코프 비활성화 -> scope.cancel() 또는 내부 Job 취소
- Android에서 생명주기 기반 클린업 -> viewModelScope, lifecycleScope 사용 (자동 취소)
- 수동으로 관리하는 스코프가 필요할 때 -> CoroutineScope + Job, 그리고 명시적 cancel() 호출 필요

### 6. Android에서의 권장 패턴
- viewModelScope -> ViewModel이 소멸되면 자동 취소
- lifecycleScope -> Activity/Fragment가 파괴되면 자동 취소

### 7. 출처
- https://proandroiddev.com/kotlin-coroutines-the-real-difference-between-job-cancel-and-scope-cancel-05e1d9dd5245