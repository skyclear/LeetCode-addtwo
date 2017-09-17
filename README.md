# LeetCode-addtwo
#include<iostream>
using namespace std;
struct ListNode{
int val;
ListNode *next;
ListNode(int x):val(x),next(NULL){}
};
class Solution{
public:
	ListNode* addtwonum(ListNode *l1,ListNode *l2){
	ListNode prehead(0);
	ListNode *p=&prehead;
	int extra=0,sum=0;
	while(l1||l2||extra){
	sum=(l1?l1->val:0)+(l2?l2->val:0)+extra;
	extra=sum/10;
	(*p).next=new ListNode(sum %10);
	p=p->next;
	l1=l1?l1->next:0;
	l2=l2?l2->next:0;
	}
	return prehead.next;
	}
};
void main(){
char input1[10];
char input2[10];
cin>>input1>>input2;
ListNode l1(0),*p1=&l1;
ListNode l2(0),*p2=&l2;

int i=0;
while(input1[i]){
	p1->next=new ListNode(input1[i]-'0');
	p1=p1->next;
	i++;
}
i=0;
while(input2[i]){
	p2->next=new ListNode(input2[i]-'0');
	p2=p2->next;
	i++;
}
Solution so;
ListNode *result=so.addtwonum(l1.next,l2.next);
while(result){
cout<<result->val;
result=result->next;
}
}
