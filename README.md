# binarysearchtreeoperations
#include<stdio.h>
#include<stdlib.h>
struct node
{
	int data;
	struct node*left;
	struct node*right;
};
typedef struct node *bstnode;
bstnode insertnode(bstnode ,int);
void inorder(bstnode);
void preorder(bstnode);
void postorder(bstnode);
bstnode minelement(bstnode);
bstnode maxelement(bstnode);
int main()
{
	bstnode root=NULL;
	printf("enter the root node:");
	int choice,x;
	scanf("%d",&x);
	root=insertnode(root,x);
	do{
		printf("\n1.insertnode\n2.inorder\n3.preorder\n4.postorder\n5.minimum_element\n6.maximum element\n7.exit\n");
		printf("enter your choice:");
		scanf("%d",&choice);
		switch(choice)
		{
			case 1:
				printf("enter value:");
				scanf("%d",&x);
				insertnode(root,x);
				break;
			case 2:
				inorder(root);
				break;
			case 3:
				preorder(root);
				break;
			case 4:
				postorder(root);
				break;
			case 5:
				minelement(root);
				break;
			case 6:
				maxelement(root);
				break;
			case 7:
				break;					
			default:
				printf("enter valid choice");		
		}
	}while(choice!=7);
}
bstnode insertnode(bstnode node,int x)
{
	if(node==NULL)
	{
		node=(bstnode)malloc(sizeof(bstnode));
		node->data=x;
		node->left=node->right=NULL;
	}
	else
	{
		if(x<node->data)
			node->left=insertnode(node->left,x);
		else if(x>node->data)
			node->right=insertnode(node->right,x);	
	}
	return node;
}
void inorder(bstnode node)
{
	if(node!=NULL)
	{
		inorder(node->left);
		printf("%d\t",node->data);
		inorder(node->right);
	}
}
void preorder(bstnode node)
{
	if(node!=NULL)
	{
		printf("%d\t",node->data);
		preorder(node->left);
		preorder(node->right);
	}
}
void postorder(bstnode node)
{
	if(node!=NULL)
	{
		postorder(node->left);
		postorder(node->right);
		printf("%d\t",node->data);
	}
}
bstnode minelement(bstnode node)
{
	if(node==NULL)
		return NULL;
	else if(node->left==NULL)
			printf("%d",node->data);
		else
			return minelement(node->left);		
}
bstnode maxelement(bstnode node)
{
	if(node==NULL)
		return NULL;
	else if(node->right==NULL)
		printf("%d",node->data);
	else
		return maxelement(node->right);		
}
