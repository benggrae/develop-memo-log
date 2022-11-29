
 
###  Stream을 종결 연산자 이후에 재사용을 하면 IllegalStateException 발생 된다. 
```java 

List<String> list = List.of("2", "4");  

Stream<String> stream = list.stream();  
stream.count();  

//종결 연산자 count 이전에 수행하여 예외가 발생된다.  
assertThatExceptionOfType(IllegalStateException.class).isThrownBy(() -> {  
	stream.collect(Collectors.joining());  
});

```

![[Pasted image 20221113162627.png]]
### 재활용을 위한 트릭

Supplier 클래스를 활용하여 새로운 스트림을 반환하여 처리한다.
```java
List<String> list = List.of("2", "4");

//Supplier을 뽑고
Supplier<Stream<String>> streamSupplier = list::stream;

//get하여 새로운 스트림을 반환 시키면
assertThatNoException().isThrownBy(() -> {
	streamSupplier.get().collect(Collectors.joining());
	streamSupplier.get().count();
});
```


### 결론 
Stream은 종결 연산자 이후에 재 사용이 불가능한 사실을 인지하여 조심히 사용하자 



