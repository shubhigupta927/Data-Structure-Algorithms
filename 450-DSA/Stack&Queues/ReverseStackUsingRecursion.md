# Reverse Stack Using Recursion

```cpp
void insertAtBottom(stack<int>& stack, int x) {
    if (stack.empty()) {
        stack.push(x);
        return;
    }

    int temp=stack.top();
    stack.pop();

    insertAtBottom(stack, x);

    stack.push(temp);
}

void reverseStack(stack<int> &stack) {
    if (stack.empty()) {
        return;
    }

    int x=stack.top();
    stack.pop();

    reverseStack(stack);

    insertAtBottom(stack, x);
}
```