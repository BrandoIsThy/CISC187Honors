## https://youtu.be/NOwU-DPg9KY
### 1) Following is the 'Word Builder' algorithm. Describe its space complexity in terms of Big O. 
  The word builder problem has a space coplexity of O(n), as it has a given array, and then creates another array called collection where data is later stored.
### 2) Following is a function that reverses an array. Describe its space complexity in terms of Big O:
  Same idea. Since the word builder function has the original array and a storage array called newArray where values are stored, the space complexity is O(n). 
### 3) Create a new function to reverse an array that takes up just O(1) extra space.
(Note: i think this is JS? ive never learned but i've planned to; seems simple enough heres my answer)  
The new function reverse is in O(1). First, a temp value is used to store the last value in the "reverse" symmetry of the array. for example, an array of ten, in pairs, the
reverse pairs would be (0, 9) (1, 8), (2, 7), (3, 6), (4, 5). We will call the first index of the two Element and the second the rElement, or reverse element.
in the case of any array, the reverse pair is (array[i], array[array.length - 1 - i]). 
First, the rElement of each pair is stored in a temp value. Then, the value of Element is placed in array[rElement]. Then, using the temp value, we go back to array[Element] 
and replace the value inside with the stored value. this switches the position. It Then continues to do that in its pairs, 1 from the beginning 1 from the end, 2 from beginning 
2 from the end, etc etc. The reason for the indexing of the for loop being array.length/2 is so it stops once it meets in the middle. If the length was the whole array, it would
first swap it, and after the middle, just swap it back to normal. 
```
function reverse(array) { 
		let temp = 0;
		for (let i = 0; i <array.length/2; i++) { 
				temp = array[array.length - 1 - i];
        array[array.length - 1 - i] = array[i];
        array[i] = temp;
		}
		return Array;
}
```
### 3) Fill in the table that follows to describe the efficiency of these three versions in terms of both time and space:

| Version    | Time complexity | Space complexity |
| ---------- | --------------- | ---------------- |
| Version #1 |      O(n)       |       O(n)       |
| Version #2 |      O(n)       |       O(1)       |
| Version #3 |      O(n)       |       O(n)       |  

reasoning:  
1) time complexity is O(n) since it just iterates thru the entire array and all n elements. space is O(n) since it uses another array, newArray. this means it delegated a space to initialize array, and a created a new space of size n equal to the initial array.
2) time complexity is O(n) since it just iterates thru the entire array and all n elements. space is O(1) since it does not create new memory, but rather just manipulates the one using the space that was already delegated for the initialization of the array.
3) time complexity is O(n) because the recursion will iterate thru the entire array until it hits the base case, where every index is processed. space is O(n) because recursion causes the creation of another action to the stack, thus increasing the total amount of needed memory, or O(n) times.
4) 
