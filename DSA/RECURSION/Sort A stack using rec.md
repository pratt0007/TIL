# Stack sorting using recursion
```cpp
#include <iostream>
#include <stack>

void insertSorted(std::stack<int> &stk, int value) {
    if (stk.empty() || value > stk.top()) {
        stk.push(value);
        return;
    }

    int topValue = stk.top();
    stk.pop();
    insertSorted(stk, value);
    stk.push(topValue);
}

void sortStack(std::stack<int> &stk) {
    if (stk.empty()) {
        return;
    }

    int topValue = stk.top();
    stk.pop();
    sortStack(stk);
    insertSorted(stk, topValue);
}

int main() {
    std::stack<int> stk;
    stk.push(34);
    stk.push(3);
    stk.push(31);
    stk.push(98);
    stk.push(92);
    stk.push(23);

    std::cout << "Stack before sorting: ";
    while (!stk.empty()) {
        std::cout << stk.top() << " ";
        stk.pop();
    }

    stk.push(34);
    stk.push(3);
    stk.push(31);
    stk.push(98);
    stk.push(92);
    stk.push(23);

    sortStack(stk);

    std::cout << "\nStack after sorting: ";
    while (!stk.empty()) {
        std::cout << stk.top() << " ";
        stk.pop();
    }

    return 0;
}
```
