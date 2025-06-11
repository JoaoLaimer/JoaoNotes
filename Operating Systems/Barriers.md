A barrier is a synchronization mechanism that blocks threads from going forward until all threads reach the barrier.
Once all threads reach the barrier they are green lit, and the barrier is lifted.
In the pthreads library we use the `pthread_barrier_wait()` function.
