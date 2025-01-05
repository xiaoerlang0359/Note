# Transactions

## Transaction Structures

### read transactions

1.  Allocating read
![read allocate transaction](image.png)

2. non-allocating read
![alt text](image-1.png)

### Write Transaction

1. Immediate Write

    a) DWT
    ![alt text](image-2.png)
    b) No DWT, no CompAck
    ![alt text](image-3.png)
    c) No DWT, with CompAck
    ![alt text](image-4.png)

2. Write Zero

![alt text](image-5.png)

3. Copy Back Write

![alt text](image-6.png)

### Atomic transactions

![alt text](image-7.png)

### Stash Transaction

1. Write with Stash Hint
![alt text](image-8.png)
2. Independent Stash without StashDone response
![alt text](image-9.png)
3. Independent Stash with StashDone response
![alt text](image-10.png)

### Dataless Transaction
![alt text](image-11.png)

### DVM Transaction
![alt text](image-12.png)

### Retry
![alt text](image-13.png)

### Home Initiated transactions

1. Read

![alt text](image-14.png)

2. Write

![alt text](image-15.png)

3. Dataless

![alt text](image-16.png)

4. Atomic

![alt text](image-17.png)

5. Snoopee

![alt text](image-18.png)

6. DVM

![alt text](image-19.png)