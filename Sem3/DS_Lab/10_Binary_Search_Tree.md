```
#include <stdio.h>
#include <stdlib.h>
struct BST
 {
  int data;
  struct BST *left;
  struct BST *right;
 };

typedef struct BST NODE;
NODE *node;

NODE* createtree(NODE *node, int data)
 {
  if (node == NULL)
   {
    NODE *temp;
    temp= (NODE*)malloc(sizeof(NODE));
    temp->data = data;
    temp->left = temp->right = NULL;
    return temp;
   }
  if (data < (node->data))
   {
    node->left = createtree(node->left, data);
   }
  else if (data > node->data)
   {
    node -> right = createtree(node->right, data);
   }
  return node;
 }

NODE* search(NODE *node, int data)
 {
  if(node == NULL)
   printf("\nElement not found");
  else if(data < node->data)
   {
    node->left=search(node->left, data);
   }
  else if(data > node->data)
   {
    node->right=search(node->right, data);
   }
  else
   printf("\nElement found is: %d", node->data);
  return node;
 }

void inorder(NODE *node)
 {
  if(node != NULL)
   {
    inorder(node->left);
    printf("%d\t", node->data);
    inorder(node->right);
   }
 }

void preorder(NODE *node)
 {
  if(node != NULL)
   {
    printf("%d\t", node->data);
    preorder(node->left);
    preorder(node->right);
   }
 }

void postorder(NODE *node)
 {
  if(node != NULL)
   {
    postorder(node->left);
    postorder(node->right);
    printf("%d\t", node->data);
   }
 }

NODE* findMin(NODE *node)
 {
  if(node==NULL)
   {
    return NULL;
   }
  if(node->left)
   return findMin(node->left);
  else
   return node;
 }

NODE* del(NODE *node, int data)
 {
  NODE *temp;
  if(node == NULL)
   {
    printf("\nElement not found");
   }
  else if(data < node->data)
   {
    node->left = del(node->left, data);
   }
  else if(data > node->data)
   {
    node->right = del(node->right, data);
   }
  else
   {
    if(node->right && node->left)
     {
      temp = findMin(node->right);
      node -> data = temp->data;
      node -> right = del(node->right,temp->data);
     }
    else
     {
      temp = node;
      if(node->left == NULL)
      node = node->right;
      else if(node->right == NULL)
      node = node->left;
      free(temp); /* temp is longer required */
    }
   }
  return node;
 }

void main()
 {
  int data, ch, i, n;
  NODE *root=NULL;
  clrscr();
  while (1)
   {
    printf("\n1.Insertion in Binary Search Tree");
    printf("\n2.Search Element in Binary Search Tree");
    printf("\n3.Delete Element in Binary Search Tree");
    printf("\n4.Inorder\n5.Preorder\n6.Postorder\n7.Exit");
    printf("\nEnter your choice: ");
    scanf("%d", &ch);
    switch (ch)
     {
      case 1: printf("\nEnter N value: " );
              scanf("%d", &n);
              printf("\nEnter the values to create BST like(6,9,5,2,8,15,24,14,7,8,5,2)\n");
              for(i=0; i<n; i++)
               {
                scanf("%d", &data);
                root=createtree(root, data);
               }
              break;
      case 2: printf("\nEnter the element to search: ");
              scanf("%d", &data);
              root=search(root, data);
              break;
      case 3: printf("\nEnter the element to delete: ");
              scanf("%d", &data);
              root=del(root, data);
              break;
      case 4: printf("\nInorder Traversal: \n");
              inorder(root);
              break;
      case 5: printf("\nPreorder Traversal: \n");
             preorder(root);
             break;
      case 6: printf("\nPostorder Traversal: \n");
             postorder(root);
             break;
      case 7: exit(0);
      default:printf("\nWrong option"); 
             break;
     }
   }
 }


Output


Program For Binary Search Tree
1.Create
2.Search
3.Recursive Traversals
4.Exit
Enter your choice :1
Enter The Element 15
Want To enter More Elements?(1/0)1
Enter The Element 25
Want To enter More Elements?(1/0)1
Enter The Element 35
Want To enter More Elements?(1/0)1
Enter The Element 45
Want To enter More Elements?(1/0)1
Enter The Element 5
Want To enter More Elements?(1/0)1
Enter The Element 7
Want To enter More Elements?(1/0)0
Enter your choice :2
Enter Element to be searched :7
The 7 Element is Present
Parent of node 7 is 5
1.Create
2.Search
© Vivekananda College of Engg. & Technology, Puttur (D.K) 51
3.Recursive Traversals
4.Exit
Enter your choice :2
Enter Element to be searched :88
The 88 Element is not Present
Enter your choice :3
The Inorder display : 5 7 15 25 35 45
The Preorder display : 15 5 7 25 35 45
The Postorder display : 7 5 45 35 25 15
Enter your choice :4
