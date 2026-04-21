# 4.8 Parallel Computing

From the 1970s through the mid-2000s, processor core speeds grew exponentially, primarily through increased clock frequency. However, this trend halted in the mid-2000s due to power and thermal limitations. Instead of faster cores, CPU manufacturers began integrating multiple cores into single processors to enable concurrent operations.

Modern multi-core systems require individual applications to leverage parallelism for performance gains. Within programs, computation must be structured to maximize parallel work. However, parallelism introduces significant challenges, particularly when dealing with shared, mutable state.

Functional programming approaches with no shared mutable state work well for parallelism. Pure functions provide referential transparency, allowing expressions to be substituted by their values without affecting program behavior.

## 4.8.1 Parallelism in Python

Python offers two approaches for parallel execution: threading and multiprocessing.

**Threading**

In threading, multiple execution threads exist within a single interpreter. Each thread runs code independently while sharing the same data. However, the CPython interpreter processes only one thread at a time, switching between them to create the illusion of parallelism. Operations external to the interpreter—such as file I/O or network access—may run in parallel.

```python
>>> import threading
>>> def thread_hello():
        other = threading.Thread(target=thread_say_hello, args=())
        other.start()
        thread_say_hello()

>>> def thread_say_hello():
        print('hello from', threading.current_thread().name)

>>> thread_hello()
hello from Thread-1
hello from MainThread
```

**Multiprocessing**

Python also supports multiprocessing, allowing programs to spawn multiple interpreters (processes) that run code independently. Processes typically don't share data; any shared state requires explicit inter-process communication. Processes execute in parallel according to the underlying operating system and hardware.

```python
>>> import multiprocessing
>>> def process_hello():
        other = multiprocessing.Process(target=process_say_hello, args=())
        other.start()
        process_say_hello()
```

## 4.8.2 The Problem with Shared State

Consider a simple counter shared between two threads:

```python
import threading
from time import sleep

counter = [0]

def increment():
    count = counter[0]
    sleep(0) # try to force a switch to the other thread
    counter[0] = count + 1

other = threading.Thread(target=increment, args=())
other.start()
increment()
print('count is now: ', counter[0])
```

The CPython interpreter can switch between threads at almost any time. A potential problematic sequence:

```
Thread 0                    Thread 1
read counter[0]: 0
                            read counter[0]: 0
calculate 0 + 1: 1
write 1 -> counter[0]
                            calculate 0 + 1: 1
                            write 1 -> counter[0]
```

The result is a counter value of 1 despite two increments. This exemplifies a **race condition**—a situation where one thread accesses mutable data while another thread simultaneously modifies it.

## 4.8.3 When No Synchronization is Necessary

Read-only data requires no synchronization since it's never modified. In rare cases, mutable shared data may not require synchronization, though this demands deep understanding of interpreter, software, and hardware behavior.

## 4.8.4 Synchronized Data Structures

The simplest synchronization approach uses data structures providing synchronized operations. The queue module's `Queue` class provides synchronized first-in, first-out access:

```python
from queue import Queue

queue = Queue()

def synchronized_consume():
    while True:
        print('got an item:', queue.get())
        queue.task_done()

def synchronized_produce():
    consumer = threading.Thread(target=synchronized_consume, args=())
    consumer.daemon = True
    consumer.start()
    for i in range(10):
        queue.put(i)
    queue.join()
```

## 4.8.5 Locks

When a synchronized data structure version isn't available, programmers must provide custom synchronization. A lock is a fundamental mechanism allowing acquisition by at most one thread at a time.

Python's `threading` module provides a Lock class with acquire and release methods. For a lock to protect data, all threads must follow one rule: no shared data access without owning the lock.

```python
seen = set()
seen_lock = threading.Lock()

def already_seen(item):
    with seen_lock:
        if item not in seen:
            seen.add(item)
            return False
        return True
```

The `with` statement acquires the lock before executing its suite and releases it when exiting for any reason.

## 4.8.6 Barriers

A barrier divides programs into phases by requiring all threads to reach it before any proceed. Code executing after a barrier cannot run concurrently with code before it.

```python
counters = [0, 0]
barrier = threading.Barrier(2)

def count(thread_num, steps):
    for i in range(steps):
        other = counters[1 - thread_num]
        barrier.wait() # wait for reads to complete
        counters[thread_num] = other + 1
        barrier.wait() # wait for writes to complete
```

Reading and writing occur in different phases separated by barriers.

## 4.8.7 Message Passing

A final mechanism avoiding improper shared data mutation is eliminating concurrent access entirely. Python's `multiprocessing` module provides Pipe class for inter-process communication:

```python
def process_consume(in_pipe):
    while True:
        item = in_pipe.recv()
        if item is None:
            return
        print('got an item:', item)

def process_produce():
    pipe = multiprocessing.Pipe(False)
    consumer = multiprocessing.Process(target=process_consume, args=(pipe[0],))
    consumer.start()
    for i in range(10):
        pipe[1].send(i)
    pipe[1].send(None) # done signal
```

A `None` message signals communication end.

## 4.8.8 Synchronization Pitfalls

**Under-synchronization**: Failing to properly synchronize shared accesses. Operations that must be atomic need to synchronize together.

**Over-synchronization**: Prevents non-conflicting operations from running concurrently. Acquiring a master lock at thread start and releasing at completion serializes entire code so nothing runs in parallel.

**Deadlock**: A situation where multiple threads or processes are stuck waiting for each other to finish. A circular wait creates deadlock:

```python
def deadlock(in_pipe, out_pipe):
    item = in_pipe.recv()  # Both processes block here
    print('got an item:', item)
    out_pipe.send(item + 1)
```

If both processes attempt receiving data first, and neither has sent anything, both wait indefinitely for the other—resulting in deadlock.

## 4.8.9 Conclusion

Parallelism presents significant challenges for writing correct, efficient code. As hardware parallelism increases, individual applications must handle parallel computation. This section provides a basic introduction to this crucial computer science area.


---

## Same Chapter

- [Ch4 1 Introduction](ch4-1-introduction.md)
- [Ch4 2 Implicit Sequences](ch4-2-implicit-sequences.md)
- [Ch4 3 Declarative Programming](ch4-3-declarative-programming.md)
- [Ch4 4 Logic Programming](ch4-4-logic-programming.md)
- [Ch4 5 Unification](ch4-5-unification.md)
- [Ch4 6 Distributed Computing](ch4-6-distributed-computing.md)
- [Ch4 7 Distributed Data Processing](ch4-7-distributed-data-processing.md)
