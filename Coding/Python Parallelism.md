
_Python's threading module does not achieve true parallelism due to the Global Interpreter Lock (GIL). The GIL is a mutex that only allows one thread to execute Python bytecode at a time, even on multi-core processors._
# threading

Based on a single process, with multiple threading capabilities. The `threading` module on python implements basic methods for creating and handling threads in a python program, that is, creating a Thread object, which needs to be specified a function to it and the parameters of the function on its constructor:

```Python
t = Thread(target=func, args=(arg1, arg2,))
```

The new `Thread` object has methods for starting the thread (`.start()`) and waiting for it to finish (`.join()`).
It can also get identification of the thread using `.get_ident()` and checking if the thread is still running using `is_alive()`.

**Lock Objects**

The threading package includes locking, which manage the handling of resources by multiple threads. A primitive lock is in one of two states, "locked" or "unlocked". It is created in the unlocked state. It has two basic methods, `acquire()` and `release()`. When the state is unlocked, `acquire()` changes the state to locked and returns immediately. When the state is locked, `acquire()` blocks until a call to `release()` in another thread changes it to unlocked, then the `acquire()` call resets it to locked and returns.
The package also includes RLock (Reentrant Lock) objects. A reentrant lock must be released by the thread that acquired it. Once a thread has acquired a reentrant lock, the same thread may acquire it again without blocking; the thread must release it once for each time it has acquired it.

**Semaphore Objects**

This is one of the oldest synchronization primitives in the history of computer science, invented by the early Dutch computer scientist Edsger W. Dijkstra (he used the names `P()` and `V()` instead of [`acquire()`](https://docs.python.org/pt-br/3.13/library/threading.html#threading.Semaphore.acquire "threading.Semaphore.acquire") and [`release()`](https://docs.python.org/pt-br/3.13/library/threading.html#threading.Semaphore.release "threading.Semaphore.release")). A semaphore manages an internal counter which is decremented by each `acquire()` call and incremented by each `release()` call. The counter can never go bellow zero; when `acquire()` finds that it is zero, it blocks, waiting until some other thread calls `release()`.

**Event Objects**

Manages flags for communication between threads: one thread signals an event and other wait for it.
Can be set with the `set()` method and reset with `clear()`. The `wait()` method blocks until the flag is true.

# multiprocessing

Is a package similar to threading but other than using threads it creates new processes.
It possesses the same synchronization primitives as the threading module. Having semaphores, locks, events and others. For communicating between other processes, it is implemented Connection Objects using Pipe with the methods `send() recv() fileno() send_bytes() recv_bytes()` between processes.