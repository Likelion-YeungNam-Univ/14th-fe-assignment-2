# 멋쟁이사자처럼 2회차 과제

## 자바스크립트 언어가 다른 언어와 다른 특징 3가지를 작성해주세요

1. 인터프리터 방식인 python과 AOT컴파일 방식인 C/C++과는 다르게, Just-In-Time 컴파일 방식이다. 이 방식은 코드를 실행하는 시점에 필요하다고 판단되는 부분을 즉석에서 컴파일 하는 방식을 뜻한다.
2. HTML과 CSS와는 다르게 웹페이지의 동작과 기능을 추가하는 언어로서, 사용자와 상호작용 하는 기능을 만들 때 사용하는 언어이다.
3. 동적 타이핑 방식이며, 메모리 할당/해제 방식이 C와 같은 수동이 아닌, GC를 통해 관리된다.

## 변수에 대해 설명하고 let, const, var 차이점을 작성해주세요

const: 중복 선언과 재할당 모두 불가능하다.
ex) 재할당 중복 선언
const e1 = 2.818 const e2 = 2.818
e1 = 3.14 (ERROR) const e2 = 2 (ERROR)

let: 중복 선언은 불가능 하지만 재할당은 가능하다.
ex) 재할당 중복 선언
let a = 20 let b = 20
a = 30 let b = 30 (ERROR)

var: 중복 선언과 재할당이 모두 가능하다. 그렇기에 앞서 선언한 변수더라도 다시 선언과 재할당이 가능하게 된다.
ex) 재할당 중복 선언
var a = 10 var b = 20
a = 20 var b = 30

## ==과, ===의 차이점을 작성해주세요

'=='은 자료형이 다르더라도 내부에서 자료형 변환이 일어난 후 같음을 비교하는 것이고, '==='은 자료형 또한 같은 지 확인하는 연산자이다.
ex) 1 == '1' (True) 1 === '1' (False)

## var 변수 타입을 지양해야하는 이유를 말해주세요

var 변수는 let과는 다르게 중복 선언이 가능하기 때문에 여러 변수가 동일한 스코프에 같은 이름으로 존재한다면 코드를 파악하기 힘들어진다.
또한 var 변수는 블록 스코프를 무시하기에 예기치 않은 버그가 더 잘 발생하기 때문이다.

## function foo() {}와 var foo = function() {} 사이에서 foo 사용의 차이에 대해 작성해주세요

function foo()는 함수 전체가 호이스팅되어 선언 이전에도 호출이 가능하다.
반면 var foo = function()은 변수 선언만 호이스팅되고 값은 undefined로 초기화되기 때문에
함수 할당 이전에 호출하면 undefined를 호출하게 되어 에러가 발생한다.

## 화살표 => 함수 문법에 대한 사용 예시를 작성해주세요. 이 문법은 다른 함수와 어떻게 다른지 작성해주세요

기존 일반 함수는 호출 방식에 따라 this가 변경되지만, 화살표 함수는 자신만의 this를 가지지 않고 상위 스코프의 this를 그대로 사용한다.
ex)
const object = {
name: "woong",
main:function(){
console.log(this);
},
mainArrow:()=>{
console.log(this);
},
};
object.main() // this: object
object.mainArrow() // this: window

## spread 문법에 대해 작성해주세요

spread 문법은 배열이나 객체를 펼쳐서 복사하거나 합칠 때 사용하는 문법이다. 얕은 복사가 수행되며, 배열과 객체 합치기에 매우 편리하다.
ex)
const arr1 = [1,2];
const arr2 = [...arr1, 3, 4];
const obj1 = { a: 1 };
const obj2 = { ...obj1, b: 2 };

# 주제 정리🦁

## 배열과 객체

배열: 데이터를 순서대로 저장하는 자료구조. 인덱스를 통해 접근. 다양한 타입의 데이터를 함께 저장할 수 있음.

객체: 데이터를 딕셔너리 형태로 저장하는 자료구조. key를 통해 value 접근.

배열 -> 객체 변환
ex)
const arr = ['사과', '바나나', '딸기']
const obj = Object.assign({}, arr);
console.log(obj) // {0: '사과', 1: '바나나', 2: '딸기'}

객체 -> 배열 변환
ex)
const obj = { a:1, b:2 };
const entries = Object.entries(obj);
console.log(entries); // [["a", 1], ["b", 2]]

## 콜백 함수

: 다른 함수의 인자로 전달되어, 특정 시점에 호출되는 함수
ex) map
const arr = [1, 2, 3];
const result = arr.map(function(x) {
return x \* 2;
});

ex) setTimeout
setTimeout(function() {
console.log("3초 후 실행");
}, 3000);

## 화살표 함수

익명 함수를 활용하여 함수를 변수에 저장하여 활용하는 방식.
ex)
const add = (a, b) => {
return a + b;
}

함수 본문이 한 줄일 경우 return과 중괄호 생략 가능.
매개변수가 하나인 경우, 소괄호 생략 가능.
상위 this를 그대로 참조함.
