#  Reverse Level Order Traversal
## for complete revrsal
```cpp
#include <stack>
#include <queue>
/************************************************************

    Following is the TreeNode class structure:

    template <typename T>

    class TreeNode {
    public:
        T val;
        TreeNode<T> *left;
        TreeNode<T> *right;
        TreeNode(T val) {
            this->val = val;
            left = NULL;
            right = NULL;
        }
    };

************************************************************/

vector<int> reverseLevelOrder(TreeNode<int> *root){
    vector<int> result;
    queue<TreeNode<int> *> q;
    stack<int> st;

    if(root==NULL){
        return result;
    }

    q.push(root);
    while(!q.empty()){
        TreeNode<int> *temp=q.front();
        q.pop();
        st.push(temp->val);

        if(temp->left!=NULL){
            q.push(temp->left);
        }
        if(temp->right!=NULL){
            q.push(temp->right);
        }
    }

    while(!st.empty()){
        result.push_back(st.top());
        st.pop();
    }

    return result;
}
```

## for level-wise reversal
```cpp

```