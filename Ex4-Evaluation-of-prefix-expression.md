# EX.NO : 1(D) Evaluation of prefix expression
## DATE: 
## AIM:
To write a C function to evaluate the given prefix expression using stack and print the output of the given prefix expression from the stack inside the function . 

## Algorithm
1. Start 
2. Initialize an empty stack s with a variable top for tracking the stack index. 
3. Define a push() function to add an element to the stack. 
4. Define a pop() function to remove and return the top element from the stack. 
5. In evalprefix(), loop through the given prefix expression from right to left. 
6. For each character, if it’s an operator (+, *), pop two operands from the stack, perform the operation, and push the result. 
7. If it's a digit, convert it to an integer and push it onto the stack; finally, print the result after the loop ends. 
8. End 


## Program:
```
/*
Program to evaluate the given prefix expression
Developed by: ASHWIN KUMAR S
RegisterNumber: 212222240013
*/
```
```c

#include<stdio.h>
#include<string.h>
#include<ctype.h>

int s[50];
int top=0;

void push(int ch)
{
	top++;
	s[top]=ch;
}

int pop()
{
	int ch;
	ch=s[top];
	top=top-1;
	return(ch);
}

void evalprefix(char p[50])
{
    int num1, num2, result;
    int len = strlen(p) - 1;
    while(len >= 0)
    {
        if(isdigit(p[len]))
        {
            push(p[len] - '0');
        }
        else
        {
            num1 = pop();
            num2 = pop();
            switch(p[len])
            {
                case '+':
                    result = num1 + num2;
                    break;
                case '-':
                    result = num1 - num2;
                    break;
                case '*':
                    result = num1 * num2;
                    break;
                case '/':
                    result = num1 / num2;
                    break;
                case '^':
                    result = num1 ^ num2;
                    break;
            }
            push(result);
        }
        len--;
    }
    printf("%d", pop());
}

int  main()
{
    char str[] = "+9*26";
    evalprefix(str);
    return 0;
}

```

## Output:
![437348076-17e818f5-e7d0-49ed-850d-35aed104df29](https://github.com/user-attachments/assets/50f5334a-09c4-458d-84b1-1d341fa921d9)



## Result:
Thus, the C program to evaluate the prefix expression using stack and print the output of the given prefix expression from the stack inside the function is implemented successfully.
