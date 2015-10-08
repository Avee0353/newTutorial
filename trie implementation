#include<bits/stdc++.h>
using namespace std;
#define size 26
struct trie{
	bool is_end;
	int prefix_count;
	trie* child[size];
};
trie*init()
{
	trie*head=new trie();
	head->prefix_count=0;
	head->is_end=false;
	return head;
}
trie*insert(trie*head,string word)
{
	trie*current=head;
	current->prefix_count++;
	for(int i=0;i<word.length();i++)
	{
		int pos=(int)word[i]-(int)'a';
		if(current->child[pos]==NULL)
		current->child[pos]=new trie();
		current->child[pos]->prefix_count++;
		current=current->child[pos];
	}
	current->is_end=true;
	return head;
}
bool search(trie*head,string word)
{
	trie*current=head;
	for(int i=0;i<word.length();i++)
	{
		if(current->child[(int)word[i]-(int)'a']==NULL)
		return false;
		current=current->child[(int)word[i]-(int)'a'];
	}
	return current->is_end;
}
int pre_count(trie*head,string word)
{
	trie*current=head;
	if(current->child[(int)word[0]-(int)'a']==NULL)
	return 0;
	else
	{
		for(int i=0;i<word.length();i++)
		{
			if(current->child[(int)word[i]-(int)'a']==NULL)
			return 0;
			current=current->child[(int)word[i]-(int)'a'];
		}
		return current->prefix_count;
	}
	
}
void print(trie*head)
{
	trie*current=head;
	if(head==NULL)
	{
		cout<<"\n";
		return;
	}

	for(int i=0;i<26;i++)
	{
		if(current->child[i]!=NULL)
		{
			cout<<(char)(i+97);
			print(current->child[i]);
		}
	}
}
void print_prefix(trie*head,string word)
{
	trie*current=head;
	if(current->child[(int)word[0]-(int)'a']==NULL)
	return;
	for(int i=0;i<word.length();i++)
	{
		current=current->child[(int)word[i]-(int)'a'];
	}
	print(current);
}
int main()
{
	trie*head;
	head=init();
	int n;
	string str;
	cout<<"enter the number of words want to insert\n";
	cin>>n;
	for(int i=0;i<n;i++)
	{
		cin>>str;
		head=insert(head,str);
	}
	cout<<"enter the string you want to search\n";
	cin>>str;
	if(search(head,str))
	{
		cout<<"string found\n";
	}
	else
	cout<<"not found\n";
	cout<<"enter prefix\n";
	cin>>str;
	cout<<pre_count(head,str)<<endl;
	cout<<"string to find all ocuureces with the given prefix\n";
	cin>>str;
	print_prefix(head,str);
}
