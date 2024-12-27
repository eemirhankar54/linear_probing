# linear_probing
I coded the linear search method of hashing search.



#include <stdio.h>

int arr[10];

void print()
{
	printf("\n existing elements of the array");
	for(int i=0;i<10;i++)
	{
	printf("\n %d.index ==> %d",i,arr[i]);
	}
}



int hash(int search)
{
	return search % 10;
}



void insert(int add)
{
	int index = hash(add);
	if(arr[index] == 0)
		arr[index] = add;
	else 
	{
		int temp = index;
		while(arr[temp] != 0)
		{
			temp = (temp + 1)%10;
			if(temp == index)
			{
				printf("\n there is no empty");
				return;
			}		
		}
		arr[temp] = add;
	}
}
void Delete(int index)
{
	if(index >= 10 || index < 0) 
			printf("Enter the index less than 10.\n");
	else
	{
		arr[index] = 0;
		printf("\nElement at index %d has been deleted.\n", index);
	}
}

void searching(int search)
{
	int index = hash(search);
	if(arr[index] == search)
	{
		printf("\n The number you are looking for has been found (index) => %d",index);
		return;
	}
	int temp = index;
	while (arr[temp] != 0)
	{
		temp = (temp + 1)%10;
		if(temp == index)
		{
			printf("\n The number you are looking for could not be found");
			return;
		}
		if(arr[temp] == search)
		{
			printf("\n The number you are looking for has been found (index) => %d",temp);
			return;
		}	
	}	
}

void list()
{
	int i;
	for(i = 0;i < 10;i++)
	{
		printf("\n %d.index ==> %d",i,arr[i]);
	}
}


int main()
{
	insert(10);
	insert(11);
	insert(22);
	insert(77);
	insert(88);
	insert(67);
	insert(888);
	insert(112);
	insert(777);
	insert(221);
	insert(666);
	print();
	searching(221);
	searching(666);
	searching(777);
	Delete(0);
	Delete(10);
	Delete(-1);
	list();
	Delete(1);
	list();
	
	return 0;
} 
