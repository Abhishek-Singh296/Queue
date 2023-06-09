# Queue
A queue in C is basically a linear data structure to store and manipulate the data elements. It follows the order of First In First Out (FIFO). In queues, the first element entered into the array is the first element to be removed from the array.It is an ordered list in which insertions are done at one end which is known as the rear and deletions are done from the other end known as the front. A good example of a queue is any queue of consumers for a resource where the consumer that came first is served first. 
The difference between stacks and queues is in removing. In a stack we remove the item the most recently added; in a queue, we remove the item the least recently added.



![Queue](https://user-images.githubusercontent.com/113619312/234083750-37286d7b-bc2d-41b0-8baa-85782428fb43.png)

---

__Basic Operations on Queue:__ 


__1.enqueue()__: Inserts an element at the end of the queue i.e. at the rear end.

Steps for enqueue:
- i. Check the queue is full or not
- ii. If full, print overflow and exit
- iii. If queue is not full, increment tail and add the element

__2.dequeue()__: This operation removes and returns an element that is at the front end of the queue.

Steps for dequeue:
- i. Check queue is empty or not
- ii. If empty, print underflow and exit
- iii. If not empty, print element at the head and increment head

---

__Types of Queues:__ 
- __Simple Queue__: Simple queue also known as a linear queue is the most basic version of a queue. Here, insertion of an element i.e. the Enqueue operation takes place at the rear end and removal of an element i.e. the Dequeue operation takes place at the front end.
- __Circular Queue__:  In a circular queue, the element of the queue act as a circular ring. The working of a circular queue is similar to the linear queue except for the fact that the last element is connected to the first element. Its advantage is that the memory is utilized in a better way. This is because if there is an empty space i.e. if no element is present at a certain position in the queue, then an element can be easily added at that position using modulo capacity(%n).
Priority Queue: This queue is a special type of queue. Its specialty is that it arranges the elements in a queue based on some priority. The priority can be something where the element with the highest value has the priority so it creates a queue with decreasing order of values. 

---

## __Code__
```
// program to implement a queue using arrays

#include <stdio.h>

#define MAX 10

int queue[MAX];
int front = -1;
int rear = -1;

void enqueue();
void dequeue();
void display();

int main()
{
	int choice;
	char c;
	
	printf("Queue Operations: \n");
	printf("1. enqueue\n2. dequeue\n3. display\n");
	
	do
	{	
		printf("\nEnter 1, 2 or 3 to perform a queue operation from the list above, or 4 to exit: ");
		scanf("%d", &choice);
	
		switch(choice)
		{
			case 1:
				{
					printf("\nEntered choice: %d\n", choice);
					enqueue();
					break;
				}
			case 2:
				{
					printf("\nEntered choice: %d\n", choice);
					dequeue();
					break;
				}
			case 3:
				{
					printf("\nEntered choice: %d\n", choice);
					display();
					break;				
				}
			case 4:
				{
					printf("\nTerminating...");
					break;
				}
			default:
				{
					printf("\nInvalid choice. Terminating...");
					break;
				}		
		}
		
	}while(choice == 1 || choice == 2 || choice == 3);
	
	return 0;
}

void enqueue()
{
	int n;
	
	printf("Enter a value to be entered in the queue: ");
	scanf("%d", &n);
	
	if(rear == (MAX - 1))
	{
		printf("queue full, cannot enter element.\n\n\n");
	}
	else
	{
		front == -1 ? front++ : 0;
		rear++;
		queue[rear] = n;
		printf("Value entered.\n\n\n");
	}
	
	return;	
}

void dequeue()
{
	int i;
	
	if(front < 0)
	{
		printf("queue empty, cannot delete element.\n\n\n");
	}
	else if(front >= 0 && front != rear)
	{
		// entering 0 to denote a deleted element (temporary - fix this)
		queue[front] = 0;
		front++;
		printf("Value deleted.\n\n");
	}
	else if(front == rear)
	{
		front = -1;
		rear = -1;
		printf("Value deleted.\nQueue empty. Reset front and rear indices to -1.\n\n\n");
	}
	
	return;
}

void display()
{
	int i;
	
	printf("Available queue: \n");
	
	for(i = front; i <= rear; i++)
	{
		printf("%d\t", queue[i]);
	}
	
	printf("\n\n\n");
	
	return;
}
```

---

## __Output__
![Screenshot 2023-04-11 161323](https://user-images.githubusercontent.com/113619312/234086285-ab424a02-95ca-4b1b-8cc5-6c23cc0e230f.png)
