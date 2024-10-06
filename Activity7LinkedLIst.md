```#include <iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
};

// Function to create a new node
Node* newNode(int data) {
    Node* temp = new Node;
    temp->data = data;
    temp->next = nullptr;
    return temp;
}

// Function to print the linked list
void printList(Node* head) {
    while (head != nullptr) {
        cout << head->data << " ";
        head = head->next;
    }
    cout << std::endl;
}

int main() {
    // Manually creating nodes
    Node* head = newNode(1);
    head->next = newNode(2);
    head->next->next = newNode(3);
    head->next->next->next = newNode(4);
    head->next->next->next->next = newNode(5);

    cout << "Linked list: ";
    printList(head);
    //delete the first
    Node* temp = head;
    head = head->next;
    delete temp;

    printList(head);
    Node* temp2 = head;
    while(temp2->next->next != nullptr){
        temp2 = temp2->next;
    }
    delete temp2->next;
    temp2->next = nullptr;

    printList(head);


    return 0;
}
```
the way the code works is by first creating a structure for Node pointers, and that way I can create and delete them with a data varaible whenever. THe main portion of the code works by creating a 5 unit linked list, and then to remove the first, I create a temporary node and point it at the same address as the head. I then assign the head to the second value in the linked list, head->next, and then deelete the temp node which takes the original head from memory with it. 


To remove the last value, i hav to iterate thru the list till its null. It checks 2 ahead so that we can assign the last one to temp2->next. Then, we delete temp2->next deleting the final address with it and then we reassign a nullptr to the temp2->next so we don't break the code. I think thats what happens when we create a memory leak? It just starts spamming numbers if i dont reassign it lol
