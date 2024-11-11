# "Why Dijkstra's algorithm fails on negative weights". https://youtu.be/KmSesnEIMuw

Dijkstra's algorithm runs on the assumption that all weights are positive. That means once dijsktra compares the path from A-B and A-C, it assumes that A-B-D > A-B and A-C-D > A-C  because it assumes the adding of positive weights. However, when negative weights are used, they can go be shortened since adding a negative is equivalent to subtracting. 

![image](https://github.com/user-attachments/assets/f4bbe8fe-8ad6-4f5f-a00d-80b003b2d79a)

in the example, Dijkstra's will first start at A. When it compares the weight of B and C, it recognizes that B = 1 is less than C = 4, so the priority queue goes (B(1), C(4)).  Dijkstra's will recognize the weight from B->D is 2, so the total length from A-B-D is 1 + 2 = 3.   
At this point, Dijkstra's assumes that the path A-B-D = 3 is the shortest because the path A-B-D = 3 is less than the path of 
A-C = 4 alone. So, it locks in the shortest path from A-B-D is 3. However, the actual case is that with the negative weight, the path of A-C-D would provide a lenght of 4 - 5 = -1. But because the assumption that the paths can only increase due to positive weights, it does not work. 
