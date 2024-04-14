
- real 真实的耗时
- user 用户态cpu核心的耗时 //包含多个运行的核心
- sys  内核态cpu核心的耗时 //包含多个运行的核心

可以从证明，多子进程和多线程，在多核心环境下是可以实现并发运行的。

```shell
real    0m0.564s
user    0m0.772s
sys     0m0.000s
```

taskset
>  taskset - set or retrieve a process's CPU affinity

可以指定某个进程的运行的cpu核心数亲和性。实现某个进程及其子进程，线程，只占用一个cpu核心数。


指定进程只运行在单个核心后，real和user的运行时间差不多。
> `time taskset -c 1  ./sched_nice 200 2`
```shell
real    0m0.761s
user    0m0.761s
sys     0m0.000s
```