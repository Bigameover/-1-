# -1-
The beginning  of a rookie.
//可变数组。
#include<stdio.h>
#include<stdlib.h>
#define max_size 8
#define more_size 10
typedef struct Array{
	int *array;
	int size;
}Array;
void inflate_array(Array *a);
Array create_array();
void free_array(Array *a);
void printf_array(const Array *a);
int get_number(const Array p,int x); 
int main(){
	Array a;
	a = create_array();
	printf_array(&a);
	get_number(a,5);
	free_array(&a);
return 0;}
Array create_array(){
	Array p;
	int *surrenal;
	int x,y,cnt = 0;
	p.array = (int*)malloc(sizeof(int)*max_size);
	p.size  = max_size; 
	surrenal = p.array;
	printf("输入-1则输入结束。\n");
	y = 0; 
	while(y!=-1){
		scanf("%d",&y);
		*surrenal = y;
		surrenal++;
		cnt++;
		if(cnt==p.size){
			inflate_array(&p);
			surrenal=p.array+cnt; 
		} 
	}
return p;}
void printf_array(const Array *a){
	int *surrenal;
	int x;
	surrenal = a->array;
	for(x=0;x<a->size;x++){
		printf("%d\t",*surrenal);
		if((x+1)%6==0) printf("\n");
		surrenal++;
	}
} 
void free_array(Array *a){
	free(a->array);
	a->size  = 0;
	a->array = NULL;
}
void inflate_array(Array *a){
	int x;
	int *tip1,*tip2,*tip3;
	Array surrenal;
	surrenal.array = (int*)malloc(sizeof(int)*(more_size+a->size));
	surrenal.size  = more_size+a->size;
	tip1 = surrenal.array;
	tip2 = a->array;
	for(x=0;x<a->size;x++){
		*tip1 = *tip2;
		tip1++;
		tip2++;
	}
	tip3 = a->array;
	a->array = surrenal.array;
	a->size  = surrenal.size; 
	free(tip3); 
}
int get_number(const Array p,int x){
	int *pice,y;
	pice = p.array;
	for(y=0;y<p.size;y++){
		if(*pice == x) printf("%d\n",y+1);
		pice++;
	}
return 0;} 
