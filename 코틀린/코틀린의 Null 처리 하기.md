* ? 연산자 
   데이터가 null이 들어올 수 있음을 확인하는 연산자
   
* ?: 연산자 (엘비스 연산자) 
   데이터가 null일 경우  데이터를 치환해준다.
	   
	```kotlin
	//saveData의 id가 널일 경우 0L을 반환한다.
	val id = saveData.id?: 0L

	```


	