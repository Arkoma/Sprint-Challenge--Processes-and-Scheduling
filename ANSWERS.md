1. List all of the main states a process may be in at any point in time on a
   standard Unix system. Briefly explain what each of these states mean.
> a process may be in a blocked state while it waits to be executed. 
> Once the process's turn comes in the queue, It is dequeued and executed.
> Once the time slice given to the process by the scheduler OR the process
> itself is finished, The process is killed.
2. What is a Zombie Process? How does it get created? How does it get destroyed?
> A zombie process is a process whose parent process stopped before it did.
> It will sit in memory until a reaper comes and kills the process. When a 
> parent process goes to destory it's children it will also clean up any
> zombie processes left in memory.
3. Describe the job of the Scheduler in the OS in general.
> Despite apperances to the contrary, a cpu cannot process two things 
> simultaneously.
>
> In order to appear as if it can process two things simultaneously,
> the scheduler tries to schedule the completion of processes in a fair and 
> responsive manner. If the scheduler runs too efficiently for process
> then it loses responsiveness, because it has to wait for whatever
> is currently running to complete before it can, for example recieve
> a mouse movement.  Howeever, if the machine only responds to interactive
> processes, then processes that take some extra cpu time and resources
> will never get run.
4. Describe the benefits of the MLFQ over a plain Round-Robin scheduler.
> one of the best answers to the scheculer problem is a data structure 
> called a multi-level-feedback-queue, or MLFQ. It improves on a plain
> Round-Robin scheduler by helping the system to prioritize shorter
> jobs first by 'predicting' which jobs will be shorter. A Round-Robin
> schedulre gives better response time than just a plain fifo or lifo
> queue, because it means that the computer is responding at regular
> intervals no matter how long a process will take. The MLFQ uses a 
> Round-Robin schedule, but also has multiple queues going at the same
> time to prioritize shorter jobs. Queues towards the top of the stack
> of queues have shorter time slices and jobs that can get finished 
> within those time slices or quantams are dequeued quickly, and jobs
> that still need to be completed but have reached the end of the quantam
> are knocked down to a lower priority queue. On modern machines they 
> may have hundreds of queues of processes going at the same time with
> each one having incrementally longer time slices. This tries to 
> increase turnaround time while at the same time allowing the machine
> to stay responsive. A good MLFQ has to also both account for processes
> that may try to game the system by making shorter run times so that 
> the process continues to be moved to a lower queue no matter how
> many times it has given up time to the cpu. Also the MLFQ can 
> try to make the system more fair to processes that need longer CPU time
> by periodically boosting all processes back up to the top queue.
