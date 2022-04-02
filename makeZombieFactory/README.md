#### 1
모든 솔리디티 코드는 "version pragma"로 시작해야한다. 이를 통해 새로운 컴파일러 코드가 나와도 기존 코드가 깨지지 않도록 예방한다.

#### 2 
솔리디티에서 변수를 다루는법을 배우자! 
상태변수는 컨트랙트 저장소에 영구적으로 저장된다. **즉 이더리움 블록체인에 기록된다는거지!!
데이터베이스 데이터를 쓰는 것과 동일하지!! 허허

```
contract Example {
  // 이 변수는 블록체인에 영구적으로 저장된다
  uint myUnsignedInteger = 100;
}
```

uint 자료형은 부호 없는 정수로, 값이 음수가 아니어야 한다는 의미!

#### 3
솔리디티에서 기본 사칙연산 연산자는 일반 프로그래밍 언어들과 거의 동일하다.

#### 4
보다 복잡한 자료형을 사용하기 구조체를 사용한다!

```
struct Person {
  uint age;
  string name;
}
```

#### 5
배열을 사용할 수 있다.
배열에는 정적 배열과 동적 배열 두 가지가 존재한다.
```
// 또다른 고정 배열으로 5개의 스트링을 담을 수 있다:
string[5] stringArray;
// 동적 배열은 고정된 크기가 없으며 계속 크기가 커질 수 있다:
uint[] dynamicArray;
```
솔리디티는 Public 배열을 위해 getter 메소드를 자동으로 생성한다!
```
Person[] public people;
```
그러면 다른 컨트랙트들은 읽을 수 있게된다!(쓸수는 없다 ㅠㅠ)

#### 6
솔리디티에서 함수의 선언은 다음과 같이 한다!
```
function eatHamburgers(string _name, uint _amount) {

}
```
#### 7
새로운 구조체 생성 방법
```
Person[] public people;
// 새로운 사람을 생성한다:
Person satoshi = Person(172, "Satoshi");
// 이 사람을 배열에 추가한다:
people.push(satoshi);
