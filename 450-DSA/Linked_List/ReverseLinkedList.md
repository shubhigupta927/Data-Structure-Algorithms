# Reverse Linked List
## Recursion solution
```cpp
LinkedListNode<int> *reverseLinkedList(LinkedListNode<int> *head) 
{
    if(head == NULL || head->next == NULL){
        return head;
    }

    LinkedListNode<int> *newHead = reverseLinkedList(head->next);

    head->next->next = head;
    head->next = NULL;

    return newHead;

}
```

## Iterative solution 
```cpp
LinkedListNode<int> *reverseLinkedList(LinkedListNode<int> *head) 
{
    LinkedListNode<int> *prev, *current, *q;
    prev =NULL;
    q = NULL;
    current=head;

    while(current!=NULL){
        q=current->next;
        current->next=prev;

        prev=current;
        current=q;
    }

    head=prev;

    return head;
}
```