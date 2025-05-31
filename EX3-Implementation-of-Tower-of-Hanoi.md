# EX.NO : 1(C) Implementation of Tower of Hanoi
## DATE: 
## AIM:
To write a C program to implement Tower of Hanoi

## Algorithm
1. Start the program. 
2. Check if n is greater than 0. 
3. Recursively move n-1 disks from source (x) to auxiliary (z) using destination (y). 
4. Print the move of the n-th disk from source (x) to destination (y). 
5. Recursively move n-1 disks from auxiliary (z) to destination (y) using source (x). 
6. The function is called initially with TOH(n, 'A', 'B', 'C') where 'A', 'B', and 'C' are the rods. 
7. End   

## Program:
```
/*
Program to implement Tower of Hanoi
Developed by: LOKESH RAHUL V V
RegisterNumber: 212222100024 
*/

```
```c
#include<stdio.h>

void TOH(int n,char x,char y,char z)
{
   if(n == 1)
   {
      
      printf("%c to %c\n", x,y);
      return;
   }
   TOH(n-1,x,z,y);
   printf("%c to %c\n", x, y);
   TOH(n-1,z,y,x);
}

int main()
{
   int n = 2;
   TOH(n,'A','B','C');
}

```

## Output:
![437346534-8253c1e6-eee0-4509-bccb-7a8fe02ca4d3](https://github.com/user-attachments/assets/429fad0b-30bb-4a0f-b174-2021d0988cdc)



## Result:
Thus, the C program to implement Tower of Hanoi using recursion is implemented successfully.
