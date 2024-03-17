# 5th
#include <stdio.h>
void push(int [], int*, int);
int pop(int [], int*);
int main()
{
int iastack[50], i, op1, op2, res;
char expr[50], symb;
int top = -1;
printf("\nEnter a valid postfix expression : \n");
scanf("%s", expr);
for(i=0; i<strlen(expr); i++)
{ symb = expr[i];
if(isdigit(symb))
{
push(iastack, &top, symb-'0');
}
else
{
op2 = pop(iastack, &top);
op1 = pop(iastack, &top);
switch(symb)
{ case '+' : res = op1 + op2;
break;
case '-' : res = op1 - op2;
break;
case '*' : res = op1 * op2;
break;
case '/' : res = op1 / op2;
break;
case '%' : res = op1 % op2;
break;
case '^' : res = (int)pow(op1 , op2);
break;
}
push(iastack, &top, res);
}
}
res = pop(iastack, &top);
printf("\nValue of %s expression is : %d\n", expr, res);
return 0;
}
void push(int Stack[], int *t , int elem)
{
*t = *t + 1;
Stack[*t] = elem;
}
int pop(int Stack[], int *t)
{
int elem;
elem = Stack[*t];
*t = *t -1;
return elem;
}

OUTPUT:
Enter a valid postfix expression :
456565+-/*()
Value of 456565+-/*() expression is : -5

#include <stdio.h>
void towers(int, char, char, char);
int main()
{
int num;
printf("Enter the number of disks : ");
scanf("%d", &num);
printf("The sequence of moves involved in the Tower of Hanoi are :\n");
towers(num, 'A', 'C', 'B');
printf("\n");
return 0;
}
void towers(int num, char frompeg, char topeg, char auxpeg)
{
if (num == 1)
{
printf("\n Move disk 1 from peg %c to peg %c", frompeg, topeg);
return;
}
towers(num - 1, frompeg, auxpeg, topeg);
printf("\n Move disk %d from peg %c to peg %c", num, frompeg, topeg);
towers(num - 1, auxpeg, topeg, frompeg);
}




