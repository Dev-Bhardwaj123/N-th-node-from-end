# N-th-node-from-end
Find the n th node from the end of the linked list
//N th node from end of LL
#include<iostream>
using namespace std;

struct Node{
	int data;
	Node* next;
	Node(int d){
		data=d;
		next=NULL;
	}
};

void nthNodeEnd(Node* head,int n){
	if(head=NULL){
		return;
	}
	Node* fast=head;
	for(int i=0;i<n;i++){
		if(fast==NULL){
			return;
		}
		fast=fast->next;
	}
	Node* slow=head;
	while(fast!=NULL){
		slow=slow->next;
		fast=fast->next;
	}
	cout<<(slow->next);
}

Node* insertAtEnd(Node* head,int x){
	Node* temp=new Node(x);
	if(head==NULL){
		return temp;
	}
	Node* curr=head;
	while(curr->next!=NULL){
		curr=curr->next;
	}
	curr->next=temp;
	return head;
}

void printList(Node* head){
	Node* curr=head;
	while(curr!=NULL){
		cout<<curr->data;
		curr=curr->next;
	}
}

int main(){
	Node* head=NULL;
	int n;
	cin>>n;
	for(int i=1;i<=n;i++){
		int x;
		cin>>x;
		head=insertAtEnd(head,x);
	}
	printList(head);
	cout<<endl;
	nthNodeEnd(head,2);
	return 0;
}

