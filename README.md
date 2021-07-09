# OS&CP Project
## A.2 The producer-consumer problem revisited
#### PUT Poznań, AI, Semester 2, Sofya Aksenyuk, 150284.

* The supplied `OSCP_A2.c` file presents the solution to the multi-process synchronization problem called the **_Producer-consumer problem_**.

* The **essence** of the problem is as follows: the producer and the consumer share the same initially fixed-size buffer. The producer is on charge of generating data that will be added to the buffer, whereas the consumer removes that data from the buffer one by one. To get an access for _"entering"_ this buffer, both - producer and consumer - has to wait for the specific sign (i.e., the state of buffer which controls by the function `sem_wait`) to prevent producer adding data to already full buffer or consumer trying to remove data from the empty buffer.

* As the **solution**, the semaphore approach was used: two semaphores (namely, `sem_empty` and `sem_full`) control the state of buffer, then waiting and awakening threads (`pthread_mutex_lock` and `pthread_mutex_unlock`, subsequently) _"tell"_ the producer or the consumer if it is the time to proceed further actions (is the mutex locked or unlocked).
In `main` function `pthread_create` and `pthread_join` functions are used to start a new thread in the calling process and then make the calling thread wait till the newly created thread returns.

* The following pseudocode was used as a base:

![pseudocode](https://user-images.githubusercontent.com/86928699/124405402-d23f3280-dd3e-11eb-9092-c44e1ca61fdf.jpg)

* To **run** the program you have to execute the file named `Makefile.txt` in a following way: 
```
make -f Makefile.txt
./A2 no.of Producers no.of Consumers
```

* Here is an **example** of the programm execution where the produced and consumed items can be checked:

![example](https://user-images.githubusercontent.com/86928699/124457132-c62d9200-dd8b-11eb-951a-78a92f2c104d.jpg)
