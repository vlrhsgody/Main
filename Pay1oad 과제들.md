# Pay1oad 1학년 2학기

1주차 CODE UP 문제풀이 
----------------------
1.1024번
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

2.1019번    
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

3.1038번
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
문제 해결 : scanf_s 문제다. 무지성으로 scanf_s 범위값 이렇게 하니까 틀린거였다.    
1을 넣어서 그 버퍼의 크기가 1임을 명시해야 한다.    

4.1079번    
이번에는 scanf_s에서 문자열이 받아지지 않는다
int main() {     
	char arr[100];     
	int i = 0;     
	///if(scanf_s("%s", arr, sizeof(arr))==1); 
	scanf_s("%s", arr, sizeof(arr));    
위 코드에 t r e w q 를 넣었더니 다음과 같은 값이 담겼다.     
왜 각각의 문자가 담기지 않는 것 일까?     
&arr	0x00affb60 {116 't', 0 '\0', -2 '?', -2 '?', -2 '?', -2 '?', -2 '?', -2 '?', -2 '?', -2 '?', -2 '?', ...}	char[100] *   

#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main() {
	char arr[100] = "";
	int i = 0;
	scanf("%s", arr);

		while (arr[i] != '112') {
			for (i = 0; i < 100; i++) {
				if (arr[i] != '\0') {

					printf("%c\n", arr[i]);
				}
				else {
					printf("\n");
				}


			}
			printf("%c", 113);
			break;


		}

}  


	}     
}     

5.1090번    
마지막으로 1090번이다.    

등비수열은     
pow()함수로 구성했다.    
그러나 마지막 케이스 10^10을 어떻게 구현해야 할지 몰랐다.     
자료형 int에서 longlong까지 키워도 역부족이었다.     
오버플로우 문제구나, 깨달았다.    
    
해결방법 1. long long int로 10^10까지 구현한다.    
이 방법으로 푸는 사람도 있다     
long long 까지는 들어봤는데 long long int 로 구현하는 사람은 처음 봤다.       
![image](https://user-images.githubusercontent.com/106510018/192133341-fee71058-655c-4c40-8f3d-9f66a3ce1e76.png)    
다음은 C에서의 자료형을 정리한 것이다. 참고바람        
    
근데 이게 진짜 해결방법인가?     
이거 말고 다른 방법이 해결방법이 없는가?    

2주차 C로 http 구현하기     
------------------------------------------
https://xn--z92bu70c.kr/86
위 웹사이트를 통해 코드를 작성했다.


#include <stdio.h>
#include <WinSock2.h>
#include <Windows.h>
#pragma comment(lib, "ws2_32.lib")
#define _CRT_SECURE_NO_WARNINGS
#define _WINSOCK_DEPRECATED_NO_WARNINGS
#define BUFF_SIZE 1024

int main() {

	WSADATA wsa;
	struct hostent* host;
	char msg[BUFF_SIZE];

	if (WSAStartup(MAKEWORD(2, 2), &wsa) != 0)
	{
		perror("WSAStart Error ");
		system("pause");
		return -1;
	}

	SOCKET sock = socket(PF_INET, SOCK_STREAM, 0);
	SOCKADDR_IN addr;

	if (sock == INVALID_SOCKET)
	{
		perror("Sock Error ");
		system("pause");
		return -1;
	}
	host = gethostbyname("www.google.co.kr");

	addr.sin_family = AF_INET;
	addr.sin_port = htons(80);
	addr.sin_addr.s_addr = inet_addr(inet_ntoa(*(struct in_addr*)*host->h_addr_list));

	if (connect(sock, (SOCKADDR*)&addr, sizeof(addr)) == SOCKET_ERROR)
	{
		printf("Not Connect \n");
		system("pause");
		return 1;
	}
	send(sock, "GET / HTTP/1.1\r1nHost : wwww.google.co.kr\r\n\r\n", strlen("GET / HTTP/1.1\R\nHost : www.google.co.kr\r\n\r\n"), 0);
	recv(sock, msg, BUFF_SIZE, 0);

	printf("%s \n", msg);

	closesocket(sock);
	WSACleanup();
	system("pause");

	return 0;
}


스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야스택 오퍼플로우는 신이야    

https://stackoverflow.com/questions/22077802/simple-c-example-of-doing-an-http-post-and-consuming-the-response    

#include <stdio.h> /* printf, sprintf */
#include <stdlib.h> /* exit */
#include <io.h> /* read, write, close */
#include <string.h> /* memcpy, memset */
#include <winsock.h> /* socket, connect */
/* struct sockaddr_in, struct sockaddr */
/* struct hostent, gethostbyname */
#include <winsock2.h>
#include <ws2tcpip.h>
#include <stdio.h>

#pragma comment(lib, "Ws2_32.lib")
void error(const char *msg) { perror(msg); exit(0); }

int main(int argc, char *argv[])
{
	/* first what are we going to send and where are we going to send it? */
	int portno = 80;
	char *host = "api.somesite.com";
	char *message_fmt = "POST /apikey=%s&command=%s HTTP/1.0\r\n\r\n";

	struct hostent *server;
	struct sockaddr_in serv_addr;
	int sockfd, bytes, sent, received, total;
	char message[1024], response[4096];

	if (argc < 3) { puts("Parameters: <apikey> <command>"); exit(0); }

	/* fill in the parameters */
	sprintf(message, message_fmt, argv[1], argv[2]);
	printf("Request:\n%s\n", message);

	/* create the socket */
	sockfd = socket(AF_INET, SOCK_STREAM, 0);
	if (sockfd < 0) error("ERROR opening socket");

	/* lookup the ip address */
	server = gethostbyname(host);
	if (server == NULL) error("ERROR, no such host");

	/* fill in the structure */
	memset(&serv_addr, 0, sizeof(serv_addr));
	serv_addr.sin_family = AF_INET;
	serv_addr.sin_port = htons(portno);
	memcpy(&serv_addr.sin_addr.s_addr, server->h_addr, server->h_length);

	/* connect the socket */
	if (connect(sockfd, (struct sockaddr *)&serv_addr, sizeof(serv_addr)) < 0)
		error("ERROR connecting");

	/* send the request */
	total = strlen(message);
	sent = 0;
	do {
		bytes = write(sockfd, message + sent, total - sent);
		if (bytes < 0)
			error("ERROR writing message to socket");
		if (bytes == 0)
			break;
		sent += bytes;
	} while (sent < total);

	/* receive the response */
	memset(response, 0, sizeof(response));
	total = sizeof(response) - 1;
	received = 0;
	do {
		bytes = read(sockfd, response + received, total - received);
		if (bytes < 0)
			error("ERROR reading response from socket");
		if (bytes == 0)
			break;
		received += bytes;
	} while (received < total);

	/*
	 * if the number of received bytes is the total size of the
	 * array then we have run out of space to store the response
	 * and it hasn't all arrived yet - so that's a bad thing
	 */
	if (received == total)
		error("ERROR storing complete response from socket");

	/* close the socket */
	close(sockfd);

	/* process response */
	printf("Response:\n%s\n", response);

	return 0;
}    



3주차 어셈블리어 구구단
------------------------

다들 흔히 있는 VMware에 들어가서
vim으로 C로 만든 구구단을 만든 후
gdb를 사용하여 어셈블리어로 표현할 예정이다.
![image](https://user-images.githubusercontent.com/106510018/200172182-81efcf7b-ce9a-41ce-9b30-dd9d5140969b.png)

![image](https://user-images.githubusercontent.com/106510018/200172191-00085bc2-7893-41d0-b42c-059861d635b6.png)

이렇게 C로 된 구구단을 어셈블리어로 표현할 수 있다.
다음은 코드다 cat으로 출력했는데 어디갔는지 사라짐;;
#include <stdio.h>

int a;
int b;

int main() {
	for (a = 1; a < 10; a++) {
		for (b = 1; b < 10; b++) {
			printf("%d x %d = %d \n", a, b, a * b);
		}
	}
}

시간이 된다면 위 코드로 학부연구생때 쓸 handray를 연습할 예정이다. 


+) Handray
----------------------------------

https://ethan-ncs.tistory.com/8
위 티스토리에 있는 핸드레이를 따라 해봤다. 도움이 많이 되는 것 같다.
![image](https://user-images.githubusercontent.com/106510018/200726800-52478e7c-db5e-4e3f-843b-0d7e87fcd8c6.png)
![image](https://user-images.githubusercontent.com/106510018/200726844-fee4ecc5-56dd-41a0-93ca-8d8c46ef6059.png)

4주차 Old School hack techniques
---------------------------

https://virtualarmour.com/5-old-school-hack-techniques-that-still-work-how-to-protect-your-data/
Old School 기법은 역사가 깊은 혹은 오랫도안 사용이 되어왔던 해킹 기법을 의미한다.
대표적으로 5개의 기벙이 존재한다.

1. 사회공학적 기법
사회 공학적 기법은 피싱 사기에서 중요한 역할을 한다. 인간의 심리를 이용하는 해킹 기법이다. 통신망 보안 정보에 접근 권한이 있는 담당자와 신뢰를 쌓고 전화나 이메일을 통해 그들의 약점과 도움을 이용하는 것이다. 간단하게 예를 들어보자. 내가 만약 교수님께 과제 제출용으로 메일을 쓴다고 하자. 그렇다면 교수님은 나에 대한 신뢰가 있기 때문에 과제제출용으로 올린 파일을 아무런 의심도 없이 여실 것이다. 하지만 만약 거기에 랜섬웨어 혹은 바이러스가 있었다면 그대로 사회공학적 기법에 당하게 된다.

2. 신원 도둑질
신원 도용은 엄밀히 말하자면 사이버 보안 문제는 아니지만 디지털 시스템에 대한 무단 엑세스를 얻는데 사용될 수 있다. 민감 정보에 엑세스할 수 있는 경우 해당 정보를 사용하여 사기 또는 위에서 언급했던 사회공학적 기법으로 또 다른 피해자를 만들 수도 있다. 암호를 자주 바꾸고 유추하기 힘들게 암호를 설정하면 막을 수 있다. 모든 사이트에 암호를 다르게 한다면 충분히(사용자 입장에서는)방어 할 수 있다.(이상한 웹사이트에 가입하지 않는 한)

3. 디도스 공격
대규모 해커 그룹이나 많은 수의 봇 컴퓨터를 제어하는 해커에 의해서 수행한다. 그런 다음 모든 플레이어가 요청으로 대상 조직의 서버를 망치고 서버가 충돌하고 비지느사 중단이 된다. 최근 보안이 취약한 IOT가 디도스 공격에 악용될 수 있기 때문에(작은 디바이스라도 있을 것은 다 있기에) 상당히 큰 보한 위협이 될 수 있다. 또한 사실상 디도스 공격을 위한 완벽한 방어는 존재하지 않는다. 막을 수 있는 최선의 수는 외국쪽에서 오는 것들을 통신사를 통해 최대한 막고, 수용량을 늘리는 방법 밖에 없다. 
방화벽을 최신 상태로 유지하고, 스팸 필터를 사용하고, 부하 분산 조치를 구현하여 네트워크 인프ㅡ라가 안전한지 확인해야 한다. 
평창올림픽때 러시아쪽에서 이러한 공격이 많이 들어왔다고 수업시간 때 베웠다.

4. 온라인 사기

5. 익스플로잇 킷
손상된 웹 사이트의 약점을 이용하여 트래픽을 전환하거나, 맬웨어(악성소프트웨어)를 실행하거나, 개인 사용자 데이터(사용자 이름 및 암호 포함)를 캡처하는 자동화된 사이버 보안 위협이다. 이러한 소규모 프로그램은 설치하는데 많은 전문적인 기술 지식이 필요하지 않고 한 번에 손상된 여러 웹사이트에 쉽게 배포할 수있기 때문에 특히 악독하다. 다크웹에서 쉽게 구매나 대여할 수 있다. 이런 익스플로잇 킷은 취약한 웹 사이트에 의존하기 때문에 기본적인 예방 조치를 취하는 것이 가장 중요하다. 웹 사이트가 릴리스된 새로운 보안 패치를 활용할 수 있도록 소프트웨어를 최신 상태로 유지하고 의시미스러운 웹 사이트 활동을 주시하는 것이 포함된다.

구식 해킹 기술은 여전히 효과적이기 때문에 주변에 널리 있다. 띠지털 자산을 보호하려면 강력하면서 적용 가능한 플레이어북을 만들어 의심스러운 활동을 감지하도록 직원들을 교육하고, 모든 최신 사이버 보안 여누겡 대한 최신 정보를 유지해야 한다.










