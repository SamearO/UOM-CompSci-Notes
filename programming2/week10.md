# Concurrency 

## Threads vs processes
* Threads are lighter weight than processes.
* Threads within a process share memory and resources. 
* Threads within a process share code. 
* Multiple Threads/ multiple processes are run simultaneously through time-slicing. 

## Threads in Java
Threads implement the Runnable Interface. 

```java
// Creating and running a thread
Thread t = new Thread(new MyFunction());
t.start();
// Writing the function within the thread body: 
Thread t = new Thread(() => {
    System.out.println("Hello");
})
t.start();
```

## Thread states 
* `Ready` State is when a thread is waiting for a time slice before being run. When a time slice is available, it transitions to the `Running` state. Can be invoked by using the `start()` method that calls `run()`
* `Sleeping` state is when the thread has been told not to run for some time. `sleep(100)` is used to get to this state. 
* `Wait` can be called by using `wait()` in a loop that checks an attribute on a shared object. It is used to synchronize threads. For example it can wait for the boolean `blocked` to change to `false`. This can be accomplished by the thread using `blocked` changing blocked to `false` then calling `notify()` or `notifyAll()` to let the first thread know that blocked has changed.


## Thread synchronization

* Threads may require shared resources that can only be read to or written to serially. 
* They may also need to be synchronized using a blocking mechanism. 
* Thus the `synchronized` keyword can be used to declare that any variables used within the method body can only be used by 1 thread at once. 

## Using shared resources

* Using a combination of `wait()`, `notify()` and `synchronized`, we can have 2 threads that can operate on a shared resource one at a time

```java
boolean blocked = true;
public synchronized produce() {
    while (!blocked) {
        wait();
    }
    doProduceFunction();
    blocked = false;
    notifyAll();
}

public synchronized consume() {
    while (blocked) {
        wait();
    }
    doConsumeFunction();
    block = true;
    notifyAll();
}

Thread produce_thread = new Thread(produce());
Thread consume_thread = new Thread(consume());
produce_thread.start();
consume_thread.start(); 

```