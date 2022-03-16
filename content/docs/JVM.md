---
title: "JVM"
date: 2022-02-28T08:36:14Z
draft: false
tags: ["java","jvm"]
categories: ["note"]
---

## Java Memory

### Runtime Data Field

Program Counter Register. Thread private. Save current executed bytecode address.  If program is executing Java method, the counter record virtual machine bytecode address. Else if *native* method, the counter's value is *Undefined*.

Java Virtual Machine Stack. Thread private. Every time executing a *method*, JVM create a **Stack Frame** saving local variable table, operator number stack, dynamic link, method out, and so on. Local variable table save JVM basic data type in compile time, object reference. If thread request stack depth larger than virtual machine permitted, throw StackOverflowError; If JVM stack can expend dynamically and can't apply more memory, throw OutOfMemoryError.

Native Method Stack. Like JVM Stack, but serve for native method. HotSpot combine JVM Stack with Native Method Stack.

Java Heap. It allocate memory for almost all objects in Java. It's alias is GC heap (Garbage Collected Heap).

Method Area. Thread shared. It saves type info, constant, static variable, code cache, etc. If method area can't satisfy need for memory, throw OutOfMemoryError.

Runtime Constant Pool. A part of Method Area.

Direct Memory. Not a part of JVM runtime data. Java NIO. Allocate memory out of heap.

### Object

Object Memory Allocation Method:

1. Bump The Pointer
2. Free List
3. Thread Local Allocation

Object Header saves meta-data,hash code,GC age, etc.

memory layout: *Header*, *Instance Data*, *Padding*.

Header includes two types, object runtime data and type pointer.

Instance data save object's real data.

Access object: handle pointer and direct pointer.

## Garbage Collection

Reachability Analysis.

