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


<br>
<br>
```
Four processes (blue lines) compete for one resource (grey circle), following a right-before-left policy.
A deadlock occurs when all processes lock the resource simultaneously (black lines). The deadlock can be resolved by breaking the symmetry.
```


![](img/deadlock21.gif)




