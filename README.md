Programmer
==========

Programmes using C,C++,PHP, Datastructures and oops. 



Link list program:


#include<iostream.h>
#include<conio.h>
struct linklist
{
       int val;
       struct linklist *next;
       //int *prev;
};
void insert(struct linklist **head,int v);
void print(struct linklist **head);
int search(linklist **head,int v);
void del(struct linklist **head,int v);

void insert(struct linklist **head,int v)//To create or insert into the linklist
{
     cout<<"insert value"<<endl;
     linklist *temp;
     linklist *r;
     //temp=*head;
     
     
     if(*head==NULL)
     {
                    cout<<"hello";//to check
                    temp = new linklist[sizeof(linklist)];
                    temp->val=v;
                    temp->next=NULL;
              
                    
                    *head=temp;
     }       
     else
     {
         //cout<<"hii";//to check
         temp = new linklist[sizeof(linklist)];
         temp->val=v;
         temp->next=NULL;
         r=*head;
         while(r->next!=NULL)
         {
                             //cout<<"not null"<<endl;
                             r=r->next;
         }
         r->next=temp;

     }
      cout<<endl<<"value inserted is:"<<temp->val;
}

void printlist(struct linklist **head)//To print values of linklist
{ 
     if(*head==NULL)
     {
                    cout<<"List is empty"<<endl;
     }
     else
     {
                    
                    linklist *list;
                    list=*head;
                    
                    for(list=*head;list->next!=NULL;list=list->next)
                    {
                        cout<<list->val<<" ";
                    }
                    cout<<list->val;
     }
}

int search(linklist **head,int v)
{
    linklist *r;
    r=*head;
    int count=0;
    while(r->val!=v && r->next!=NULL)
    {
                    count++;
                    r=r->next;                
                    
    }
    if(r->val==v)
    {
                 cout<<"value found at:";
                 return (count);
    }
    else
    {
                 cout<<"value not found:";
                 return 0;
    }
}

void del(linklist **head,int v)
{
     int flag=0;
     linklist *r;
     r=*head;
     if(r->val==v)
     {
                  *head=r->next;
                  cout<<"value is head itself"<<endl;
                  goto end;
     }
     while(r->next!=NULL)
     {
                         cout<<"yes"<<endl;
         if((r->next)->val==v)
         {
                            cout<<r->next->val<<"in"<<endl;  
                              flag=1;
                 // cout<<"found";
                  r->next=(r->next)->next;
                  cout<<"value is deleted"<<endl;
                  break;
         }              
         r=r->next;
     }
     if(flag!=1)
     cout<<"value not found";
     end:cout<<"end";
}

int main()
{
    linklist *head=NULL;
    int v;
    char ch='y';
    while(ch=='y')
    {
    cout<<"enter the value:";
    cin>>v;
    insert(&head,v);//insert into list
    cout<<"enter choice:";
    cin>>ch;
    }
    printlist(&head);
    cout<<endl<<"enter the value to be searched:";
    cin>>v;
    int key=search(&head,v);//search into list
    cout<<key;
    cout<<"enter the value to be deleted:";
    cin>>v;
    del(&head,v);//delete from list
     printlist(&head);
    getch();
}
