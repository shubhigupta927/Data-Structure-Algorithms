# Clone List with Next and Random
```cpp
/* Structure of Linked List Node
class Node {
  public:
    int data;
    Node* next;
    Node* random;

    Node(int x) {
        data = x;
        next = random = nullptr;
    }
};*/

class Solution {
  public:
    Node* cloneLinkedList(Node* head) {
        // code here
        
        unordered_map<Node*, Node*>m;
         //simple structure
         if(head==NULL){
             return NULL;
         }
         Node *newHead = new Node(head->data);
         m[head] = newHead;
         Node *oldtemp=head->next, *newtemp=newHead;
         while(oldtemp!=NULL){
             Node *copyNode = new Node(oldtemp->data);
             m[oldtemp] = copyNode;
             newtemp->next=copyNode;
             newtemp->random=NULL;
             newtemp=newtemp->next;
             oldtemp=oldtemp->next;
         }
    
         //random pointer replication
         oldtemp=head;
         newtemp=newHead;
         while(oldtemp!=NULL){
             if(oldtemp->random!=NULL){
                 newtemp->random = m[oldtemp->random];
             }
             oldtemp=oldtemp->next;
             newtemp=newtemp->next;
         }
         return newHead;
    }
};
```