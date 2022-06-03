---
title: "Java Concurrent"
date: 2021-3-18T08:11:45Z
draft: false
tags: ["java"]
categories: ["note"]
---

## Introduction

### Thread's advantage

1. unleash the performance of processor
2. simplification of modeling
3. simplified handling of asynchronous events
4. responsive user interface

### Thread's disadvantage

1. security problems
2. activation problems
3. performance problems

## Thread Safety

keyword *synchronized* *volatile*

solve problems of multiple threads access mutable variables:

* don't share the variable in threads
* change the variable to immutable
* use sync when access variables

**Thead Safety**: When multiple threads access a class, no longer the running environment uses any scheduling methods or the threads alternately execute, and the main code needn't any other sync or synergy, the class can perform rightly.

Sateless object is thread safe.

### Atomic

Race condition: Check-Then-Act.

### Lock

Built-in lock: **synchronized**. equivalent to a mutual exclusion lock. can re-entry. 

## Sharing of Object

### Visibility

use **volatile**

don't let *this* escape when construct.

### Thread Closure

Ad-hoc thread closure.  
Stack closure.  
ThreadLocal

### Immutability

Immutable object must be thread safe.

## Composition of Object

* find all variables constructing the object status
* find the immutable condition binging status variables
* build concurrent manage strategies of object status

## Basic Building Blocks

1. Sync container class (Vector and Hashtable)
2. Concurrent container class (ConcurrentHashMap CopyOnWriteArrayList)
3. Blocking queue ans Producer and Customer
4. Blocked method and Interrupted method
5. Sync util class

## Task execution

### Execute task in thread

Serial execution, create explicitly thread for task.

Disadvantage of infinite threads

* Thread lifecycle overhead high
* resource consumption
* stability

### Executor framework

```java
    public interface Executor {
        void execute(Runnable command)
    }
```

Thread pool: use static methods in class `Executor`

* `newFixedThreadPool` create a fixed length pool
* `newCachedThreadPool` create a pool can cache
* `newSingleThreadExecutor` create a single thread executor
* `newScheduledThreadPool` schedule tasks

use `shutdown()` in `interface ExecutorService extents Executor` to shutdown an executor.

Executor has three status in lifecycle,running, closed, terminated.

### Find available concurrent

`Callback and Future`

`CompletionService` include `Executor` and `BlockingQueue`. use blocked method `take` and `poll` get result.

## Cancel and Close

### Task cancel

cancel reasons:

* user request cancel
* operation with time limit
* application event
* error
* close

interrupt methods:

* response interrupt (wait, sleep)
* use Future implement cancel

uninterrupted block

1. Java.io sync Socket I/O
2. Java.io sync I/O
3. Selector async I/O
4. get some lock

package standard cancel operation to process uninterrupted block.

use `newTaskFor` to package substandard cancel

### Stop service based on thread

