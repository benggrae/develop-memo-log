
GraalVM의 가장 큰 핵심은 AOT 컴파일러이다. 20년이 지난 후 Java가 **어셈블리** 코드로 컴파일 할 수 있게 되었다. 더 중요한 점은 네이티브 코드가 필요한 상황이 존재한다는 것이고 이는 AWS Lambda로 표현되었다.

Lambda의 흥미로운 점은 사용량에 따라 비용을 지불한다는 것이다. 코드가 실행되는 경우에만 비용을 지불한다는 의미다. 만약 이를 VM기반으로 구현한다고 가정하면 사용하지 않을 때 VM을 반복해서 종료해야 할 것이다. 그리고 요청이 왔을때 구동을 해야 할 것이다. 이 경우 대략 3초의 시간이 필요하다.

이런 문제를 AOT 컴파일러가 해결 할 수 있다. 일반적으로 Java는 수천 개의 클래스를 로드해야 하기 때문에 느리게 시작한다. 그러나 간단한 CRUD 애플리케이션은 로드된 클래스의 극히 일부만 사용한다. GET 요청에 응답하기 위해 Spring Boot의 모든 기능이 필요하진 않다.

AOT 컴파일러는 코드를 최적화하고 컴파일 후 네이티브 코드로 제공된다. Quarkus, Helidon과 같은 클라우드 네이티브 프레임워크를 이용하면 0.005초에 응답하는 Lambda 함수를 만들 수 있다.