---
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
      values:
        layout: single
        categories: Translation
        author_profile: true
        read_time: true
        comments: true
        share: true
        related: true
---

새해가 되어 처음으로 블로그에 글을 써본다 올해 처음으로  [Medium]()을 구독하기 시작했다. 그리고 1년 구독서비스를 결제 했다. 사실 작년부터 종종 올라오는 블로그 포스트들을 눈여겨 봤었는데 나의 관심사에 따라 매일 알림으로 관련 분야의 인기 있는 블로그 포스트들을 스크랩해서 알림이 오기 때문에 나는 JS와 관련된 글들을 광고가 없이 잘 받아 볼 수 있엇따.
새해 계획중 한가지는 하루에 적어도 하나의 글을 읽는게 `2020`목표 인데 9일이 될때 까지는 잘 지키고 있는 편이다. 그런데 내가 글을 읽는 것들도 중요하지만 기억은 언젠간 사라지기 마련이며 어딘가에 기록하여 기억을 더 오래 지속시킬 수 있게 하는 것도 중요하게 생각이 들어 내가 최근 흥미롭게 읽었던 글들중 하나를 골라 읽었던 글의 번역을 올려볼까 한다.

### Origin : [11 extremely useful JavaScript Tips](https://medium.com/better-programming/11-extremely-useful-javascript-tips-4484429a5655)


---


### 1.  !!연산자를 이용하여 불 값으로 변환하기

종종 변수가 존재하는지 또는 유효한 변수인지 확인해보거나 변수가 true값인지 고려해야할 필요가 있는데 이러한 확인과정에서 !! 연산자를 사용할 수 있습니다.


심플한 !!변수는 자동적으로 어떤 종류의 데이터값에서 불값의 타입으로 변환되는데 만약 `0`, `null` , `""` , `undefined` , 또는 `NaN`와 같은 값을 가지고 있다면 오직 `false`만 반환할 것 입니다. 그렇지 않다면 `true`값을 반환합니다.


이를 실제로 이해하기 위해 간단한 예제를 보겠습니다.


``` 
function Account(cash) {
    this.cash = cash;
    this.hasMoney = !!cash;
}

var account = new Account(100.50);
console.log(account.cash); // 100.50
console.log(account.hasMoney); // true

var emptyAccount = new Account(0);
console.log(emptyAccount.cash); // 0
console.log(emptyAccount.hasMoney); // false
```

위와 같은 경우는 `account.cash` 값이 0보다 크기 때문에 `account.hasMoney`는 `true`값이 될 것입니다.





### 2.  +연산자를 이용해서 숫자로 변환하기

이 마법은 환상적이며 매우 간단히 구현 할 수 있지만 숫자로 된 문자열 에서만 동작 합니다. 다른 경우엔 `NaN`을 반환합니다.(숫자가 아닌경우) 예제를 보겠습니다.

```
function toNumber(strNumber) {
    return +strNumber;
}
console.log(toNumber("1234")); // 1234
console.log(toNumber("ACB")); // NaN

//Date 타입에 대해서도 동작합는데 이경우에선 타임스탬프 숫자를 반환합니다.
console.log(+new Date()) // 1461288164385


```

### 3. Short-Circuit Conditionals 

만약 아래와 비슷한 코드에선,

```
if (connected) {
    login();
}
```

위의 코드를 변수와 `&&`연산자를 이용한 함수의 조합을 통해서 단순화 시킬수 있습니다. 예를 들면 위의 코드는 한줄로 축소 될 수 있습니다. 

```
connected && login();
```

객체 안의 속성 값이나 함수가 존재하는지 확인 하고 싶은 경우에도 같은 방법으로 적용가능 합니다. 아래의 비슷한 코드를 보겠습니다.

```
user && user.login();
```

### 4. Default Values Using the || Operator ||연산자를 이용해서 변수값을 디폴트 하기
오늘날의 ES6 문법에선 디폴트 인수기능이 있습니다. 이기능을 오래된 브라우저들에서 실행시키기 위해서는 두번째 매개변수로 사용될 디폴트 값을 포함시키서 `||` 연산자를 사용 할 수 있습니다.
만약 첫번째 매개변수가 `false`를 반환한다면 두번째 매개변수는 디폴트 값가 될 것 입니다.
```

function User(name, age) {
    this.name = name || "Oliver Queen";
    this.age = age || 27;
}


var user1 = new User();
console.log(user1.name); // Oliver Queen
console.log(user1.age); // 27
var user2 = new User("Barry Allen", 25);
console.log(user2.name); // Barry Allen
console.log(user2.age); // 25

```


### 5. Caching the array.length in the Loop `array.length`를 반복문에 캐싱하기

반복문 안에서 규모가 큰 배열을 처리 할 때 성능에 강력한 영향을 미치는 아주 간단한 팁입니다. 
기본적으로, 거의 모두가 동시에 배열을 반복하기 위해  아래 코드를 작성 할 것 입니다.

```
for(var i = 0; i < array.length; i++) {
    console.log(array[i]);
}

```
만약 크기가 작은 배열에서는 문제가 없습니다. 그러나, 크기가 큰 배열 에선 위의 코드는 반복문을 반목 할 때마다 배열의 크기를 다시 계산 할 것입니다. 이는 지연을 발생 시킵니다. 


반목분 안에서 매번 `array.length`를 호출 하는 대신에  `array.length`를 사용할 변수안에 캐싱 하여 이를 피할 수 있습니다. 

```
var length = array.length;
for(var i = 0; i < length; i++) {
    console.log(array[i]);
}
```

  간소화를 위해 아래와 같은 코드를 작성합니다.

```
for(var i = 0, length = array.length; i < length; i++) {
    console.log(array[i]);
}
```

### 6. Getting the Last Item in the Array 배열의 마지막 아이템 가져오기
`Array.prototype.slice(begin, end)`는 시작 과 끝의 인수를 설정 하였다면 배열을 자를 수 있습니다. 그러나 인수를 설정 하지 않았을 경우 위 함수는 자동적으로 배열의 최대값을 설정 할 것 입니다. 


몇몇 사람들은 위의 함수가 마이너스 값도 받을 수 있다고 생각합니다. 만약 마이너스 숫자를 시작 인수로 설정 한다면 배열의 가장 마지막 인수를 배열을 통해 얻을 수 있습니다.

```
var array = [1,2,3,4,5,6];
console.log(array.slice(-1)); // [6]
console.log(array.slice(-2)); // [5,6]
console.log(array.slice(-3)); // [4,5,6]
```
### 7. Truncating Array 배열의 크기 줄이기

이 테크닉은 배열의 크기를 조정 할 수 있습니다, 이는 원하는 숫자 만큼의 배열의 원소를 삭제 하는데 아주 유용합니다.


예를 들면 만약 10개의 원소를 가진 배열이 있는데 5번째 까지의 원소만 필요하다면 `array.length = 5`를 설정하여 배열의 크기를 작게 조정 할 수 있습니다.
```

var array = [1,2,3,4,5,6];
console.log(array.length); // 6
array.length = 3;
console.log(array.length); // 3
console.log(array); // [1,2,3]
```


### 8. Replace All 전체 바꾸기

String.replace() 함수는 문자열과 정규 표현식을 사용하여 문자열들을 대체 가능 합니다. 원래 이 함수는 오직 첫번째 상황만 치환하지만  `regex`의 끝에 `/g`를 사용함으로써 `replaceAll()`함수처럼 보이게 할 수 있습니다.

```
var string = "john john";
console.log(string.replace(/hn/, "ana")); // "joana john"
console.log(string.replace(/hn/g, "ana")); // "joana joana"
```


### 9. Converting NodeList to Arrays NodeList를 배열로 변환하기
만약 `document.querySelectorAll("p")` 를 사용 한다면 DOM elements(`NodeList`객체)를 반환 할 것입니다. 허나 객체는 모든 배열의 함수를 가지지 않습니다. 예를 들면 : `sort()` `reduce()` , `map()` , `filter()`


위와 같은 함수들과 다른 네이티브 배열 함수를 사용하기 위해서는 `NodeList`를 `Arrays`로 변환 해야 합니다. 이 테크닉을 사용하기 위해서는 `[].slice.call(elements)` 함수를 사용하십시오.

```
var elements = document.querySelectorAll("p"); // NodeList
var arrayElements = [].slice.call(elements); // Now the NodeList is an array

// This is another way of converting NodeList to Array

var arrayElements = Array.from(elements);
```


### 10. Merging Arrays 배열 병합하기 

만약 두개의 배열을 합치고 싶다면 `Array.concat()`함수를 사용 할 수 있습니다.

```
var array1 = [1,2,3];
var array2 = [4,5,6];
console.log(array1.concat(array2)); // [1,2,3,4,5,6];
```

그러나, 위 함수는 규모가 큰 배열들을 병합하는데는 알맞지 않습니다. 이는 새로운 배열을 만들어 많은 메모리를 사용 할 것입니다.


이러한 경우엔 새로운 배열을 만드는 대신에`Array.push.apply(arr1, arr2)`를 사용 할 수 있습니다. 이는 두번째 배열을 첫번째 배열에 합칠 것이며 메모리 소모를 줄입니다.


```
var array1 = [1,2,3];
var array2 = [4,5,6];
console.log(array1.push.apply(array1, array2)); // [1,2,3,4,5,6];
```


### 11.  Shuffling an Array’s Elements 배열의 원소 섞기

`Lodash`와 같은 외부 라이브러리 없이 배열의 원소들을 섞기 위해서는 그냥 이 매직트릭을 동작 하세요!


```
var list = [1,2,3];
console.log(list.sort(function() { Math.random() - 0.5 })); // [2,1,3]
```


WRITTEN BY
[Javascript Jeep🚙💨](https://medium.com/@jagathishsaravanan)

TRANSLATED BY
[koDaegon](https://kodaegon.github.io)