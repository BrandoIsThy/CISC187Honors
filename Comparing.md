# H3 Linked List

preface: I could not understand how to get a profiler onto my system. So, I watched a few videos, and ran intoThe Cherno's video on C++ benchmarking (//www.youtube.com/watch?v=YG4jexlSAjc) by using the <chrono> library I created his timer for a function below:

```
#include <iostream>
#include <chrono>
#include <vector>

class Timer { //This is the timer funciton
public:
    Timer() {
        m_StartTimepoint = std::chrono::high_resolution_clock::now();
    }
    ~Timer() {
        Stop();
    }

    void Stop() {
        auto endTimepoint = std::chrono::high_resolution_clock::now();

        auto start = std::chrono::time_point_cast<std::chrono::microseconds >(m_StartTimepoint).time_since_epoch().count();
        auto stop = std::chrono::time_point_cast<std::chrono::microseconds >(endTimepoint).time_since_epoch().count();

        auto duration = stop - start;
        std::cout << duration * .001 << "ms spent." << std::endl;

    }


private:
    std::chrono::time_point<std::chrono::high_resolution_clock> m_StartTimepoint;
};
```
i couldn't find why my code wouldnt work with 100m regardless of int, double or floats, so I looked it up; apparently, vector utilizes the heap instead of the stack, and while i could increase my stack size, there could be other problems resulting from that. So I just continued with the float.

## Array vs Linked List Performance
### Array list Performance:
Here was the function for the array:
```
#include <iostream>
#include <chrono>
#include <vector>

class Timer { //This is the timer funciton
public:
    Timer() {
        m_StartTimepoint = std::chrono::high_resolution_clock::now();
    }
    ~Timer() {
        Stop();
    }

    void Stop() {
        auto endTimepoint = std::chrono::high_resolution_clock::now();

        auto start = std::chrono::time_point_cast<std::chrono::microseconds >(m_StartTimepoint).time_since_epoch().count();
        auto stop = std::chrono::time_point_cast<std::chrono::microseconds >(endTimepoint).time_since_epoch().count();

        auto duration = stop - start;
        std::cout << duration * .001 << "ms spent." << std::endl;

    }


private:
    std::chrono::time_point<std::chrono::high_resolution_clock> m_StartTimepoint;
};

int main() {
    const int size = 100000000;
    std::vector<int> Arr(size); // Using vector to allocate on the heap
    Timer timer;

    for (int i = 0; i < size; i++) {
        Arr[i] = i;
    }

    return 0;
}
```
the time it took was 127.367 ms.


### Linked List:
Here was the function for the linked list:
```
#include <iostream>
#include <chrono>

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

class Timer { // This is the timer function
public:
    Timer() {
        m_StartTimepoint = std::chrono::high_resolution_clock::now();
    }
    ~Timer() {
        Stop();
    }

    void Stop() {
        auto endTimepoint = std::chrono::high_resolution_clock::now();

        auto start = std::chrono::time_point_cast<std::chrono::microseconds>(m_StartTimepoint).time_since_epoch().count();
        auto stop = std::chrono::time_point_cast<std::chrono::microseconds>(endTimepoint).time_since_epoch().count();

        auto duration = stop - start;
        std::cout << duration * .001 << " ms spent." << std::endl;
    }

private:
    std::chrono::time_point<std::chrono::high_resolution_clock> m_StartTimepoint;
};

int main() {
    const int size = 100000000; // Number of nodes to create
    Node* head = nullptr; // Pointer to the head of the linked list
    Node* tail = nullptr; // Pointer to the tail of the linked list

    Timer timer;
    // initializing the first not in the loop;
    head = newNode(0);
    tail = head;
    //creating the other 9999999 nodes;
    for (int i = 1; i < size; i++) {
        Node* temp = newNode(i);
            tail->next = temp; // Link the new node to the end of the list
            tail = temp;
        }
    return 0;
}

```
This took a total of 311.993 ms; I thought it'd be faster, but I guess it depends; This one is what i believe is a doubly linked list since it uses a tail; Currently, I understand that this is O(n) time, but a singly linked would require O(n^2), as it would have to traverse form the beginning each time. 

CONCLUSION FOR A:

I thought that in conclusion, that the linked list would be faster; Maybe its because the question was super vague and didn't ask for anything specifically, and in the case of initialization, arrays are faster; I guess this also makes sense cause its basically just a search algortihm which takes both O(n) time, but the linked list module is  larger  than that of the array module for the part being measured;

## For loop vs while loop interator performance

### While loop performance:
```
  #include <iostream>
#include <chrono>

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

class Timer { // This is the timer function
public:
    Timer() {
        m_StartTimepoint = std::chrono::high_resolution_clock::now();
    }
    ~Timer() {
        Stop();
    }

    void Stop() {
        auto endTimepoint = std::chrono::high_resolution_clock::now();

        auto start = std::chrono::time_point_cast<std::chrono::microseconds>(m_StartTimepoint).time_since_epoch().count();
        auto stop = std::chrono::time_point_cast<std::chrono::microseconds>(endTimepoint).time_since_epoch().count();

        auto duration = stop - start;
        std::cout << duration * .001 << " ms spent." << std::endl;
    }

private:
    std::chrono::time_point<std::chrono::high_resolution_clock> m_StartTimepoint;
};

int main() {

    int j = 0;

    {
        Timer timer;
        while (j != 1000000) {
            j++;
            std::cout << j << std::endl;
        }
    }
}
```  
This took 67746.8 ms.

### for for-loop:
```
#include <iostream>
#include <chrono>

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

class Timer { // This is the timer function
public:
    Timer() {
        m_StartTimepoint = std::chrono::high_resolution_clock::now();
    }
    ~Timer() {
        Stop();
    }

    void Stop() {
        auto endTimepoint = std::chrono::high_resolution_clock::now();

        auto start = std::chrono::time_point_cast<std::chrono::microseconds>(m_StartTimepoint).time_since_epoch().count();
        auto stop = std::chrono::time_point_cast<std::chrono::microseconds>(endTimepoint).time_since_epoch().count();

        auto duration = stop - start;
        std::cout << duration * .001 << " ms spent." << std::endl;
    }

private:
    std::chrono::time_point<std::chrono::high_resolution_clock> m_StartTimepoint;
};

int main() {

    int j = 0;


    {
        Timer timer;
        for (int i = 1; i <= 1000000; i++) {
            std::cout << i << std::endl;
        }
    }
}
```
this took 64638.9 ms.

CONCLUSION FOR B:

I thought that this is how it'd go. Comparing the two, the main sections of code, the iteration, have different amount of lines, therefore different processes. With the while loop, a iteration had to happen every time the while statement as still true, thus an extra step; meanwhile, in a for loop, the iteration is in the same step as the identification. Im not sure if thats how that works, but it makes sense to me. For the while loop, it goes: Step 1, identify T/F. Step 2, iterate, step 3, print, and for the For loop it goes: Step 1, identiy T/F AND interate, step 2, print. 


