# DS_Module13
# EX.NO : 1(A) Display operator precedence in the infix expression.
## DATE: 
## AIM:
To write a C program to find and display the priority of the operator in the given Postfix expression

## Algorithm
1. Start the program. 
2. Define the priority() function to return the priority of operators. 
3. Initialize the string containing operators and operands. 
4. Loop through each character in the string. 
5. For each operator, call the priority() function to determine its priority. 
6. Print the operator and its corresponding priority level. 
7. End.
  

## Program:
```
Program to find and display the priority of the operator in the given Postfix expression
Developed by: LOKESH RAHUL V V
RegisterNumber: 212222100024
```
```c

int priority(char x)
{
  if(x == '&' || x == '|')
  {
      return 1;
  }
  else if(x == '+' || x == '-')
  {
      return 1;
  }
  else if(x == '*' || x == '/')
  {
      return 3;
  }
  else if(x == '^')
  {
      return 4;
  }
  return -1;
}
 
int main() 
{ 
    int i,j; 
    char ch[100]="(A*B)^C+(D%H)/F&G"; 
    for(i=0;i<strlen(ch);i++) 
    { 
        if(ch[i]=='+'|| ch[i]=='-'|| 
           ch[i]=='*'|| ch[i]=='/'|| 
           ch[i]=='%'|| ch[i]=='^'|| 
           ch[i]=='&'|| ch[i]=='|') 
        { 
            j=priority(ch[i]); 
            switch(j) 
            { 
                case 1: 
                    printf("%c ---- > ",ch[i]); 
                    printf("Lowest Priority\n"); 
                    break; 
                case 2: 
                    printf("%c ---- > ",ch[i]); 
                    printf("Second Lowest Priority\n"); 
                    break; 
                case 3: 
                    printf("%c ---- > ",ch[i]); 
                    printf("Second Highest Priority\n"); 
                    break; 
                case 4: 
                    printf("%c ---- > ",ch[i]); 
                    printf("Highest Priority\n"); 
                    break; 
            } 
        } 
    }  
    return 0; 
}

```
## Output:
![437342137-73624742-16f8-4405-bf6a-102a635d3fc7](https://github.com/user-attachments/assets/48fa7afe-b65c-43ae-97ab-f3c82a5231e6)



## Result:
Thus the C program to find and display the priority of the operator in the given Postfix expression is implemented successfully
# EX.NO : 1(B) Conversion of the infix expression into postfix expression
## DATE:
## AIM:
To write a C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule.

## Algorithm
1. Start the program. 
2. Initialize a stack and set the top index to -1. 
3. Define the push() and pop() functions to add and remove elements from the stack. 
4. Define the priority() function to assign priorities to operators. 
5. Traverse the expression in the IntoPost() function, handling operands, parentheses, and operators. 
6. After processing the expression, pop and print any remaining operators from the stack. 
7. End. 

## Program:
```
Program to convert the infix expression into postfix expression
Developed by: LOKESH RAHUL V V
RegisterNumber: 212222100024

```
```

#include<stdio.h>
#include<ctype.h>

char stack[100];
int top = -1;

void push(char x)
{
    top++;
    stack[top] = x;
}

char pop()
{
    if(top == -1)
    {
        printf("Stack Underflow");
    }
    else
    {
        return stack[top--];
    }
    return -1;
}
int priority(char x)
{
    if(x == '&' || x == '|')
  {
      return 1;
  }
  else if(x == '+' || x == '-')
  {
      return 1;
  }
  else if(x == '*' || x == '/' || x == '%')
  {
      return 3;
  }
  else if(x == '^')
  {
      return 4;
  }
  return -1;
}
void IntoPost(char *exp)
{
    char *e = exp;
    while(*e != '\0')
    {
        if(isalnum(*e))
        {
            printf("%c ", *e);
        }
        else if(*e == '(')
        {
            push(*e);
        }
        else if(*e == ')')
        {
            while(top != -1 && stack[top] != '(')
            {
                printf("%c ", pop());
            }
            pop();
        }
        else
        {
            while(top != -1 && priority(stack[top]) >= priority(*e))
            {
                printf("%c ", pop());
            }
            push(*e);
        }
        e++;
    }
    
    while(top != -1)
    {
       printf("%c ", pop());
    }
}


int main()
{
    char str[100] = "2*3%(2-1)+5|3" ;
    IntoPost(str);
    return 1;
}

```

## Output:
![437343854-0b145590-36d4-494b-b57d-ae01fbcae9c4](https://github.com/user-attachments/assets/2b35c228-2f75-4ee4-9961-707488f66263)



## Result:
Thus, the C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule is implemented successfully.
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
Program to implement Tower of Hanoi
Developed by: LOKESH RAHUL V V
RegisterNumber: 212222100024 
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
Program to evaluate the given prefix expression
Developed by: LOKESH RAHUL V V
RegisterNumber: 212222100024
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
# EX.NO : 1(E) Stack Operations
## DATE:
## AIM:
To write a C function to perform push and pop operation of the stack in the infix to postfix conversion.

## Algorithm
1. Initialize top as -1 and declare stack as a character array. 
2. To push, increment top and assign the character to stack[top]. 
3. To pop, check if top is -1 and return -1 if true. 
4. If not, return stack[top] and decrement top.
  

## Program:
```
Program to find and display the priority of the operator in the given Postfix expression
Developed by: LOKESH RAHUL V V
RegisterNumber: 212222100024
```
```c

#include<stdio.h>

char stack[100];
int top = -1;

void push(char x)
{
   top++;
   stack[top] = x;
}

char pop()
{
   if(top == -1)
   {
       printf("Stack Underflow");
   }
   else
   {
       return stack[top--];
   }
   return -1;
}

```
## Output:
![437311737-49cba1a6-9421-47cd-a84e-3118bf29135c](https://github.com/user-attachments/assets/1c9baf94-3960-4799-a1be-a64788f17e8a)



## Result:
Thus the C program to perform push and pop operation of the stack in the infix to postfix conversion is implemented successfully.
