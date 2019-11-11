> What is deadlock, explain wait and die scheme used for deadlock prevention. [5M]
***
#### Deadlock explained [1M]
Deadlock occurs when each transaction T in a set of two or more transactions is waiting for some item that is locked by some other transaction T′ in the set. 
Hence, each transaction in the set is in a waiting queue, waiting for one of the other transactions in the set to release the lock on an item.
But because the other transaction is also waiting, it will never release the lock.
#### Wait and die scheme [3M]
Its a deadloack prevention scheme where each transaction is given a unique timestamp (TS).
Suppose that transaction Ti tries to lock an item X but is not able to lock it because X is locked by some other transaction Tj with a conflicting lock. 
The rule followed by this scheme is:  
```
If TS(Ti) < TS(Tj), then ... Ti older than Tj
   Ti is allowed to wait;
otherwise ... Ti younger than Tj
  abort Ti (Ti dies) and restart it later with the same timestamp.
```
#### Example [1M]
For example if there are three transactions T5, T10, and T15 (number represents their timestamps).  
If T5 requests a data item held by T10, then T5 will wait since 5 < 10.  
If T15 requests a data item held by T10, then T15 will be aborted since 15 > 10.
