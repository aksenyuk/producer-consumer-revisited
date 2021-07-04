#                                                                            OS&CP Project A.2
#                                                          PUT Poznań, AI, Semester 2, Sofya Aksenyuk, 150284.

The supplied "OS-CP-Project-A.2" file presents the solution to the multi-process synchronization problem called Producer-Consumer problem. 

The essence of the problem is as follows: The producer and the consumer share the same initially fixed-size buffer. The producer is on charge of generating data that will be added to the buffer, whereas the consumer removed that data from the buffer one by one. To get an access for "entering" this buffer both - producer and consumer - has to wait for the specific sign (i.e., the state of buffer which controls by the function "sem_wait") to prevent producer adding data to already full buffer or consumer trying to remove data from the empty buffer.

As the solution, the semaphore approach was used: two semaphores (namely, "sem_empty" and "sem_full") control the state of buffer, then waiting and awakening threads ("pthread_mutex_lock" and "pthread_mutex_unlock", subsequently) "tell" the producer or the consumer if it is the time to proceed further actions (is the mutex locked or unlocked).
In "main" function "pthread_create" and "pthread_join" functions were used to starts a new thread in the calling process and then make the calling thread wait till the newly created thread returns.

Here is an example of the programm execution where the produced and consumed items can be checked:

![execution example](https://user-images.githubusercontent.com/86928699/124398318-66949f80-dd15-11eb-990e-cf0ad7a5d28f.jpg)
