# a

| 우선 순위              | 숫자값 | 플래그                        | C#플래그                   |
|------------------------|--------|-------------------------------|----------------------------|
| 실시간(Time Critical)  | 32     | THREAD_PRIORITY_TIME_CRITICAL |                            |
| 실시간(Real Time)      | 24     | REALTIME_PRIORITY_CLASS       |                            |
| 최상(Highest)          |        | THREAD_PRIORITY_HIGHEST       | ThreadPriority.Highest     |
| 보통 초과(AboveNormal) |        | THREAD_PRIORITY_ABOVE_NORMAL  | ThreadPriority.AboveNormal |
| 보통(Normal)           | 7-9    | THREAD_PRIORITY_NORMAL        | ThreadPriority.Normal      |
| 보통 미만(BelowNormal) |        | THREAD_PRIORITY_BELOW_NORMAL  | ThreadPriority.BelowNormal |
| 낮음(Lowest)           |        | THREAD_PRIORITY_LOWEST        | ThreadPriority.Lowest      |
| 휴지(Idle)             | 1      | THREAD_PRIORITY_IDLE          |                            |


| 정적 멤버      | 설명                                                                  |
|----------------|-----------------------------------------------------------------------|
| CurrentContext | 현재 실행중인 쓰레드 컨텍스트를 가져온다.                             |
| CurrentThread  | 현재 실행중인 쓰레드의 참조를 가져온다.                               |
| GetData()      | 쓰레드의 현재 도메인에 대해서 실행중인 쓰레드의 특정 슬롯의 값을 설정 |
| SetData()      | 쓰레드의 현재 도메인에 대해서 실행중인 쓰레드의 특정 슬롯의 값을 얻기 |
| GetDomain()    | 현재 쓰레드가 실행중인 도메인에 대한 참조를 가져온다.                 |
| GetDomainID()  |                                                                       |
| Sleep()        | 현재 실행중인 쓰레드를 일정 시간 동안 중지시킨다.                     |


| 인스턴스 멤버 | 설명                                                                                                                                   |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------|
| IsAlive       | 쓰레드가 시작된 이후로 살아있는지를 알려준다.                                                                                          |
| IsBackground  | 쓰레드가 백그라운드 쓰레드인지 아닌지를 설정하거나 알려준다(ThreadState.Background).                                                   |
| Name          | 쓰레드의 이름을 설정하거나 가져올 수 있다.                                                                                             |
| Priority      | ThreadPriority 열거형에 정의된 쓰레드 우선 순위를 정의하거나 알려준다.                                                                 |
| ThreadState   | ThreadState 열거형에 정의된 쓰레드의 상태를 알려주는 읽기 전용 프로퍼티                                                                |
| Abort()       | 쓰레드를 죽일 때 사용한다. 이 메소드를 사용하면 ThreadAbortException 예외가 발생한다(ThreadState.Aborted, ThreadState.AbortRequested). |
| Interrupt()   | 현재 쓰레드를 중지시킨다.                                                                                                              |
| Join()        | 현재 쓰레드가 완료될 때까지 기다린다(ThreadState.WaitSleepJoin).                                                                       |
| Suspend()     | 쓰레드를 잠시 대기상태로 만든다(ThreadState.Suspended, ThreadState.SuspendRequested).                                                  |
| Resume()      | 대기 상태로 만든 쓰레드를 다시 활성상태로 만든다.                                                                                      |
| Start()       | ThreadStart에 위임한 쓰레드 실행을 시작한다(ThreadState.Unstarted, ThreadState.Running).                                               |


| ThreadState      |                                                                                                                               |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Unstarted        | 스레드에 Start() 메서드가 호출되지 않았습니다.                                                                                |
| Background       | 해당 스레드는 전경 스레드와 반대인 배경 스레드로 실행됩니다. 이 상태는 IsBackground 속성을 설정하여 제어합니다.               |
| Running          | 스레드가 시작되었고 아직 중지되지 않았습니다.                                                                                 |
| WaitSleepJoin    | 스레드가 차단되었습니다. .                                                                                                    |
| StopRequested    | 스레드를 중지하도록 요청했습니다. 이는 내부 전용입니다.                                                                       |
| Stopped          | 스레드가 중지되었습니다.                                                                                                      |
| SuspendRequested | 스레드를 일시 중단하도록 요청하고 있습니다.                                                                                   |
| Suspended        | 스레드가 일시 중단되었습니다.                                                                                                 |
| AbortRequested   | 스레드에 Abort(Object) 메서드가 호출되었지만 해당 스레드는 자신을 종결시키려는 보류된 ThreadAbortException을 받지 못했습니다. |
| Aborted          | 스레드 상태에 AbortRequested가 포함되어 있고 스레드가 작동하지 않지만 상태가 아직 Stopped로 변경되지 않았습니다.              |

| Action                                                                     | ThreadState      |
|----------------------------------------------------------------------------|------------------|
| A thread is created within the common language runtime.                    | Unstarted        |
| The Start method does not return until the new thread has started running. | Running          |
| The thread calls Sleep                                                     | WaitSleepJoin    |
| The thread calls Monitor.Wait on another object.                           | WaitSleepJoin    |
| The thread calls Join on another thread.                                   | WaitSleepJoin    |
| Another thread calls Interrupt                                             | Running          |
| Another thread calls Suspend                                               | SuspendRequested |
| The thread responds to a Suspend request.                                  | Suspended        |
| Another thread calls Resume                                                | Running          |
| Another thread calls Abort                                                 | AbortRequested   |


``` csharp
ThreadStart
Thread thread;
thread.IsBackground

ThreadPool
public static bool SetMinThreads (int workerThreads, int completionPortThreads);
public static bool QueueUserWorkItem (System.Threading.WaitCallback callBack, object state);
```

``` plantuml
node Unstarted
node Running
node WaitSleepJoin
node AbortRequested
node Aborted
node Stopped

Unstarted -> Running : 시작
WaitSleepJoin --> Running: 블락
WaitSleepJoin <-- Running: 언블락
WaitSleepJoin --> AbortRequested: Abort
Running -> AbortRequested : Abort
Running <- AbortRequested : ResetAbort
Running --> Stopped        : 종료
AbortRequested ..> Aborted : only in theory.
AbortRequested --> Stopped : 종료

```

// *Time taken to lock and unlock the construct once on the same thread (assuming no blocking), as measured on an Intel Core i7 860.

| Construct                           | Purpose                                                                                                  | Cross-process? | Overhead* |
|-------------------------------------|----------------------------------------------------------------------------------------------------------|----------------|-----------|
| lock (Monitor.Enter / Monitor.Exit) | Ensures just one thread can access a resource, or section of code at a time                              | -              | 20ns      |
| Mutex                               |                                                                                                          | Yes            | 1000ns    |
| SemaphoreSlim                       | Ensures not more than a specified number of concurrent threads can access a resource, or section of code | -              | 200ns     |
| Semaphore                           |                                                                                                          | Yes            | 1000ns    |
| ReaderWriterLockSlim                | Allows multiple readers to coexist with a single writer                                                  | -              | 40ns      |


| Construct            | Purpose                                                                                      | Cross-process? | Overhead*         |
|----------------------|----------------------------------------------------------------------------------------------|----------------|-------------------|
| AutoResetEvent       | Allows a thread to unblock once when it receives a signal from another                       | Yes            | 1000ns            |
| ManualResetEvent     | Allows a thread to unblock indefinitely when it receives a signal from another (until reset) | Yes            | 1000ns            |
| ManualResetEventSlim |                                                                                              | -              | 40ns              |
| CountdownEvent       | Allows a thread to unblock when it receives a predetermined number of signals                | -              | 40ns              |
| Barrier              | Implements a thread execution barrier                                                        | -              | 80ns              |
| Wait and Pulse       | Allows a thread to block until a custom condition is met                                     | -              | 120ns for a Pulse |




    Thread.MemoryBarrier();

|                             |
|-----------------------------|
| Interlocked.Increment       |
| Interlocked.Decrement       |
| Interlocked.Add             |
| Interlocked.Read            |
| Interlocked.Exchange        |
| Interlocked.CompareExchange |
 

``` plantuml
node Monitor.Enter
node Monitor.Exit
node ReadyQueue
node WaitingQueue

Monitor.Enter -> ReadyQueue
ReadyQueue -> Lock
Lock -> Monitor.Exit
Lock --> WaitingQueue
Pulse <. WaitingQueue
ReadyQueue <-- Pulse
```

Barrier barrier = new Barrier (3);
barrier.SignalAndWait();