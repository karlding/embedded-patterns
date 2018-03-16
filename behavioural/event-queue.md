# Event Queue Pattern

## Intent

Decouple a message or event from where it is sent away from when it is processed.

## Motivation

A data structure that receives events to be executed and allows other executors
to receive and process these events.

## Applicability

Consider using an event queue when you want to decouple events in *time*.

## Structure

A queue stores a series of notifications or requests in order based on 
priority&mdash;in a normal queue, a queue acts as a First In First Out data 
structure (although the queue could be a priority queue and bubble up events 
with higher priority). Receiving a notification or data results in an event 
being enqueued into the queue. The request processor then processes events at 
a later time. Requests can be handled directly, or routed to interested 
parties. This decouples the receiver and the data
processing both statically and in time.

A simple event queue can be implemented using an array.

## See Also

Observer Pattern
