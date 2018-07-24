# Annotation
어노테이션은 메타데이터(metadata)라고 볼수 있다. 메타데이터란 애플리케이션이 처리해야 할 데이터가 아니라, 컴파일 과정과 실행 과정에서 코드를 어떻게 컴파일하고 처리할 것인지를 알려주는 정보이다.

## 용도
1. 컴파일러에게 코드 문법 에러를 체크하도록 정보를 제공
2. 소프트웨어 개발 툴이 빌드나 배치 시 코드를 자동으로 생성할 수 있도록 정보를 제공
3. 실행 시(런타임 시) 특정 기능을 실행하도록 정보를 제공

코드 문법 에러 체크의 대표적인 예는 @Override 어노테이션이다. @Override는 메소드 선언 시 사용하는데, 메소드가 오버라이드 된 것임을 컴파일러에게 알려주어 컴파일러가 이를 검사하도록 해준다. 정확히 오버라이드가 되어 있지 않았다면 컴파일러는 에러를 발생시킨다.

어노테이션은 빌드 시 자동으로 XML 설정 파일을 생성하거나 배포를 위해 JAR 압축 파일을 생성하는데에도 사용된다. 또한 실행 시 클래스의 역할을 정의하기도 한다.

## 어노테이션 타입 정의와 적용
어노테이션 타입을 정의하는 방법은 인터페이스 정의와 유사하다.

~~~java
public @interface AnnotationName {
}
~~~

이렇게 정의한 어노테이션은 다음과 같이 사용한다.

~~~java
@AnnotationName
~~~

어노테이션은 **엘리먼트(element)** 를 멤버로 가질 수 있다. 각 엘리먼트는 ***타입*** 과 ***이름*** 으로 구성되며, 디폴트 값을 가질 수 있다.

~~~Java
public @interface AnnotationName {
  type elementName() [default value]; //엘리먼트 선성
  ...
}
~~~

엘리먼트 타입으로 int나 double과 같은 기본 데이터 타입이나 String, 열거 타입, Class 타입, 그리고 이들의 배열 타입을 사용할 수 있다.

엘리먼트의 이름 뒤에는 메소드를 작성하는 것처럼 ()를 붙여야 한다.

~~~Java
public @interface AnnotationName {
  String elementName1();
  int elementName2() default 5;
}
~~~

이렇게 정의한 어노테이션을 코드에서 적용할 때에는 다음과 같이 기술한다.

~~~java
@Annotation(elementName1="값", elementName2=3);
or
@Annotation(elementName1="값")
~~~

디폴트 값이 없을 때는 반드시 값을 기술해줘야 한다.

또한 어노테이션은 기본 엘리먼트인 value를 가질 수 있다. Value 엘리먼트를 가진 어노테이션을 코드에서 적용할 때는 다음처럼 값만 기술할 수 있다.

~~~Java
public @interface AnnotationName {
  String value();
  int elementName() default 5;
}

@AnnotationName("값");
~~~

하지만 만약 value 엘리먼트와 다른 엘리먼트의 값을 동시에 주고 싶다면 엘리먼트 이름을 기술해 줘야 한다.

~~~Java
@AnnotationName(value="값", elementName=3);
~~~

## 어노테이션 적용 대상
