### Array vs Linked List Performance
Array:
```
   int Arr[100000000];

    for(int i = 0; i < 100000000; i++){
        Arr[i]= i;
    }
}
```

Linked List:
```
#include <iostream>

struct Node {
    int data;
    Node* next;
};

int main() {
    Node* head = nullptr;

    for (int i = 0; i < 100000000; i++) {
        Node* newNode = new Node();
        newNode->data = i;
        newNode->next = nullptr;

        if (!head) {
            head = newNode;
        } else {
            Node* current = head;
            while (current->next) {
                current = current->next;
            }
            current->next = newNode;
        }
    }

    Node* current = head;
    for (int i = 0; i < 10 && current; i++) {
        std::cout << current->data << " ";
        current = current->next;
    }
    std::cout << std::endl;

    current = head;
    while (current) {
        Node* nextNode = current->next;
        delete current;
        current = nextNode;
    }

    return 0;
}

```

### For loop vs while loop interator performance

for while loop:
```
   int j = 0;
    while (j != 100000000){
        j++;
        cout << j << endl;
    }
```  

for for-loop:
```
 for (int i = 1; i <= 1000000; i++) {
        cout << i << endl;
```
