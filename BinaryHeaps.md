# https://youtu.be/SUxVl0a5g9M
## For Questions 1 and 2:
![image](https://github.com/user-attachments/assets/26f0b51a-b10d-4f90-97ad-a908dd845f35)

## Question 3
Considering a max heap, the numbers, 55, 22, 34, 10, 2, 99, and 68, First we build our binary tree. 
![image](https://github.com/user-attachments/assets/39e27374-43e4-4bcf-b926-e33201f0ac6c)
Once rearranged via max heap, it'll look like:
![image](https://github.com/user-attachments/assets/f28d7b0f-0afe-4432-b1e6-d4f2d7854f7e)

So this is our complete tree. Now, we will assign the value of the root to the first index of an array. Then, we reassign the root as the bottom right node (55) in the heap and it'll trickle down and rearrange without the previous root, in this case, 99.
We do this over and over, where the array will iterate and assign the root and then reassign the root with the bottom right node and "trickle down",
leaving us with an array [99, 68, 55, 38, 22, 10 , 2]
