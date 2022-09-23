# Pay1oad 1학년 2학기
======================
1주차 CODE UP 문제풀이 
----------------------
1024번
배열 입출력 문제로 이 문제를 풀 정도면      
기본적인 배열 입출력을 알 수 있다고 하지 않을까 한다.   
C입문자인 나한테 의미 깊었던 문제였다...(저번주에 배열 베웠음)   

최종 코드다.    
#include <stdio.h>   

int main() {   
	char a[20];   
	int i = 0;     
	scanf_s("%s", &a, sizeof(a));    
	for (i = 0; a[i] != '\0'; i++) {    
		printf("\'%c\'", a[i]);     
		printf("\n");       
	}        
}    

앞으로 많이 쓸 것 같다.    
for문중 두번째 공간을 약간 자동반사적으로 범위를 쓰곤 했는데       
for이라는 것 자체가 두번째 공간이 조건이라는 것을 잊지 않았으면 한다     
선언후 scanf로 받은 후 반복문을 설정하여 배열을 출력하는 코드다.    

1019번    
굉장히 삽질을 많이 했던 문제다.     
첫번째 생각했던 아이디어는		
년월일을 각기 다른 공간에 받은후	
월, 일을 만약 10보다 작다면 앞에 0을 붙이는 코드를 생각했다.	
자리수와 int가 아니면 안되도록 오류처리까지 붙여서 코드를 짰었다.	
그렇게 삽질을 하다 문득 수업떄 들은 내용을 복습하다	
위 코드를 발견했다     	   
#include <stdio.h>       	    	   	

int main(void) {             		
	int y, m, d;      	    	
	scanf("%d.%d.%d", &y, &m, &d);     	     		
	printf("%04d.%02d.%02d", y, m, d);      	        		
	return 0;      		         
}      		               
cplusplus.com에 보면 printf에 이런 비슷한 예제가 나오는데 자릿수를 출력하는 방법이다.     	   
삽질을 치우고 다시 간단한 코드로 이렇게 만들었다.	
첫번째 아이디어도 물론 좋겠지만 위 아이디어가 더 좋은 것 같다.      	
나중에 첫번쨰 아이디어로 코드 완성할 예정이다.      	

1038번
scanf과정에서 계속 예외 처리가 안되었다고 애먹었던 문제다.
코드에 문제가 없는 것 같은데 뭐가 문제일까 정말 많은 고민을 했다.
#include <stdio.h>    

#include <stdio.h>    

int main() {    
	int num1=0;    
	int num2=0;    
	int res=0;    
	char oper;     

	scanf_s("%d %c %d", &num1, &oper, 1, &num2);     
		
	switch (oper)         
	{     	
	case '+':	    
		

		printf("%d", num1 + num2);     	
		break;      

	case '-':     
		

		printf("%d", num1 - num2);     
		break;     

	case '*':      
		

		printf("%d", num1 * num2);     
		break;     

	case '/':     
	
		if (num2 == 0) {      
			printf("0으로 나눌 수 없습니다.");     
			break;     
		}     
		else{      
			printf("%d", num1 / num2);     
			break;      
		}     
		
	}      


}     
왜 num1, num2 값이 담기지 않을까 고민을 했다.      
근데 도저히 모르겠다. 맞는 문제인 것 같은데 왜 안되는지 도저히 모르겠다.      
