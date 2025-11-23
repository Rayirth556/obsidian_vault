waiting time of the current process is the turnaround time of the previous process


wt[i] = bt[i-1] + w[i-1]



Priority scheduling : 
we initiate these arrays

pid, pr(process priority), bt, tat, wt
in main function
step 1 : sort by priority order
step 2: calculate waiting time , first set waiting time of p1 as 0 then init for loop

step 3: caluclate turnaround time using for loop
tat[i] = wt[i] + bt[i]
total_wt += wt[i]
total_tat += tat[i]


SHORTEST JOB FIRST
Process with the smallest burst time gets executed first 



FOr shortest job first 
use the follwing algo

create a function to sort processes by burst time

swap burst times using temp variable
swap process id too 


IN PREEMPTIVE ROUND ROBIN SCHEDULING
Every process gets assigned a time slice quantum 

if a process doesn’t finish in its time slice,  
it’s sent back to the **ready queue** to wait for the next turn.

For round robin scheduling
follwing are the arrays we declare

burst time , waiting time, remaining time, tq(time quantum), sq(total cpu time elapsed)
