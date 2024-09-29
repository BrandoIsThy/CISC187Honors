### QUESTION 1)
![image](https://github.com/user-attachments/assets/a6faefff-30f4-4abe-866c-35bcb3bdf22a)

### QUESTION 2)
![image](https://github.com/user-attachments/assets/e2e8405d-cef9-48c7-a899-40808872709c)

### QUESTION 3)

```
if Q.head = Q.tail
  underflow
if (Q.head = Q.tail + 1) or (Q.head = 1 and Q.tail = Q.length)
  overflow
Q[Q.tail] = x
if Q.tail == Q.length
    Q.tail = 1
else Q.tail = Q.tail + 1
```
and
```
if Q.head = Q.tail
  underflow
if (Q.head = Q.tail + 1) or (Q.head = 1 and Q.tail = Q.length)
  overflow
x = Q[Q.head]
if Q.head == Q.length
    Q.head = 1
else Q.head = Q.head + 1
return x
```

### QUESTION 4)

# Insert Front
Not as easy. My code works by first checking for overflow, but then it checks for the head position; If head is at 0 it moves the head to the back, and if not just a position infront of the head. it then updates the position of the new head.
```
 if Q.size == Q.length then
        return "Deque is full"
    
    if Q.head == 0 then
        Q.head = Q.length - 1
    else 
        Q.head = Q.head - 1

    Q[Q.head] = element
```

# Insert Back
Easy, can just treate like push():
```
S.top = S.top + 1
S[S.top] = x
```

# Remove Front
Easy, can just treat like dequeue():
```
x = Q[Q.head]
if Q.head == Q.length
    Q.head = 1
else Q.head = Q.head + 1
return x
```
# Remove Back
  Easy, can just treat like pop():
  ```
if STACK-EMPTY(S)
    error "underflow"
else S.top = S.top-1
    return S[S.top + 1]
```
