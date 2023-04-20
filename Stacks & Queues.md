# Stacks & Queues
## Stacks
#### Concept
**Stacks**: is a data struct which type of working is LIFO(Last In First Out). The last added elements will be the first removed.
#### Basic operation
<ul>
<li>empty() – Returns whether the stack is empty – Time Complexity : O(1)</li>
<li>size() – Returns the size of the stack – Time Complexity : O(1) </li>
<li>top() – Returns a reference to the top most element of the stack – Time Complexity : O(1) </li>
<li>pushStacks(data) – Adds the element ‘data’ at the top of the stack – Time Complexity : O(1) </li>
<li>popStacks() – Deletes the most recent entered element of the stack – Time Complexity : O(1) </li>
</ul>
<hr/>

## Queues
#### Concept
**Queues** is a data struct which type of working is FIFO(First In First Out). The first added elements will be the first removed.
#### Basic operation
<ul>
<li>pushQueues(data) – Adds the element ‘data’ at the top of the stack – Time Complexity : O(1) </li>
<li>popQueues() – Deletes the first element of the stack – Time Complexity : O(1) </li>
</ul>
<hr/>

### Code Stacks

```c++
struct Node{
 	int data;
	Node* next; 
 };
 ```

##### Push Stacks
```c++
node *top = NULL;
void PushStacks(int data)  
{  
    Node* temp;  
    temp = new Node;  
  
    //Trường hợp không cấp phát được bộ nhớ cho temp
    if (!temp) 
    {  
        cout << "\nHeap Overflow";  
        exit(1);  
    }  
  
    //Thêm temp vào đỉnh Stack, cập nhập lại biến top
    temp->data = data;  
    temp->link = top;   
    top = temp;  
} 
```
##### Pop Stacks
```c++
void PopStacks()  
{  
    Node* temp;  
  
    //Kiểm tra trường hợp Stack rỗng
    if (top == NULL)  
    {  
        cout << "\nStack Underflow" << endl;  
        exit(1);  
    }  
    else
    {  
        //xóa phần tử ở top, cập nhập lại top
        temp = top;  
        top = top->link;   
        temp->link = NULL;
        delete temp;  
    }  
}  
```
##### Top
```c++
int Top()  
{    
    if (!isEmpty())  
        return top->data;  
    else
        exit(1);  
}
```
##### Empty
```c++
int isEmpty()  
{  
    return top == NULL;  
}
```
##### Print
```c++
void PrintStack(){
    Node* temp = top;
    while (temp != NULL){
        cout << temp->data << " ";
        temp = temp->link;
    }
    cout << endl;
}
```

<hr/>

### Code Queues
##### Push Queue
```c++
Node* front = NULL, rear = NULL;
void pushQueue(int x) { 
    Node* temp;  
    temp = new Node;  

    if (!temp) {  
        cout << "\nHeap Overflow";  
        exit(1);  
    }  
    temp->data = x;
    temp->next = NULL;

    if (rear == NULL) { 
        front = rear = temp; 
        return; 
    } 

    rear->next = temp; 
    rear = temp; 
} 
```
##### Pop Queue
```c++
void popQueue() {  
    if (front == NULL) 
        return; 
         
    Node* temp = front; 
    front = front->next; 

    if (front == NULL) 
        rear = NULL; 
  
    delete temp; 
} 
```