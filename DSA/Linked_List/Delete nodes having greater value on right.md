# Delete nodes having greater value on right
### In this logic we make the new head as soon as we get a value that is most maximum on the right and then we return the head. While returning the head only the nodes whoch are beyond head is accessible and printable all the previous nodes of head are irrelevent 

### There are 2 approach for this que -
```
1. We reverse the linked list and then get the maximum value if the value is less than maximum then delete the node and move on and in the end again reverse and retune the head.
 Node *compute(Node *head)
    {
      
        Node * temp = head;
        vector<int>vec;
        while(temp)
        {
            vec.push_back(temp->data);
            temp=  temp -> next;
        }
    int maxVal = vec.back();
    int i = vec.size() - 2;

    while (i >= 0) 
    {
        if (vec[i] < maxVal) 
        {
            vec.erase(vec.begin() + i);
        } else 
        {
            maxVal = vec[i];
            i--;
        }
    }
       
        Node *finalans = new Node(0);
        Node * curr = finalans;
        for(int i=0;i<vec.size();i++)
        {
            curr -> next = new Node(vec[i]);
            curr = curr -> next;
        }
        Node * result = finalans->next;
        delete finalans;
        return result;
    }
```
# 2nd Method-
```cpp
In the 2nd method we change the head to the most maximum value and then return head in such a way that only the nodes which are to the right of head are accessible and hence return head directly.
  Node *compute(Node *head)
    {
        // your code goes here
        Node *temp = head;
        while(temp->next != NULL)
        {
            if(temp->next->data>temp->data)
            {
                temp->data = temp->next->data;
                Node*curr = temp->next;
                temp->next = temp->next->next;
                delete(curr);
                temp = head; // This step is very imp
            }
            else
            {
                temp = temp->next;
            }
        }
        return head;
    }
```cpp
