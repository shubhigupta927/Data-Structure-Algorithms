#  Level Order Traversal
```cpp
#include <bits/stdc++.h> 
/************************************************************

    Following is the BinaryTreeNode class structure

    template <typename T>
    class BinaryTreeNode {
       public:
        T val;
        BinaryTreeNode<T> *left;
        BinaryTreeNode<T> *right;

        BinaryTreeNode(T val) {
            this->val = val;
            left = NULL;
            right = NULL;
        }
    };

************************************************************/
vector<int> getLevelOrder(BinaryTreeNode<int> *root)
{
    queue<BinaryTreeNode<int>*> q;
    vector<int> result;

    if(root==NULL){
        return result;
    }

    q.push(root);
    while(!q.empty()){
        BinaryTreeNode<int> *temp= q.front();
        q.pop();
        result.push_back(temp->val);

        if(temp->left!=NULL){
            q.push(temp->left);
        }
        if(temp->right!=NULL){
            q.push(temp->right);
        }
    }
    return result;
}
```