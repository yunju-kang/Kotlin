# Class 정리

## Class란?

- 값과 그 값을 사용하는 기능들을 묶어놓은 것
- 속성(고유의 특징값)과 함수(기능의 구현)으로 이루어짐
- 인스턴스(클래스를 이용해 만드는 서로 다른 속성의 객체)를 만드는 틀

```
fun main(){

    var a = Person("박보영", 1990) // 인스턴스 a
    var b = Person("전정국", 1997) // 인스턴스 b
    var c = Person("장원영", 2004) // 인스턴스 c

    a.impormation() // a에 대해 함수 실행
    b.impormation() // b에 대해 함수 실행
    c.impormation() // c에 대해 함수 실행

}

class Person (var name: String, val birthDay: Int){ // 클래스 Person 
    fun impormation(){ // 함수 선언
        println("${name}은 ${birthDay}년생이다.") //println하기
    }
}
```

```
박보영은 1990년생이다.
전정국은 1997년생이다.
장원영은 2004년생이다.

Process finished with exit code 0
```





## 생성자

- 새로운 인스턴스를 만들기 위해 호출하는 특수한 함수
- 인스턴스의 속성을 초기화, 인스턴스 생성시 구문을 수행

- 기본 생성자 : 클래스를 만들 때 기본으로 선언

```
fun main(){
	
	//변수 생성
    var a = Person("박보영", 1990)
    var b = Person("전정국", 1997)
    var c = Person("장원영", 2004)

}

class Person (var name: String, val birthDay: Int){
    init { println("${this.birthDay}년생 ${this.name}님이 생성되었습니다.")}
    //init은 생성자를 통해 인스턴스가 만들어질 때 호출되는 함수
    //this는 인스턴스 자신의 속성이나 함수를 호출하기 위해 클래스 내부에서 사용
}
```

```
1990년생 박보영님이 생성되었습니다.
1997년생 전정국님이 생성되었습니다.
2004년생 장원영님이 생성되었습니다.

Process finished with exit code 0
```

- 보조 생성자 :  필요에 따라 추가적으로 선언

  - 인스턴스 생성시 편의를 제공하거나 추가적인 구문을 수행하는 기능 제공

  - 보조 생성자는 반드시 기본 생성자를 통해 속성을 초기화 해줘야 함.

  - constructor(넘겨받을 패러미터) : this(넘겨받을 패러미터, 초기화 할 패러미터)

```
fun main(){

    var a = Person("박보영", 1990)
    var b = Person("전정국", 1997)
    var c = Person("장원영", 2004)

	//보조 생성자용 변수
    var d = Person("이루다")
    var e = Person("차은우")
    var f = Person("류수정")
}

class Person (var name: String, val birthDay: Int){
    
    init { println("${this.birthDay}년생 ${this.name}님이 생성되었습니다.") }
    
    //년도를 1997년으로 초기화
    constructor(name: String) : this(name,1997) {
        println("보조 생성자가 사용되었습니다.")
    }    
}
```

```
1990년생 박보영님이 생성되었습니다.
1997년생 전정국님이 생성되었습니다.
2004년생 장원영님이 생성되었습니다.
1997년생 이루다님이 생성되었습니다.
보조 생성자가 사용되었습니다.
1997년생 차은우님이 생성되었습니다.
보조 생성자가 사용되었습니다.
1997년생 류수정님이 생성되었습니다.
보조 생성자가 사용되었습니다.

Process finished with exit code 0
```





## 상속

- 상속이 이루어지는 경우
  - 이미 존재하는 클래스를 확장하여 새로운 속성이나 함수를 추가한 클래스를 만들 때
  - 이미 존재하는 여러 개의 클래스의 공통점을 뽑을 떄

- 수퍼/서브 클래스
  - 수퍼 클래스 : 속성과 함수를 물려주는 쪽
  - 서브 클래스 : 속성과 함수를 물려받는 쪽

- 상속의 규칙
  - 서브 클래스는 수퍼 클래스에 존재하는 속성과 같은 이름의 속성을 가질 수 없음
  - 서브 클래스가 생성될 땐 수퍼 클래스의 생성자까지 호출되야 함