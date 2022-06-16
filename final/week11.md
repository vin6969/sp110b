## Deadlock

In an operating system, a deadlock occurs when a process or thread enters a waiting state because a requested system resource is held by another waiting process, which in turn is waiting for another resource held by another waiting process.
If a process remains indefinitely unable to change its state because resources requested by it are being used by another process that itself is waiting, then the system is said to be in a deadlock.
In a communications system, deadlocks occur mainly due to loss or corruption of signals rather than contention for resources.

```
Two processes competing for two resources in opposite order.
1.A single process goes through.
2.The later process has to wait.
3.A deadlock occurs when the first process locks the first resource at the same time as the second process locks the second resource.
4.The deadlock can be resolved by cancelling and restarting the first process.
```
![](img/deadlock2.gif)

#### source
https://en.wikipedia.org/wiki/Deadlock

<br>
<br>
```
Four processes (blue lines) compete for one resource (grey circle), following a right-before-left policy.
A deadlock occurs when all processes lock the resource simultaneously (black lines). The deadlock can be resolved by breaking the symmetry.
```


![](img/deadlock21.gif)



### Zombie Process

A zombie process is a process whose execution is completed but it still has an entry in the process table. Zombie processes usually occur for child processes, as the parent process still needs to read its child’s exit status. Once this is done using the wait system call, the zombie process is eliminated from the process table. This is known as reaping the zombie process.

![](img/zombiepro.png)

#### source 
https://www.tutorialspoint.com/what-is-zombie-process-in-linux





### Race Condition
So far, we have used C# to implement the concepts of Thread and Deadlock in the operating system, but in fact, there is a relationship between these two concepts. To understand the relationship between Thread and deadlock, we must start from the Race Condition (competition situation) this issue.

In the case of multiple threads (or multiple CPUs), two threads can share some variables, but sharing variables may cause a serious problem, that is, when two threads modify a variable at the same time, this modification will cause variable The value of may be wrong, the following is an example.

```
| |T2:counter=R1 |T2:R1 = R1-1            
          | |T1:R1 = R1+1 |T2:counter = R1         
          | |T1:counter = R1 |T1:counter = R1         
          | |... |...                     
          | |Execution result: counter = 0 |Execution result: counter = -1
```
  
|high-level|language	combined language	|corresponding action|
|----------|----------------------------|--------------------|
|          | counter++	LD R1, counter  |	R1 = counter       |
|          |     ADD R1, R1, 1          |R1 = R1 + 1         |
|          |        ST R1, counter	    |counter = R1        |

#### source
https://kinmen6.com/root/%E9%99%B3%E9%8D%BE%E8%AA%A0/%E6%9B%B8%E7%B1%8D/C%EF%BC%83%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88/thread.md
