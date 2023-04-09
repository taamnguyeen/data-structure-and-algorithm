# LINKED LIST 
### Concept
**Linked list**: is a data structure that each element have only 1 element before and 1 element after.
### Types of Linked List:
-Singly linked list
-Doubly linked list
-Circularly linked list
### Basic operation
-Construct
-Insert
-Remove
-Search
-Retrieve
-Traverse
### Compare linked list and array
| Link list     | Array         |
| ------------- |-------------| 
| Include nodes. Each node include value and adress | Include elements the same data type | 
| Each node is stored everywhere in memory zone  | All element are stored in a big memory zone  |
| Easy to add or delete node | Hard to add or delete element  |
| Hard to access node | Easy to access element |

### Code
##### Initialization
```c++
struct node{
    int data;
    struct node *next;
};
```

##### New node
```c++
node* makeNode(int x){
    node *newNode = new node();
    newNode->data = x;
    newNode->next = NULL;
    return newNode;
}
```

##### Traverse node
```c++
void traverse(node *head){
    while(head != NULL){
        cout<< head->data << ' ';
        head = head->next;
    }
}
```

##### Count node
```c++
int size(node *head){
    int dem = 0;
    while(head != NULL){
        dem++;
        head = head->next;
    }
    return dem;
}
```

##### Add new node at head
```c++
void addAtHead(node **head, int x) {
   node *newNode = makeNode(x);
   newNode->next = *head;
   *head = newNode;
}
```

##### Add new node at tail
```c++
void addAtTail(node **head, int x) {
    node *newNode = makeNode(x);
    if(*head == NULL){
        *head = newNode;
        return;
    }
    node *temp = *head;
    while(temp->next != NULL){
        temp = temp->next;
    }
    temp->next = newNode;
}
```

##### Add node everywhere in linked list
```c++
void addAtIndex(node **head, int index, int x) {
    int n = size(*head);
    if(index == 0 || index > n){
        cout<<"vi tri chen ko hop le ";
        return;
    }
    if(index == 1){
        addAtHead(head, x);
        return;
    }
    node *temp = *head;
    for(int i = 1; i < index-1; i++){
        temp = temp->next;
    }
    node *newNode = makeNode(x);
    newNode->next = temp->next;
    temp->next = newNode;
}
```

##### Delete node at head
```c++
void deleteAtHead(node **head) {
    if(*head == NULL){
        return;
    }
    else{
        node *temp = *head;
        *head = temp->next;
        delete(temp);
    }
}
```

##### Delete node at tail
```c++
void deleteAtTail(node **head) {
    if(*head == NULL) return;
    node *temp = *head;
    if(temp->next == NULL){
        *head = NULL;
        delete temp;
        return;
    }
    while(temp->next->next != NULL){
        temp = temp->next;
    }
    node *tempp = temp->next;
    temp->next =NULL;
    delete(tempp);
}
```

##### Delete node everywhere in linked list
```c++
void deleteAtIndex(node **head, int index) {
    if(*head == NULL) return;
    int n = size(*head);
    if(index == 0 || index > n){
        cout<<"vi tri xoa ko hop le ";
        return;
    }
    if(index == n){
        deleteAtTail(head);
        return;
    }
    if(index == n-1){

    }
    else{
        node *temp = *head;
        for (int i = 0; i < index-2; ++i) {
            temp = temp->next;
        }
        node *tempp = temp->next;
        temp->next = tempp->next;
        delete(tempp);
    }
}
```

##### Search
```c++
bool search(node* head, int x)
{
    node* temp = head;
    while (temp != NULL) {
        if (temp->data == x)
            return true;
        temp = temp->next;
    }
    return false;
}
```