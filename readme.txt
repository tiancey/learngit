#include <stdio.h>


void save(char* suc,int len,char * dest)
{
	int i;
	for(i=0;i<len;i++)
	{
		dest[i] = suc[i];
	}
	dest[len] = 0;
}

void main()
{
	char command[30];
	char param[10][5];
	int i,flag,len;
	char * head;
	
	printf("Please enter the command\n");
	scanf("%s",command);
	
	head = command;
	for(i=0,len=0,flag =0;;i++,len++)
	{

		if(command[i]==',')
		{
			save(head,len,param[flag]);
			len = -1;
			flag++;
			head = &(command[i+1]);
		}
		else if(command[i]==0)
		{
			save(head,len,param[flag]);
			break;
		}
	}

	for(i=0;i<=flag;i++)
	{