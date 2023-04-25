# dscl_exp7
QUEUES IN C
A Queue is defined as a linear data structure that is open at both ends and the operations are performed in First In First Out (FIFO) order.
Queue can handle multiple data.
We can access both ends.
They are fast and flexible. 

Basic Operations of Queue
A queue is an object (an abstract data structure - ADT) that allows the following operations:
Enqueue: Add an element to the end of the queue
Dequeue: Remove an element from the front of the queue
IsEmpty: Check if the queue is empty
IsFull: Check if the queue is full
Peek: Get the value of the front of the queue without removing it

Applications of Queue
CPU scheduling, Disk Scheduling
When data is transferred asynchronously between two processes.The queue is used for synchronization. For example: IO Buffers, pipes, file IO, etc
Handling of interrupts in real-time systems.
Call Center phone systems use Queues to hold people calling them in order.

![image](https://user-images.githubusercontent.com/124857385/234319179-7dc5ae4a-a471-4386-9834-1cc022f8b61b.png)
![image](https://user-images.githubusercontent.com/124857385/234319362-2c0df244-fe7e-4a59-b84b-403686f1b903.png)


    // Queue implementation in C

    #include <stdio.h>
    #define SIZE 5

    void enQueue(int);
    void deQueue();
    void display();

    int items[SIZE], front = -1, rear = -1;

    int main() {
      //deQueue is not possible on empty queue
      deQueue();

      //enQueue 5 elements
      enQueue(1);
      enQueue(2);
      enQueue(3);
      enQueue(4);
      enQueue(5);

      // 6th element can't be added to because the queue is full
      enQueue(6);

      display();

      //deQueue removes element entered first i.e. 1
      deQueue();

      //Now we have just 4 elements
      display();

      return 0;
    }

    void enQueue(int value) {
      if (rear == SIZE - 1)
        printf("\nQueue is Full!!");
      else {
        if (front == -1)
          front = 0;
        rear++;
        items[rear] = value;
        printf("\nInserted -> %d", value);
      }
    }

    void deQueue() {
      if (front == -1)
        printf("\nQueue is Empty!!");
      else {
        printf("\nDeleted : %d", items[front]);
        front++;
        if (front > rear)
          front = rear = -1;
      }
    }

    // Function to print the queue
    void display() {
      if (rear == -1)
        printf("\nQueue is Empty!!!");
      else {
        int i;
        printf("\nQueue elements are:\n");
        for (i = front; i <= rear; i++)
          printf("%d  ", items[i]);
      }
      printf("\n");
    }
<img width="374" alt="Screenshot 2023-04-07 200841" src="https://user-images.githubusercontent.com/124857385/233785224-f0a7ead1-e2a3-4b79-a36b-86cf9c4743a4.png">
