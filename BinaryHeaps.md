![image](https://github.com/user-attachments/assets/fbbe1b7d-d154-44f2-90ef-8b5fa7e388b9)## For Questions 1 and 2:
![image](https://github.com/user-attachments/assets/5afb98d1-10f1-4871-87f2-219afced4cee)
## Question 3
Considering a max heap, the numbers, 55, 22, 34, 10, 2, 99, and 68, First we build our binary tree. 
![image](https://github.com/user-attachments/assets/39e27374-43e4-4bcf-b926-e33201f0ac6c)
Since it doesn't match the condtions needed for a heap, some numbers must be rearranged: 
First, when 99 is inserted, the max-heap will realize it is larger than its parent and the root, so itll move it up while replacing down as such: 
![image](https://github.com/user-attachments/assets/a99452dc-0da2-4e87-855e-28821ec47066)
Then, we insert 68 way below:
![image](https://github.com/user-attachments/assets/8f611177-e7dc-4af8-9250-ec5804afc8e9)
The heap max will recognize that 68 is bigger than 55 but lower than 99, so it'll bring it up one as such:
![image](https://github.com/user-attachments/assets/ef00ca82-14ec-4dfd-bc99-377048e7f305)
So this is our complete tree. Now, we will assign the memory address of the root to the first index of an array. Then, we reassign the root as the bottom right node (22) in the heap and it'll trickle down and rearrange without the previous root, in this case, 99.
We do this over and over, where the array will iterate and assign the root and then reassign the root with the bottom right node and "trickle down",
leaving us with an array [99, 68, 55, 38, 22, 10 , 2]
