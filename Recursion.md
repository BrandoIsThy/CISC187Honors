# https://youtu.be/KgbHzo5vjA8
### Base Case
The base case is low = 12, and high = 10. This is because high does not change, however low = low + 2 every time low is not greater than high. At first, i thought it might be low = 10 and high = 10, but 10 is infact not greater than 10, so i think it'll have to be 12 and 10 to satisfy that low > high. 

### factorial case
since we start with 10 and recursively repeats by n-2, the factorial of 10 would be -infinity and wrong. This is because the base case is that n = 1, but if the function repeats via n - 2 and starts at 10, n will never become 1. instead, it will repeat starting at n = 10 as such:  
n = 10 -> n = 8 -> n = 6 -> n = 4 -> n = 2 -> n = 0 -> ... n = - infinity; therefore, n never becomes 1, therefore the function never will reach the base case. 

### fixing code
added the return if low > high function, so when low becomes larger than high, it stops adding. 
```
def sum(low, high)
    return if low > high
else 
    return high + sum(low, high - 1)
    
end
```

### Write a recursive function that prints all the numbers

i had to pull out the good ol pycharm for this one. I tried doing it in cpp, realized i haave no clue how i'd actually achieve it htere, and then moved on. I did some research later on it in cpp and it seemed super complicated lol. I did it in python because lists are super easy to manipulate, read, write etc. The recursive portion is in the elif statmement isinstance(item, list), which can tell whether the current index is a integer or another array. If its another array, it iterates through the array in the array, then moves on after that.

```
def printVal(arr):
    for item in arr: #iterates thru whole array
        if isinstance(item, int):  # if its a integer
            print(item)
        elif isinstance(item, list):  # If it's a list, it uses recursion to go thru the list within the list
            printVal(item)

# Define the nested array
array = [
    1, 
    2, 
    3, 
    [4, 5, 6], 
    7, 
    [8, 
        [9, 10, 11, 
            [12, 13, 14]
        ]
    ],
    [15, 16, 17, 18, 19,
        [20, 21, 22, 
            [23, 24, 25,
                [26, 27, 29]
            ], 30, 31 
        ], 32
    ], 33
]

printVal(array)
```
