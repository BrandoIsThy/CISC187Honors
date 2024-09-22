### https://youtu.be/bPgtn39TuEU

## A) Assume you have a simple single-dimensional array

```
#include <iostream>
#include <unordered_map> //Using this fo rthe .find function which is O(1) time.
using namespace std;

int main() {

    unordered_map<int, int> Map;

    //yes, this is in O(n) cause I want to convert my array into the map.
    int Arr[5] = {200, 400, 100, 50, 350};
    int search;
    for(int i = 0; i < 5; i++){
        Map[Arr[i]] = i;
    }
    //Yes, im aware this is in O(n) time but i want to confirm that my turning Array into map worked properly.
    cout << "Contents of the map (value, index):" << endl;
    for(auto x : Map){
        cout << x.first << " -> " << x.second << endl;
    }
    cout << "which value would you like to search?" << endl;
    cin >> search;


    //this is the actual search; by utilizing Map.find, the search takes O(1) time 
    if(Map.find(search) != Map.end()){
        cout << "The value " << search << " is located in index # " << Map[search] << endl;
    } else {
        cout << "The value " << search << " was not found in the map." << endl;
    }

    return 0;
}
```
## B) Use C++, generate hash value of your name
we weren't specified which hash function to use, so I just made a quick hash function that multiplies the ASCII character by 2 ^ i, where i is the index char of the string:
```#include <cmath>
#include <iostream>
using namespace std;

int main() {
    string Name = "Brandon";
    int hashCode = 0;
    for (int i = 0; i < Name.length(); i++) {
        hashCode += Name[i] * pow(2, i);
    }
        cout << hashCode << endl;

}
```
for my name, Brandon, it outputs 13754

## C) With the help of a figure, explain the problem that occured due to introducing a tombstone to mark the deleted cell. 5 pts
  lets use the figure below:
  ```
    1 2 3 4 5 6 7 8 9
```
This figure indicates a dictionary with 9 entries. When an entry is deleted, it doesnt become empty because that would cause the saerch to stop at the empty cell. Rather, a tombstone is placed as such:
```
1 2 3 4 5 6 7 8 9 --> 1 2 T 4 5 6 7 8 9
```
When doing this, the search can just acknowledge a entry was once there and move on. New data can be inserted into the location of tombstones in order of appearance as seen below:
```
1 2 t 4 5 t 7 8 9 -- inserting value 13 --> 1 2 13 4 5 t 6 7 8 9
```
After a series of deletions and insertions, there may be a number of tombstones left. As an example, lets say theres a bunch of tombstones as shown:
```
1 t t t t t t t 9
```
The process of searching for 9 would be drastically slower than a dictionary without the tombstones inbetween. This is the problem by introducing tombstones; The existence and memory of tombstones require more memory and computations to maintain. To fix this, we can re hash the dictionary, which would filter out the tombstones as such:
```
1 t t t t t t t 9 --> 1 9
```
Now, the new dictionary is much shorter, requires less memory, space complexity, and computational overhead to run through.

