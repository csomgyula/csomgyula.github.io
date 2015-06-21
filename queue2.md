wait-free queue protocol for 2 threads
==

2015.06.21.

Overview
--

The protocol is based on a **gentle coordination** scheme. In case the thread detects that the other thread is active, it gently offers the position for it.
 
Details:

1. **Actual pos** - Read the actual queue position
2. **Is other active?** - Check whether the other thread is active
3. **Determine the next positions** - depending on whether the other thread is active or not:
   1. If the other queue is not active, then the next position will be the actual + 1 and do not offer anything
   1. If the other queue is active, then 
      1. if there was a previous offer then the next position will be the actual + 1 and reoffer the previous offer, 
      2. if there was no previous offer, then the next positionn will be the actual pos + 2 and offer the actual pos + 1.
4. **Try to set the next positions** - set the above numbers using CAS
5. **Use my number if we won, use the offer otherwise** - If the set was successful then we are DONE. If the set was unseccessful then accept the offer made by the other thread. If there was no offer then use the actual pos + 1 


Premisse: The protocol builds on the `compare-and-set` (`CAS`) primitive and `volatile` fields (that is always read from main memory). These should be supported by the underlying platform (for instance Java does support them).


States
--

The protocol has the following states:

* `active_0, active_1 : boolean` - two flags that show whether thread 0, thread 1 is active or not. A thread is *active* if it is just enqueueing.
* `actual : struct(last : int, last_offered: int)` - a struct that shows the actual positions
  * `pos` - the actual queue position, ie. the position in the queue where the last item was pushed
  * `offer_0, offer_1` - the last position the thread offered for the other thread


Protocol
--

### 1 actual numbers

    volatile v_actual := actual
    v_pos := actual.pos
    v_offer := actual.offer_my_index
    
, where `my_index` is the index of the thread (0 or 1)

Premisse: data is read from main memory, not from CPU cache

### 2 is other thread active?

    volatile v_other_active := active_its_index

, where 

    its_index = my_index + 1 % 2

Premisse: data is read from main memory, not from CPU cache

### 3 determine next positions

#### 3.1 other is not active

    if not v_other_active then
        v_next := v_actual + 1
        v_next_offer := undefined


#### 3.2 other is active

    if v_other_active then

##### 3.2.1 there was no previous offer

    if v_offer is undefined then:
        next_pos := pos + 2
        next_offer := pos + 1

##### 3.2.2 there was a previous offer

    if v_offer is defined then:
        next_pos := pos + 1
        next_offer := offer

##### store it
    
    v_next.pos := next_pos
    v_next.offer_my_index := offer
    v_next.offer_her_index := undefined
 
### 4 try to set next positions

    set_succeeded := actual.compare_and_set(v_actual, v_next)    

Premisse: either thread wins, that is it does not happen that both fails.

### 5 use my number if won and accept her offer otherwise

#### 5.1 use my number if won

    if set_succeeded then
        return next_pos

#### 5.1 use her offer if lost

    if not set_succeeded then
        v_actual := actual
        pos := actual.pos
        offer := actual.offer_its_index
        return offer defined ? offer : pos + 1 

Premisse: data is read from main memory, not from CPU cache


Features
--

To my beleif the above protocol provides the above features/guarantees:

1. it is consistent with the queueing protocols - the same position is never overwritten, the protocol does not introduce holes in the queue
1. it is wait-free/fair - queueing is guaranteed to finish in finite steps even in race condition, typically the thread can enqueue its item to the next position or to the next position + 1


TODO
--

* Queues are typically not infinite, instead they use circular positons - this might cause problem.
* In case of a slow thread a gentle offer could mean that the queue as a whole (and its consumers) should wait for the slow thread. This could be solved if the other thread repeat the enqueueing procedure of the other thread. It is slower but more reliable.
