

## Table of contents : 


- [nOS Modules :](#nos-modules-)
    - [nOS_Alarm](#nos_alarm)
    - [nOS_Barrier](#nos_barrier)
    - [nOS_Event](#nos_event)
    - [nOS_Flag](#nos_flag)
    - [nOS_List](#nos_list)
    - [nOS_Mem](#nos_mem)
    - [nOS_Mutex](#nos_mutex)
    - [nOS_Queue](#nos_queue)
    - [nOS_Sched](#nos_sched)
    - [nOS_Sem](#nos_sem)
    - [nOS_Signal](#nos_signal)
    - [nOS_Thread](#nos_thread)
    - [nOS_Time](#nos_time)
    - [nOS_Timer](#nos_timer)


## nOS Modules :
### [nOS_Alarm](/wiki/nos_alarm)
```c
void nOS_InitAlarm(void);
void nOS_AlarmTick (void);
void nOS_AlarmProcess (void);
nOS_Error nOS_AlarmCreate (nOS_Alarm *alarm, nOS_AlarmCallback callback, void *arg, nOS_Time time);
nOS_Error nOS_AlarmDelete (nOS_Alarm *alarm);
nOS_Error nOS_AlarmSetTime (nOS_Alarm *alarm, nOS_Time time);
nOS_Error nOS_AlarmSetCallback (nOS_Alarm *alarm, nOS_AlarmCallback callback, void *arg);
```


### [nOS_Barrier](/wiki/nos_barrier)
```c
nOS_Error nOS_BarrierCreate (nOS_Barrier *barrier, uint8_t max);
nOS_Error nOS_BarrierDelete (nOS_Barrier *barrier);
nOS_Error nOS_BarrierWait (nOS_Barrier *barrier);
```

### [nOS_Event](/wiki/nos_event)
```c
void nOS_DeleteEvent (nOS_Event *event);
void nOS_BroadcastEvent (nOS_Event *event, nOS_Error err);
nOS_Thread* nOS_SendEvent (nOS_Event *event, nOS_Error err);
```

### [nOS_Flag](/wiki/nos_flag)
```c
nOS_Error nOS_FlagCreate (nOS_Flag *flag, nOS_FlagBits flags);
nOS_Error nOS_FlagDelete (nOS_Flag *flag);
nOS_Error nOS_FlagSend (nOS_Flag *flag, nOS_FlagBits flags, nOS_FlagBits mask);
```
### [nOS_List](/wiki/nos_list)
```c
void nOS_AppendToList (nOS_List *list, nOS_Node *node);
void nOS_RemoveFromList (nOS_List *list, nOS_Node *node);
void nOS_RotateList (nOS_List *list);
void nOS_WalkInList (nOS_List *list, nOS_NodeHandler handler, void *arg);
```

### [nOS_Mem](/wiki/nos_mem)
```c
nOS_Error nOS_MemCreate (nOS_Mem *mem, void *buffer, nOS_MemSize bsize, nOS_MemCounter bmax);
nOS_Error nOS_MemDelete (nOS_Mem *mem);
void *nOS_MemAlloc(nOS_Mem *mem, nOS_TickCounter timeout);
nOS_Error nOS_MemFree(nOS_Mem *mem, void *block);
bool nOS_MemIsAvailable (nOS_Mem *mem);
```

### [nOS_Mutex](/wiki/nos_mutex)
```c
nOS_Error nOS_MutexDelete (nOS_Mutex *mutex);
nOS_Error nOS_MutexLock (nOS_Mutex *mutex, nOS_TickCounter timeout);
nOS_Error nOS_MutexUnlock (nOS_Mutex *mutex);
bool nOS_MutexIsLocked (nOS_Mutex *mutex);
nOS_Thread* nOS_MutexGetOwner (nOS_Mutex *mutex);
```

### [nOS_Queue](/wiki/nos_queue)
```c
nOS_Error nOS_QueueCreate (nOS_Queue *queue, void *buffer, uint8_t bsize, nOS_QueueCounter bmax);
nOS_Error nOS_QueueDelete (nOS_Queue *queue);
nOS_Error nOS_QueueRead (nOS_Queue *queue, void *block, nOS_TickCounter timeout);
nOS_Error nOS_QueuePeek (nOS_Queue *queue, void *block);
nOS_Error nOS_QueueWrite (nOS_Queue *queue, void *block, nOS_TickCounter timeout);
nOS_Error nOS_QueueFlush (nOS_Queue *queue, nOS_QueueCallback callback);
bool nOS_QueueIsEmpty (nOS_Queue *queue);
bool nOS_QueueIsFull (nOS_Queue *queue);
nOS_QueueCounter nOS_QueueGetCount (nOS_Queue *queue);
```

### [nOS_Sched](/wiki/nos_sched)
```c
nOS_Error nOS_Schedule(void);
nOS_Error nOS_Init(void);
nOS_Error nOS_Start(void);
nOS_Error nOS_Yield(void);
void nOS_Tick(nOS_TickCounter ticks);
nOS_TickCounter nOS_GetTickCount(void);
uint32_t nOS_MsToTicks (uint16_t ms);
nOS_Error nOS_Sleep (nOS_TickCounter ticks);
nOS_Error nOS_SleepMs (uint16_t ms);
nOS_Error nOS_SleepUntil (nOS_TickCounter tick);
nOS_Error nOS_SchedLock(void);
nOS_Error nOS_SchedUnlock(void);
nOS_Thread * nOS_GetRunningThread (void);
```

### [nOS_Sem](/wiki/nos_sem)
```c
nOS_Error nOS_SemCreate (nOS_Sem *sem, nOS_SemCounter count, nOS_SemCounter max);
nOS_Error nOS_SemDelete (nOS_Sem *sem);
nOS_Error nOS_SemTake (nOS_Sem *sem, nOS_TickCounter timeout);
nOS_Error nOS_SemGive (nOS_Sem *sem);
bool nOS_SemIsAvailable (nOS_Sem *sem);
```

### [nOS_Signal](/wiki/nos_signal)
```c
void nOS_InitSignal (void);
void nOS_SignalProcess (void);
nOS_Error nOS_SignalDelete (nOS_Signal *signal);
nOS_Error nOS_SignalSend (nOS_Signal *signal, void *arg);
nOS_Error nOS_SignalSetCallback (nOS_Signal *signal, nOS_SignalCallback callback);
nOS_Error nOS_SignalSetPrio (nOS_Signal *signal, uint8_t prio);
bool nOS_SignalIsRaised (nOS_Signal *signal);
```

### [nOS_Thread](/wiki/nos_thread)
```c
void nOS_TickThread (void *payload, void *arg);
void nOS_WakeUpThread (nOS_Thread *thread, nOS_Error err);
int nOS_ThreadWrapper (void *arg);
void nOS_SetThreadPrio (nOS_Thread *thread, uint8_t prio);
nOS_Error nOS_ThreadDelete (nOS_Thread *thread);
nOS_Error nOS_ThreadAbort (nOS_Thread *thread);
nOS_Error nOS_ThreadSuspend (nOS_Thread *thread);
nOS_Error nOS_ThreadResume (nOS_Thread *thread);
nOS_Error nOS_ThreadSuspendAll (void);
nOS_Error nOS_ThreadResumeAll (void);
nOS_Error nOS_ThreadSetPriority (nOS_Thread *thread, uint8_t prio);
int16_t nOS_ThreadGetPriority (nOS_Thread *thread);
const char* nOS_ThreadGetName (nOS_Thread *thread);
nOS_Error nOS_ThreadSetName (nOS_Thread *thread, const char *name);
nOS_Error nOS_ThreadJoin (nOS_Thread *thread, int *ret, nOS_TickCounter timeout);
```

### [nOS_Time](/wiki/nos_time)
```c
void nOS_InitTime (void);
void nOS_TimeTick (nOS_TickCounter ticks);
nOS_Time nOS_TimeGet (void);
nOS_Error nOS_TimeSet (nOS_Time time);
nOS_TimeDate nOS_TimeConvert (nOS_Time time);
nOS_Error nOS_TimeWait (nOS_Time time);
bool nOS_TimeIsLeapYear(uint16_t year);
uint16_t nOS_TimeGetDaysPerYear(uint16_t year);
uint8_t nOS_TimeGetDaysPerMonth(uint8_t month, uint16_t year);
nOS_TimeDate nOS_TimeDateGet (void);
nOS_Error nOS_TimeDateSet (nOS_TimeDate timedate);
nOS_Time nOS_TimeDateConvert (nOS_TimeDate timedate);
nOS_Error nOS_TimeDateWait (nOS_TimeDate timedate);
```

### [nOS_Timer](/wiki/nos_timer)
```c
void nOS_InitTimer(void);
void nOS_TimerTick (nOS_TickCounter ticks);
void nOS_TimerProcess (void);
nOS_Error nOS_TimerDelete (nOS_Timer *timer);
nOS_Error nOS_TimerStart (nOS_Timer *timer);
nOS_Error nOS_TimerStop (nOS_Timer *timer, bool instant);
nOS_Error nOS_TimerRestart (nOS_Timer *timer, nOS_TimerCounter reload);
nOS_Error nOS_TimerPause (nOS_Timer *timer);
nOS_Error nOS_TimerContinue (nOS_Timer *timer);
nOS_Error nOS_TimerSetReload (nOS_Timer *timer, nOS_TimerCounter reload);
nOS_Error nOS_TimerSetCallback (nOS_Timer *timer, nOS_TimerCallback callback, void *arg);
nOS_Error nOS_TimerSetMode (nOS_Timer *timer, nOS_TimerMode mode);
nOS_Error nOS_TimerSetPrio (nOS_Timer *timer, uint8_t prio);
bool nOS_TimerIsRunning (nOS_Timer *timer);
```