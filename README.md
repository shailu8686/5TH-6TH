# 5TH-6TH
SUFIX

#include<stdio.h>
#define MAX 10
int stack[MAX],top=-1;
void push(int);
int pop();
void eval(int op1,char sym,int op2);
int main()
{
 int i=0,op1,op2;
 char exp[20];
 char sym;
 printf("Enter postfix expression:\t");
 scanf("%s",exp);
 for(i=0;exp[i]!='\0';i++)
 {
 sym=exp[i];
 if(isdigit(sym)) // Check given symbol is a digit or operator
 {
 push(sym-'0'); // Symbol converted to int
 }
 else{
 op2=pop(); // Pop the top ele as op2
 op1=pop(); // Pop the next top ele as op1
 eval(op1,sym,op2); // Call eval function to find res..
 }
 }
 printf("Result of given expression=%d",pop()); // Last ele in stack is res
 return 0;
}
void push(int ele)
{
 stack[++top]=ele;
}
int pop()
{
 return stack[top--];
}
void eval(int op1,char sym,int op2)
{
 int res;
 switch(sym)
 {
 case '+':res= op1+op2; // Calculate addition of Op1+Op2
 push(res); // Result Push it into stack
 break;
 case '-':res= op1-op2;
 push(res);
 break;
 case '*':res= op1*op2;
 push(res);
 break;
 case '/':res= op1/op2;
 push(res);
 break;
 case '%':res= op1%op2;
 push(res);
 break;
 }
} 

CIRCULAR QUEUE
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#define MAX 5
char cqueue[MAX], element;
int front = 0, rear = -1, count = 0; // count set to 0 Initially Q Empty.
void insert(char ele);
void delete();
void display();
int main()
{
 int ch;
 while(1)
 {
 printf("\n1.insert\n2.delete \n3.display \n4.exit\n Enter Your Choice:");
 scanf("%d", &ch);
 switch (ch)
DSA Lab Manual_________________________________________________________
 {
 case 1:printf("\n Enter a char element to insert:");
 scanf(" %c",&element); // Space is mandatory Before %c
 insert(element); // Call insert function
 break;
 case 2:
 delete ();
 break;
 case 3:
 display();
 break;
 case 4:
 return;
 }
 }
 return 0;
}
void insert(char ele)
{
 if (count == MAX) // if count is MAX then queue is full
 {
 printf("Circular Queue is full\n");
 return;
 }
 rear = (rear + 1) % MAX; //Find rear and insert element
 cqueue[rear] = ele; // Inserting element into queue
 count++; // Increment the count of elements
 printf("Element inserted into C-Queue. \n");
 // display();
}
void delete()
{
 if (count == 0)
 {
 printf("Circular Queue is empty\n");
 return;
 }
 printf("Element deleted from C-Queue: %c\n", cqueue[front]);
 front = (front + 1) % MAX; // Change front position after deletion
 count-=1; // Decrement count after deleting an element.
}
void display()
{
 int i;
 if (count == 0)
 {
 printf("\n Circular Queue is empty!\n");
 return;
 }
 else
 {
 // Display elements from front and till rear
 for (i=front;i!=rear;i=(i+1)%MAX)
 {
 printf("%c \n", cqueue[i]);
 }
 printf("%c",cqueue[i]); // print last element
 }
}
