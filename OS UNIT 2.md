SEMAPHORE : A mechanism that controls how many processes or threads can access a specific resource at the same time or at one particular time 

Components of a semaphore:
1) Integer value ( A counter ) : This counter represents the number of available resources or permits.
2) Two atomic operations : 
		1) wait() / acquire() : Decrements the counter. If the thread becomes negative, the thread is blocked until it becomes non negative
		2) signal() / release() : Increments the counter or wakes up a waiting thread if there exists any

Types of semaphores:
Binary semaphore ( mutex ) : 
A binary semaphore only has two values 0 or 1 
1 means the resource is available and 0 means that the resource is unavailable.
Used in mutual exclusion

Mutual exclusion : It is the property of concurrent systems that ensure that a shared resource or critical section is accessed by only one process or thread at the same time. It prevents race conditions and data inconsistancies when multiple processes attempt to modify a single data 


Requirements of mutual exclusion:
No two processes can be in the shared resource simultaneously

If no process is in the critical section than one of the waiting processes must be allowed to enter the critical section 

A process should not wait indefinitely to enter the critical section , no starvation 



5 states of a process:

Running, ready, waiting, new, exit

Running : A process is being executed by the cpu 
Ready : the process is in the ready queue and it is waiting for the cpu to execute it 
Waiting : A process cannot continue execution until an event occurs like the completion of an io operation.
New : The pcb of a process is created but it has not yet entered the main memory
Exit : A process or a job that has been released by the os, either because it has completed its job or aborted because of some issue.

![[Pasted image 20251111134851.png]]

