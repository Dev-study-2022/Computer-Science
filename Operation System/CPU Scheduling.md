# CPU Scheduling
### 스케줄링
> CPU를 잘 사용하기 위해 프로세스를 잘 배정하기    

- 조건: 오버헤드와 기아 현상은 낮추되, CPU 사용률은 높인다
- 목표
    1. Batch System: 가능한 많은 일을 수행. 시간보단 처리량(throughout)이 중요
    2. Interactive System: 빠른 응답 시간과 적은 대기 시간
    3. Real-time System: 기한(deadline) 맞추기

<code>💡 기아 현상(Starvation): 특정 프로세스의 우선 순위가 낮아서 원하는 자원을 계속 할당받지 못하는 상태</code>

### 선점/비선점 스케줄링
1. 선점(preemptive): OS가 CPU의 사용권을 선점, 강제 회수 가능 (처리시간 예측 어려움)
2. 비선점(non-preemptive): 프로세스 종료 or I/O 등의 이벤트가 있을 때까지 실행 보장 (처리시간 예측 용이)

### 프로세스 상태
![process_state.png](../resource/process_state.png)
- 비선점 스케줄링: `Interrupt`, `Scheduler Dispatch`
- 선점 스케줄링: `I/O or Event Wait`

**프로세스 상태 전이**
1. 승인(Admitted): 프로세스 생성이 가능하여 승인됨
2. 스케줄러 디스패치(Scheduler Dispatch): 준비 상태에 있는 프로세스 중 하나를 선택해 실행시키는 것
3. 인터럽트(Interrupt): `예외`, `입출력`, `이벤트` 등이 발생하여 현재 실행 중인 프로세스를        
준비 상태로 바꾸고, 해당 작업을 먼저 처리하는 것
4. 입출력 또는 이벤트 대기(I/O or Event wait): `실행 중인 프로세스가` 입출력이나      
이벤트를 처리해야 하는 경우, 입출력/이벤트가 모두 끝날 때까지 대기 상태로 만드는 것
5. 입출력 또는 이벤트 완료(I/O or Event Completion): 입출력/이벤트가 끝난 프로세스를        
준비 상태로 전환해 스케줄러에 의해 선택될 수 있도록 만드는 것