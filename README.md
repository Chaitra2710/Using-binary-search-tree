# Using-binary-search-tree
#include <stdio.h> 

#include <stdlib.h> 

struct Node 

{ 

int data; 

struct Node *left, *right; 

}; 

struct Node* newNode(int key) 

{ 

struct Node* node = (struct Node*)malloc(sizeof(struct 

Node)); 

node->data = key; 

node->left = node->right = NULL; 

return node; 

} 

struct Node* kthSmallest(struct Node* root, int* counter, int k) 

{ 

  

if (root == NULL) { 

return NULL; 

} 

  

struct Node* left = kthSmallest(root->left, counter, k); 

  

if (left != NULL) { 

return left; 

} 

  

if (++(*counter) == k) { 

return root; 

} 

return kthSmallest(root->right, counter, k); 

} 

struct Node* findKthSmallest(struct Node* root, int k) 

{ 

  

int counter = 0; 

return kthSmallest(root, &counter, k); 

} 

int main(void) 

{ 

struct Node* root = newNode(7); 

root->right = newNode(10); 

root->left = newNode(4); 

root->left->left = newNode(3); 

root->right->right = newNode(20); 

root->right->right->left = newNode(15); 

printf("Given elements are : 7 10 4 3 20 15 "); 

printf("\n Enter k value: "); 

int k; 

scanf("%d",&k); 

struct Node* result = findKthSmallest(root, k); 

if (result) { 

printf("%d'th smallest node is %d", k, result->data); 

} 

else { 

printf("%d'th smallest node does not exist.", k); 

} 

return 0; 

}
