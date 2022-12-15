
# Open JDK

* OpenJDK는 자바 플랫폼, 스탠다드 에디션(Java-SE)의 오픈소스 구현체 
* 라이선스 Oracle GPL v2
* 신규 버전 배포주기 6개월 
* 무료이다 
* 여러 벤더들이 참여하여 개발 진행 
* 커뮤니티 기반 빌드인 AdoptOpenJDK가 가장 대표적 이다. 

## AdoptOpenJDK(https://adoptopenjdk.net/)

2017년에 자바 유저 그룹 멤버, 개발자, 벤더(아마존, 마이크로소프트, 피보탈, 레드햇 등)로 구성된 그룹이 AdoptOpenJDK라는 커뮤니티를 시작하여 가장 유명함 

최근에는 (2021 ~ 8월) 에  프로젝트를  Eclipse Adoptium(https://adoptium.net/)에 이관하였다 

### Openj9 빌드

Adoptium은 OpenJ9 기반 또는 GraalVM 기반 런타임을 릴리즈하지 않는다. AdoptOpenJDK 에서 OpenJ9이 인기가 많았었는데 이는 IBM 에서 직접 제공하는 빌드를 통해 해결 할 수 있다고 한다. 현재 AdoptOpenJDK API에 'adoptopenjdk'의 최신 'Hotspot' 빌드를 요청하면 최신 Temurin 빌드를 제공하고 'adoptopenjdk'의 'openj9' 빌드를 요청하면 IBM 빌드를 제공하고 있다.

## openj9  ? GraalVM

VM의 종류이다.

* openj9 
	*기존의 HotSpot (hs) 방식의 JVM과 단리 클라우드 환경에 최적화 되어 있다고 하며 
	적은 메모리를 사용하여 구현을 진행 중
* GraalVM
	*GraalVM은 Java 코드를 작성하고 실행할 수 있는 도구이다. Oracle에서 만든 JVM(Java Virtual Machine) 및 JDK(Java Development Kit)이고 애플리케이션의 성능과 효율성을 개선하는 목적으로 나온 고성능 런타임이다.
	AOT[[AOT 컴파일러]] Just-In-Time 컴파일러 사용 
	
	
  Just-In-Time 컴파일러? [[JIT 컴파일러 란?]]
	


*TCK가 무엇인가?
TCK란, Technology Compatibility Kit의 약자로서 VM들이 JVM 표준 구현을 준수하였는지 확인하는 절차입니다. (AdoptOpenJDK 인증 받지 못했음)


# Oracle JDK

 Oracle사에서 개발되고 빌드 되고 있는 자바 프로젝트 
 2018년 오라클의 정책 변경에 따라 Oracle JDK 바이너리에 적용되던 BCL 라이선스가 바뀌어 이를 사용하려면 라이선스 구독이 필요하다.

* 유료이다
* Oracle에 의해 지속적으로 관리되고 있다.  (성능, 안정성)


* 참조
	* https://revf.tistory.com/253
	* https://giljae.medium.com/graalvm-%EC%86%8C%EA%B0%9C-84ac547f8df2