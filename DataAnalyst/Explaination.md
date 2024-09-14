# a. Explain how you are going to solve the problem mentioned above. No coding or pseudocode is needed in this step.
Since we're given the data in order, I'm gonna use two arrays that are already sorted in order of the months. 
First, I'm gonna find the total average sales of the year, and then find all the months that performed above average. 
Then, using the array of sales, I'll create a vector with those months by INDICES. The reason for a vector is so I can append, kind of like a list in python. 
Then, I can find the months that are in order, and if the indices are in order, we can then create another vector to store the months in order.
then, using those, we can go back to the name array, and call each month in order that is in order AND has sales greater than the average.
