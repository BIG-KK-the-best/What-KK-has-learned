/*有一个字符串s,他想知道这个字符串是否含有非重叠AB和BA。(如ABA不存在非重叠AB和BA，ABBA存在)*/

#include<stdio.h>
#include<string.h>
int main() {
	char a[99999];  
	while(gets(a)!=NULL) {
		char ch1[]="AB";
		char ch2[]="BA";
		//先查找AB在前，BA在后的情况 
		char *ret1=strstr(a,ch1);
		char *ret2=NULL;
		int i = 0;
		while(ret1!=NULL&&i!=2) {
			ret1++;
			i++;
		}
		int ok=0;
		if(ret1!=NULL)//防止runtime error 
			ret2=strstr(ret1,ch2);
		if(ret1!=NULL&&ret2!=NULL)
			ok=1;
			//查找BA在前，AB在后的情况 
		char *ret3=strstr(a,ch2);
		char *ret4=NULL;
		int j=0;
		while(ret3!=NULL&&j!=2) {
			ret3++;
			j++;
		}
		if(ret3!=NULL)
			ret4=strstr(ret3,ch1);
		if(ret3!=NULL&&ret4!=NULL)
			ok=1;
		if(ok) {
			printf("存在\n");
		} else {
			printf("不存在\n");
		}
	}

	return 0;
}
