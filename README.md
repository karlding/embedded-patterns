# Embedded Patterns

A curated collection of embedded design patterns, recipes and idioms. Although the examples are primariliy written in C, the concepts behind each pattern should be applicable to other languages, even if the implementation may differ.

Each page follows the format from the Gang of Four book, and contains these sections:

* *Intent* - What is the problem this pattern solves?
* *Motivation* - A longer, motivating example problem and a simple description of the pattern
* *Applicability* - Situations in which this pattern might be useful
* *Structure* - Specifically, how does the pattern look or how might you implement it? 

## Creational Patterns

| Pattern | Description |
|:------- |:-----------|
| [Object Pool](/creational/object-pool.md) | Instantiates and maintains a group of objects instances of the same type |

## Behavioural Patterns

| Pattern | Description |
|:------- |:-----------|
| [Control Table](/behavioural/controltable.md) | Direct program control flow in some way through "execution" by a processor or interpreter |
| [State Machine](/behavioural/statemachine.md) | Encapsulates varying behavior for the same object based on its internal state |

## Synchronization Patterns

| Pattern | Description |
|:------- |:-----------|
| [Lock/Mutex](/synchronization/mutex.md) | Enforces mutual exclusion limit on a resource to gain exclusive access |

## Reliability Patterns

| Pattern | Description |
|:------- |:-----------|
| [Cyclic Redundancy Check](/reliability/crc.md) | Checks that the data matches a checksum |

## Hardware Access Patterns

| Pattern | Description |
|:------- |:-----------:|
| [Debouncing](/hardware/debouncing.md) | Reject multiple false input events |
