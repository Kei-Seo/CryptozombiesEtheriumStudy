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
```

#### 8

솔리디티에서 기본적으로 함수는 public으로 실행된다네,,
즉, 누구나 혹은 다른컨트랙트가 public 함수를 호출할 수 있다는 소리지!
이건 바람직하지 않다네,,,공격에 취약해지니까 private로 선언할 필요가 있어!

```
uint[] numbers;

function _addToArray(uint _number) private {
  numbers.push(_number);
}
```
private 함수는 함수명 앞에 _를 붙이는게 관습

#### 9

반환값을 받으려면 아래와 같이 선언해야한다!

```
string greeting = "What's up dog";

function sayHello() public returns (string) {
  return greeting;
}
```

위에서 살펴 본 함수 sayHello()는 솔리디티에서 상태를 변화시키지 않는다네. 즉, 어떤 값을 변경하거나 무언가를 쓰지 않지.
이 경우에는 함수를 view 함수로 선언하지!

```
function sayHello() public view returns (string) {
```

솔리디티는 pure 함수도 가지고 있는데, 이는 함수가 앱에서 어떤 데이터도 접근하지 않는 것을 의미하지
```
function _multiply(uint a, uint b) private pure returns (uint) {
  return a * b;
}
```
이 함수는 앱에서 읽는 것도 하지 않고, 다만 반환값이 함수에 전달된 인자값에 따라서 달라지지. 그러니 이 경우에 함수를 pure로 선언하지




