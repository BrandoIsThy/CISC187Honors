# H2 - DATA ANALYST - https://youtu.be/z3K7-go6cKM

### A. Explain how you are going to solve the problem mentioned above. No coding or pseudocode is needed in this step.
Since we're given the data in order, I'm gonna use two arrays that are already sorted in order of the months. 
First, I'm gonna find the total average sales of the year, and then find all the months that performed above average. 
Then, using the array of sales, I'll create a vector with those months by INDICES. The reason for a vector is so I can append, kind of like a list in python. 
Then, I can find the months that are in order, and if the indices are in order, we can then create another vector to store the months in order.
then, using those, we can go back to the name array, and call each month in order that is in order AND has sales greater than the average.

### B. Implement the solution that you proposed in part a. Furthermore, the implemented solution should be able to identify consecutive months when the sales are at the highest when a different dataset is used. C++ code is needed.

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
    // SECTION 1: Initializing variables
    int sum = 0;
    vector<int> top; // Vector to store the months that performed above average.
    string Months[14] = {"temp", "Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec", "temp"};
    int Sales[12] = {100, 113, 110, 85, 81, 101, 94, 106, 105, 102, 86, 63};

    // SECTION 2: Finding the Average Monthly Sale of the given year.
    for (int i = 0; i < 12; i++) {
        sum += Sales[i];
    }
    int avg = sum / 12;
    cout << "The Average Monthly Sale For The Given Year is $" << avg << "M. The months that performed above the average are: " << endl;

    // SECTION 3: Finding the months that outperformed the average and storing in the vector
    top.push_back(100); // Padding front end for later
    for (int j = 0; j < 12; j++) {
        if (Sales[j] > avg) {
            top.push_back(j + 1);
        } else {
            top.push_back(100); // Fill underperforming months with 100
        }
    }
    top.push_back(100); // Padding back end for later

    // SECTOIN 4: Storing vector values in an array
    int temp[top.size()];
    for (int k = 0; k < top.size(); k++) {
        temp[k] = top[k];
        if (temp[k] != 100) { // Avoid out-of-bounds access in Months[]
            cout << Months[k - 1] << " | "; // Print temp array values
        }
    }
    cout << endl;

    // SECTION 5: Calling the months that are in consecutive order and above average
    cout << "Consecutive months above average: ";
    for (int x = 1; x < top.size() - 1; x++) { // 1 to top.size() - 2 to avoid padding
        if (temp[x] != 100 && (temp[x - 1] != 100 || temp[x + 1] != 100)) {
            // Ensure that the current month and its neighbors are not 100
            cout << "|" << Months[temp[x]] << "|"; // Print the corresponding month name
        }
        else{
            cout << "---";
        }
    }

  // SECTION 6 When to advertise.
    cout << endl << "if results are empty, that is due to no consecutive months all being above average in sales."
         << endl;
    cout << "RESULTS: " << endl << "Boost Advertising In Months ";
    for (int x = 1; x < top.size() - 1; x++) { // 1 to top.size() - 2 to avoid padding
        if (temp[x] == 100 || (temp[x - 1] == 100 && temp[x + 1] == 100)) {
            // Ensure that the current month and its neighbors are not 100
            cout << "|" << Months[x] << "|"; // Print the corresponding month name
        } else {
            cout << "---";
        }
    }


    return 0;
}
```
### C. Write the pseudocode and explain the algorithm using O(N) notation. No coding is needed in this step.
```cpp
//My code is split into sections, so  i will pseudocode by sections

//section 1: Variable initizalization (0 steps)
  No actual function here so no need for O(n)
//section 2: Finding Average (2N + 1 --> O(n))
  Add total Sales of the year by iterating thru array of sales prices and adding (2N steps, 1 for iterating, 1 for adding)
  Divide total sales by 12 because 12 months a year (1 step)
//Section 3: Comparing Average to Each Months Sales
  Using a vector, compare each month via iteration to the average. (2N--> O(n))
  If greater than the average, push into the vector as the months int (Jan = 1, Feb = 2, etc), otherwise, Make it = 100 (N steps).
//Section 4: Turn vector back into array (2N + M --> O(n))
  Create a array Temp the same size as the vector ( 1 step)
  Iterate through the vector and array to move values from vector to array (2N Steps)
  Print Months that do not equal 100 (M steps, where M is # of steps greater than the avg)
//Section 5: Call out months in consecutive order and above average (3N + N + 1 = 4N + 1--> O(n))|
  Print "Consecutive Months that perform above average" (1 step)
  Iterate through indexes 1 - 12 of Temp. Index 0 and 13 are used as fillers. Then, check if the selected index isn't 100, or isn't surrounded (index - 1 and index + 1) for 100. (3N)
  If it clears the if statement above, print the corresponding month to the index in Temp, otherwise, print "---" (N steps)
//Section 6: Calling when to advertise (4N + 1 --> O(n))
Print "advertise these months:" (1 step)
 Iterate through indexes 1 - 12 of Temp. Index 0 and 13 are used as fillers. Then, check if the selected index is 100, or surrounded (index - 1 and index + 1) for 100. (3N)
  If it clears the if statement above, print the corresponding month to the index in Temp, otherwise, print "---" (N steps)


//So, total would be 0 + 2N + 1 + 2N + N + 2N + M + 1 + 4N + 1 + 4N + 1 = 15N + M + 4 = O(n) time.
```

### D. What are the limitations of the solution you proposed in part a?
There aren't many limitations, as it works successfully for whether months show up consecutively successful at both the beginning and end and everything in between. The biggest limitation is that it only works for 1 year. 
I could change it by using vectors in the initialization of my arrays and then converting said vectors into arrays. I'd have to change a few things around to accomodate for the dynamic alterations via the use of vectors though.


