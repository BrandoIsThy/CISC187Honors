### 1) Explain Proof that, under the average-case scenario, the insertion sort has a time complexity of O(n^2). Draw a clear figure and show all operations clearly.
The image below shows that for the average unsorted array, which is 1/2 needing sorting and 1/2 not, it requires N^2/4 steps, if 1 step was compare and no switch or compare and switch. 
![image](https://github.com/user-attachments/assets/a1967e3b-af40-431a-9ce8-93f6504247fe)
Another really simple proof, that makes sense to me atleast, is that we know that The best case scenario takes N - 1 steps as it just has to compare each step and the worst case scenario takes N(N-1)/2 steps, if one step was compare and no switch or compare and switch.
This can be seen by the example given in the reference material:
![image](https://github.com/user-attachments/assets/a62ff995-ccd5-447b-8ef6-5ff203da5f8e)
The average formula is (A<sub>1</sub> + A<sub>2</sub> + ...A<sub>n</sub>)/n. Since we have the GREATEST # of steps and LOWEST # of steps (Worst and Best case scenarios), we can take their # of step formulas and find the average:
(N(N-1)/2 + (N-1))/2 --> (((N^2 - N) + 2N - 2)/2)/2 --> (N^2 + N - 2)/2/2 --> (N^2 + N - 2)/4, and we take the highest order, so N^2/4, and no constants for time compelxity, so O(N^2).

### 2) At the start of the insertion sort, the index of the inspected value is set to 1. Change the index of the inspected value and verify that the total number of operations equals 20. Consider the worst-case scenario. Use N=5, where N is the number of elements.
From my understanding of this question, you are asking for me to look at a array [5, 4, 3, 2, 1], and starting at the first index, show that this will take 20 steps of comparing or sorting.  
Since the first iteration is (1) compare 5 and 4 and (2) switch 5 and 4, it 1 took 2 steps.  
The nexct iteration is (3) comparing 5 and 3, (4) switching 5 and 3, (5) comparing 4 and 3, and (6) swicthing 4 and 3.  
Basically, per # of spaces, it requires 2 actions per space. So between index 0 and 1, 2 step. Index 1 and 2 is the 2nd space, so 4 steps. Index 2 and 3 is the 3rd space, so 6 steps. Index 3 and 4 is the 4th, so 8 steps. Therefore, 20 steps. 
![image](https://github.com/user-attachments/assets/27cffb16-dda5-4cde-aec2-12f3be847cef)

### 3) The following function returns whether or not a capital “X” is present within a string (refer to https://github.com/d-khan/dslabs/blob/main/intro/sorting-2.md)

### a) What is this functions time complexity regarding Big O notation?
regarding big O notation, since we use a string, which is basically a array of characters, this function is in O(n) or linear time. Since all we're doing is iterating through the list and comparing every character, the # of steps is 2N + 1, where N is the # of chars in the string. 
For example, in the word "excel", it'd take 11 steps, every character has a step of iterating and a step of comparing, and then the aditional step of turning foundX true for the given character. 

### b) Then, modify the code to improve the algorithm’s efficiency for best- and average-case scenarios.
  I believe this function is already in O(N), so time complexity can't become O(1) constant time, but we could optimize the number of steps as mentioned above. In the code before editing, it continues iterating through the string even after finding X. We can optimize the code by one, making it return true when X is found, which would also end the loop and the function, and then an else step where it returns false. That way, we reduce the # of variables, lines of code, and stop when X is found.
```
function containsX(string) {
	
	for(let i = 0; i < string.length; i++) { 
		if (string[i] === "X") {
			return true;
		}
	}
	return false.
}
```
