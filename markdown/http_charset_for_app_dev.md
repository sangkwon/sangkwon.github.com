APP개발자를 위한 HTTP / Encoding
-----------------
* HTTP
	* HTTP란?
		* 프로토콜: HTTP, FTP, SSH, HTTPS
		* 포트: 80, 8080...
		* Proxy 란?
	* Request vs. Response
		* Header / Body
		* Request
			* GET
				* 데이터가 URL자체에(사실은 첫 라인에) 들어감
				* ?, & 등을 사용해서 분기: parameter 값 자체에 & 이 있을 경우에는 어떻게?
			* POST
				* 데이터가 body 에 들어감
			* 기타 다른 방식들
			* coupang-app
		* Response
			* Status Code 200, 404, 503, 500
	* Cookie
		* 저장위치
		* Http Header 사용하여 set(server->client)/get(client->server)

* Charset
	* Overview
		* ISO8859-1, CP949, EUC-KR
		* KSC5601
	* Ascii
		* 1byte(7bit)
		* 영문과 일부 특수문자만 표시 ==> 한글 등 표시 못함.
		* 0x41:A, 0x42:B
	* EUC-KR = KSC5601
		* 영문:1byte, 한글:2byte
		* 예전, Unix 한글언어에서 표준으로 사용했음. 많은 DB들도 이것.
		* 그러나, 글자수가 몇 개 안돼서, 표현 못하는 글자들 많음. 똠방각하.
	* Unicode(UCS2, UCS4)
		* 모든 언어의 글자가 전부 들어있음. (사실 대부분은 한자)
		* UCS2(2byte), UCS4(4byte)
			* http://www.unicode.org/charts/
			* http://www.utf8-chartable.de/unicode-utf8-table.pl
		* 모든 글자가 동일한 바이트 차지. (2 or 4)
			* Little Endian vs. Big Endian
		* 단점
			* 영문사용자 입장에서는 공간 2~4배 낭비.
			* 2byte중 0x00 를 포함하는 바이트도 있어서, C에서는 문자열이 끝난 것으로 인식. ex) 글 = 0xAE00

* Encoding
	* UTF-8(& UTF-16)
		* UCS2(& UCS4)로 1:1 변환.
		* 글자에 따라 1~3byte 차지: 영문자는 1바이트 차지, 동아시아 언어는 3바이트 차지.
		* 0x00 인 바이트 없어서 C 언어에서 문제 없음.
	* URLEncoding/URLDecoding
		* HTTP-GET 방식으로 값을 넣을 때에, 
		* % 들어가는 글자들. 영문자와 숫자를 제외한 글자들(특수문자, 한글) 등등을 글자 번호로 표시함.
		* 특히 &,?,# 등은 URL에서 특수한 의미를 지니므로 반드시 변환 필요
		* 어떤 charset 으로 인코딩하느냐에 따라 달라지므로, chartset 알아야함. (대부분 UTF-8 사용)
		* '글' = 0xEAB880(UTF-8) = %EA%B8%80
		* https://www.google.co.kr/?q=%EA%B8%80
	* Html Special Characters
		* html 마크업에서 특수 문자 지정. &OOO; 형태
		* ex) &lt; &amp; &gt;
	* Escape
		* \ 붙어있는 문자들. '\'는 일반 문자가 아니라 뭔가 특수한 상태로 escape 한다는 키워드.
		* ex) \n, \t, \\, \", \'

* WebServer, DB, Cache 서버 ....





