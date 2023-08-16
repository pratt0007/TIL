# Reverse a stack using recursion!!

```
#include <iostream>
#include <stack>

void insertAtBottom(std::stack<int> &stk, int value) {
    if (stk.empty()) {
        stk.push(value);
        return;
    }

    int topValue = stk.top();
    stk.pop();
    insertAtBottom(stk, value);
    stk.push(topValue);
}

void reverseStack(std::stack<int> &stk) {
    if (stk.empty()) {
        return;
    }

    int topValue = stk.top();
    stk.pop();
    reverseStack(stk);
    insertAtBottom(stk, topValue);
}

int main() {
    std::stack<int> stk;
    stk.push(1);
    stk.push(2);
    stk.push(3);
    stk.push(4);
    stk.push(5);

    std::cout << "Stack before reversal: ";
    while (!stk.empty()) {
        std::cout << stk.top() << " ";
        stk.pop();
    }

    stk.push(1);
    stk.push(2);
    stk.push(3);
    stk.push(4);
    stk.push(5);

    reverseStack(stk);

    std::cout << "\nStack after reversal: ";
    while (!stk.empty()) {
        std::cout << stk.top() << " ";
        stk.pop();
    }

    return 0;
}
```
