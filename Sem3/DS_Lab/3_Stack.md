#include <stdio.h>
#include <stdlib.h>

int stack[6],rev[6];
int top=-1,k=0;
int size;

void push();
void pop();
void display();
int pali();

void main()
{
 int choice,f;
 printf("Enter the size for stack\n");
 scanf("%d",&size);
 printf("1.Push\n2.Pop\n3.Display\n4.Check for Palindrome\n5.Exit\n");
 printf("Enter the choice\n");
 scanf("%d",&choice);
 while(choice!=5)
  {
   switch(choice)
    {
     case 1:push();
            break;
     case 2:pop();
            break;
     case 3:display();
            break;
     case 4:f=pali();
            if(f==1)
              printf("It's Palindrome\n");
            else
              printf("It's not a Palindrome\n");
            break;
     default:printf("Wrong choice...\n");
    }
   }
}

void push()
 {
  int num;
  if(top==(size-1))
   {
    printf("Stack Overflow\n");
   }
  else
   {
    printf("Enter the number to be pushed\n");
    scanf("%d",&num);
    top++;
    stack[top]=num;
   }
 }

void pop()
 {
  int num;
  if(top==-1)
   {
    printf("Stack Underflow\n");
   }
  else
   {
    num=stack[top];
    printf("Popped element is %d\n",num);
    top--;
   }
 }

void display()
 {
  int i;
  if(top==-1)
   {
    printf("Stack Underflow\n");
   }
  else
   {
    printf("Stack Contents....\n");
    for(i=top;i>=0;i--)
     {
      printf("%d\n",stack[i]);
      rev[k++]=stack[i];
     }
   }
 }

int pali()
 {
  int i,flag=1;
  for(i=top;i>=0;i--)
   {
    if(stack[i]!=rev[--k])
     {
      flag=0;
     }
   }
  return flag;
}

# Output
--------STACK OPERATIONS-----------
1.Push
2.Pop
3.Check for Palindrome
4.Display
5.Exit

Enter your choice: 1
Enter the element to be inserted: 1
Enter your choice: 1
Enter the element to be inserted: 2
Enter your choice: 1
Enter the element to be inserted: 1
Enter your choice: 1
Enter the element to be inserted: 5
Enter your choice: 2
The poped element: 5
Enter your choice: 4
The stack elements are:
1
2
1
Enter your choice: 3
It’s a Palindrome
Enter your choice: 5
