# Activity 8 Binary Search Trees

## 1) Imagine you were to take an empty binary search tree and insert the following sequence of numbers in this order: [1, 5, 9, 2, 4, 10, 6, 3, 8]. Draw a diagram showing what the binary search tree would look like. Remember, the numbers are being inserted in the order presented here. (2 points)

![image](https://github.com/user-attachments/assets/a3b635ff-2c9b-4f49-b076-ac682fdbac08)

---

## 2) If a well-balanced binary search tree contains 1,000 values, what is the maximum number of steps it would take to search for a value within it? (1 point)
By looking at the patterns of previous diagrams, it can be said that per level, the total # of values in N^2 - 1 values for all levels greater than 1 (1 will always just be 1 value). For example, a tree with 2 levels, it has 2^2 - 1 = 3 total values. If a tree has 3, it has 8 values, 4 has 15, 5 has 24, etc. So, if we say that 1000 = n^2 - 1, we get 999 = n ^2 . This results in n = 31.62277, but because we cant have a "partial level," it means rounding up to the closest integer is the right amount of levels, thus 32 total levels.
This can also be proven by showing that 31 levels is not enough nodes, meaning we'd need one more level to fit 1000 units: (31)^2 - 1 = 961 + 1 = 962, which is less than 1000. Since a 32nd level could store a total (32)^2 - 1 = 1024 values, it means a 32nd level must be implemented to hold the 1000 values

### final answer: 32 total levels. 

---

## 3) Write an algorithm that finds the greatest value within a binary search tree. 2 points)
Because a binary search tree by definition has it such that the right child of a parent node is always greater, we can keep going down the right until we get to the greatest value node:

```
void GreatestNode(Node* root){
    if(root->right == nullptr){
        cout << "greatest value is " << root->data;
        return;
    }
    GreatestNode(root->right);
}
```
this function is recursive. Referring to the code for question 4 on this assignment, if the node creates the left and right child node as nullptr values, then we can just check until the right child of a given node is nullptr, making that parent node the highest. The GreatestNode function keeps looping through until it bumps into the nullptr value on a right child node, and outputs the data of the right parent node. This will be implemented into the #4 also. 

---

## 4) Write a code in C++ using the same array mentioned in #1 and implement a binary search tree. Only insertion operation is required. (5 points)
```
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node *left;
    Node *right;
};

    Node* newNode(int data) {
        Node* temp = new Node;
        temp->data = data;
        temp->left = nullptr;
        temp->right = nullptr;
        return temp;
};

Node* insertNode(Node* root, int data){
    if(root == nullptr){
        return newNode(data);
    }
    if (data < root->data) {
        root->left = insertNode(root->left, data);
        } else {
        root->right = insertNode(root->right, data);
        }
    return root;
}


void GreatestNode(Node* root){
    if(root->right == nullptr){
        cout << "greatest value is " << root->data;
        return;
    }
    GreatestNode(root->right);
}

int main() {
    int Arr[9] = {1, 5, 9, 2, 4, 10, 6, 3, 8};
    Node* root = newNode(Arr[0]);

    for(int i = 1; i < 9; i++){
    root = insertNode(root, Arr[i]);
    }

    GreatestNode(root);
}


```
