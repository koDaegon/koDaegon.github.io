---
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
      values:
        layout: single
        categories: Personal
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

### 4. Default Values Using the || Operator
Today, in ES6, there is the default argument feature. To simulate this feature in old browsers, you can use the || (OR operator) by including the default value as a second parameter to be used.
If the first parameter returns false, the second one will be used as a default value. See this example:
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
5. Caching the array.length in the Loop
This tip is very simple and causes a huge impact on performance when processing large arrays during a loop. Basically, almost everybody writes this synchronously to iterate an array:
for(var i = 0; i < array.length; i++) {
    console.log(array[i]);
}
If you work with smaller arrays, it’s fine, but if you process large arrays, this code will recalculate the size of an array in every iteration of this loop and this will cause some delays.
To avoid it, you can cache the array.length in a variable to use it, instead of invoking the array.length every time during the loop:
var length = array.length;
for(var i = 0; i < length; i++) {
    console.log(array[i]);
}
To make it smaller, just write this code:
for(var i = 0, length = array.length; i < length; i++) {
    console.log(array[i]);
}
6. Getting the Last Item in the Array
The Array.prototype.slice(begin, end) has the power to cut arrays when you set the beginning and end arguments. But, if you don’t set the end argument, this function will automatically set the max value for the array.
I think that few people know that this function can accept negative values, and if you set a negative number as the beginning argument, you will get the last elements from the array:
var array = [1,2,3,4,5,6];
console.log(array.slice(-1)); // [6]
console.log(array.slice(-2)); // [5,6]
console.log(array.slice(-3)); // [4,5,6]
7. Truncating Array
This technique can lock the array’s size, this is very useful to delete some elements from the array based on the number of elements you want to set.
For example, if you have an array with 10 elements but you want to get only the first five elements, you can truncate the array, making it smaller by setting the array.length = 5. See this example:
var array = [1,2,3,4,5,6];
console.log(array.length); // 6
array.length = 3;
console.log(array.length); // 3
console.log(array); // [1,2,3]
8. Replace All
The String.replace() function allows you to use string and regex to replace strings; natively, this function only replaces the first occurrence. But you can simulate a replaceAll() function by using the /g at the end of a Regex:
var string = "john john";
console.log(string.replace(/hn/, "ana")); // "joana john"
console.log(string.replace(/hn/g, "ana")); // "joana joana"
9. Converting NodeList to Arrays
If you run the document.querySelectorAll("p") function, it will probably return an array of DOM elements, the NodeList object. But this object doesn’t have all the array’s functions, like: sort(), reduce(), map(), filter().
To enable these and many other native array functions, you need to convert NodeList into Arrays. To run this technique, just use this function: [].slice.call(elements):
var elements = document.querySelectorAll("p"); // NodeList
var arrayElements = [].slice.call(elements); // Now the NodeList is an array
// This is another way of converting NodeList to Arrayvar arrayElements = Array.from(elements);
10. Merging Arrays
If you need to merge two arrays, you can use the Array.concat() function:
var array1 = [1,2,3];
var array2 = [4,5,6];
console.log(array1.concat(array2)); // [1,2,3,4,5,6];
However, this function is not the most suitable to merge large arrays because it will consume a lot of memory by creating a new array.
In this case, you can use Array.push.apply(arr1, arr2), which instead creates a new array. It will merge the second array into the first one, reducing memory usage:
var array1 = [1,2,3];
var array2 = [4,5,6];
console.log(array1.push.apply(array1, array2)); // [1,2,3,4,5,6];
11. Shuffling an Array’s Elements
To shuffle an array’s elements without using an external library like Lodash, just run this magic trick:
var list = [1,2,3];
console.log(list.sort(function() { Math.random() - 0.5 })); // [2,1,3]
Resource : JavaScript Tips