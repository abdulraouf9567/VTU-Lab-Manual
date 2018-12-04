```
#include<stdio.h>
#include<stdlib.h>
int a[20]; // Array declaration
int n,val,i,pos;
void create();
int display();
void insert();
int delete();

void main()
{
 int choice;
 printf("\n\n--------MENU-----------\n");
 printf("1.CREATE\n");
 printf("2.display\n");
 printf("3.INSERT\n");
 printf("4.DELETE\n");
 printf("5.EXIT\n");
 printf("-----------------------");
 while(1)
  {
   printf("\nENTER YOUR CHOICE:\t");
   scanf("%d",&choice);
   switch(choice)
    {
     case 1: create();
     break;
     case 2: display();
     break;
     case 3: insert();
     break;
     case 4: delete();
     break;
     case 5: exit(0);
     default: printf("\nInvalid choice:\n");
     break;
   }
 }
}

void create()
 {
  printf("\nEnter the size of the array elements:\t");
  scanf("%d",&n);
  printf("\nEnter the elements for the array:\n");
  for(i=0;i<n;i++)
  {
   scanf("%d",&a[i]);
  }
 }

int display()
 {
  if(n==0)
  {
   printf("\t Array is empty; no elements to display\n");
   return 0;
  }
  printf("\nThe array elements are:\n");
  for(i=0;i<n;i++)
  {
   printf("%d\t",a[i]);
  }
 }

void insert()
 {
  printf("\nEnter the position for the new element:\t");
  scanf("%d",&pos);
  if(pos<=n)
  {
   printf("\nEnter the element to be inserted :\t");
   scanf("%d",&val);
   for(i=n-1;i>=pos;i--)
   {
    a[i+1]=a[i];
   }
   a[pos]=val;
   n=n+1;
   display();
  }
  else
  {
   printf(" Invalid Position");
  }
 }

int delete()
 {
  if(n==0)
  {
   printf("\t Array is empty; no elements to delete \n");
   return 0;
  }
  printf("\nEnter the position of the element to be deleted:\t");
  scanf("%d",&pos);
  if(pos<=n-1)
  {
   val=a[pos];
   printf("\n Deleted element is =%d",val);
   for(i=pos;i<n-1;i++)
   {
    a[i]=a[i+1];
   }
   n=n-1;
   display();
  }
  else
  {
   printf(" Invalid Position");
  }
 }
 

Output
--------MENU-----------
1.CREATE
2.DISPLAY
3.INSERT
4.DELETE
5.EXIT

ENTER YOUR CHOICE: 1
Enter the size of the array elements: 3
Enter the elements for the array:
10 25 30
ENTER YOUR CHOICE: 2
The array elements are:
10 25 30
ENTER YOUR CHOICE: 3
Enter the position for the new element: 1
Enter the element to be inserted : 20
ENTER YOUR CHOICE: 2
The array elements are:
10 20 25 30
ENTER YOUR CHOICE: 4
Enter the position of the element to be deleted: 3
The deleted element is =30
enter your choice: 5
```
