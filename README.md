#include<bits/stdc++.h>
using namespace std;

int arr[5]={1,2,3,4,5};
struct node {
int DateTIme;
string owner_name;
string address;
int mobile;
float value;
int Node_Number=0;
int Node_id;
struct node *ref_NodeId;
int  child_NodeId;
node *child[5];
node *next;
node *parent;
struct node *ref_ChildNodeId;
};

 struct node* first_node= new node;

void create_firstNode()
{
    first_node->owner_name= "shubham";
    first_node->address="ymca university, faridabad";
    first_node->mobile= 74684656;
    first_node->value= 2.23;
    first_node->Node_Number= 1;
    first_node->Node_id= rand() %100;
    first_node->ref_NodeId= NULL;
    first_node->child_NodeId= NULL;
    first_node->ref_ChildNodeId= NULL;
    first_node->parent=NULL;
    first_node->next=NULL;
}

void multi_set(int i, string name, string address, int mobile, float value)
{

        node * node1= new node();
        first_node->child[i]= node1;
        node1->Node_Number=arr[i];
        node1->owner_name=name;
        node1->address=address;
        node1->mobile=mobile;
        node1->value=value;
        node1->Node_id=rand()% 100;
        node1->parent=first_node;
        node1->child_NodeId= NULL;
        node1->ref_ChildNodeId= NULL;
        node1->next=NULL;
}

void add_newNode(int nodenumber, string name, string address, int mobile, float value)
{
    node * node1 =new node();
    node *ptr= first_node->child[nodenumber-1];

    while(ptr->next!=NULL)
    {
        ptr= ptr->next;
    }

        node1->owner_name=name;
        node1->address=address;
        node1->mobile=mobile;
        node1->value=value;
        node1->Node_id=rand()% 100;
        node1->parent=ptr;
        node1->child_NodeId= NULL;
        node1->ref_ChildNodeId= NULL;
        node1->next=NULL;

    ptr->next=node1;

}


void encrypt_data(){
	string s;
        char len;
    static const char password[] =
        "0123456789"
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        "abcdefghijklmnopqrstuvwxyz";

    for (int i = 0; i < len; ++i) {
        s[i] = password[rand() % (sizeof(password) - 1)];
    }
    
    


}


int main()
{
    int option;
    cin>>option;

    switch(option)
    {
        case 1: create_firstNode();
        break;

        case 2:
    for(int i=0;i<5;i++)
    {
        string name,address;
        int mobile, value;
        cin>>name>>address>>mobile>>value;
        multi_set(i, name, address, mobile, value);
    }
        break;

        case 3 :
            cout<<"Enter node number to which you wants to add node";
            int nodenumber;
            cin>>nodenumber;
            string name,address;
            int mobile, value;
            cin>>name>>address>>mobile>>value;
            add_newNode(nodenumber, name, address, mobile, value);\
            break;
            
        case4: encrypt_data();
            
    }

    return 0;
}

