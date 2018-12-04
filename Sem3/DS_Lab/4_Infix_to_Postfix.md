#define size 50 /* size of stack */

#include <ctype.h>
#include <stdio.h>

char s[size];
int top = -1; /* global declarations */

push(char elem) /* function for push operation */
 {
  s[++top] = elem;
 }

char pop() /* function for pop operation */
 {
  return (s[top--]);
 }

int pr(char elem) /* function for precedence */
 {
  switch (elem)
  {
   case '#':return 0;
   case '(':return 1;
   case '+':
   case '-':return 2;
   case '*':
   case '/':
   case '%':return 3;
   case '^':return 4;
  }
 }

void main() /* main program */
 {
  char infx[50], pofx[50], ch, elem;
  int i = 0, k = 0;
  printf("\n\nEnter the infix expression ");
  scanf("%s", infx);
  push('#');
  while ((ch = infx[i++]) != '\0')
  {
   if (ch == '(')
    push(ch);
   else if (isalnum(ch))
    pofx[k++] = ch;
   else if (ch == ')')
    {
     while (s[top] != '(')
     {
      pofx[k++] = pop();
     }
     elem = pop(); /* remove ( */
    }
  else /* operator */
  {
   while (pr(s[top]) >= pr(ch))
   {
    pofx[k++] = pop();
   }
   push(ch);
  }
  }
  while (s[top] != '#') /* pop from stack till empty */
   {
    pofx[k++] = pop();
   }
  pofx[k] = '\0'; /* make pofx as valid string */
  printf("\n\n Given infix expression: %s\n postfix expression is: %s\n", infx, pofx);
 }


# Output

Enter the infix expression (a+b)*c/d^5%1
Given Infix Expn: (a+b)*c/d^5%1
Postfix Expn: ab+c*d5^/1%
