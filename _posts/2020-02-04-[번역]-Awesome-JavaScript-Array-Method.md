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
# Awesome JavaScript array methods


origin : https://jilles.me/awesome-javascript-array-methods/](https://jilles.me/awesome-javascript-array-methods/)


만약 자바스크립트를 프로그래밍 한다면, 아마도 배열을 많이 사용할 것 입니다. 이 포스트 에서는 몇가지 가장 즐겨쓰는 배열 메소드를 소개하고자 합니다. 모든 예제들은 아래의 배열을 사용 하게 될 것입니다.


```js
var users = [
    {
        firstName: 'Jilles',
        lastName: 'Soeters',
    	gender: 'M'
    },
    {
        firstName: 'Justin',
        lastName: 'Bieber',
        gender: 'M'
    },
    {
        firstName: 'Miley',
        lastName: 'Cyrus',
        gender: 'F'
    }
];
```

## #1 array.forEach(fn, index)

이는 자바스크립트에서 가장 잘 알려진 배열 메소드 입니다. 간단한 `for`문 보다는 몇 가지 이점이 있습니다.

`arr.forEach()`는 함수를 첫번째 매개변수로 가지며 현재 인덱스 값을 두번째 매개변수로 가집니다. 반면에 `for`문은 만들지 못하는 새로운 스코프 또한 만듭니다. 

```js
users.forEach(function (user, i) {
    var fullName = user.firstName + ' ' + user.lastName;
    console.log('Hello ' + fullName);
});
```

로그상에서 이름을 출력 할 것 입니다. 끝입니다! 그런데, 만약 `for`반복문을 사용하면 반복문 밖에서 접근이 가능한 2가지 변수를 생성합니다.
```js
for (var i = 0; i < users.length; i++) {
    var fullName = users[i].firstName + ' ' + users[i].lastName;
    console.log('Hello ' + fullName);
}
// fullName is now Miley Cyrus 
// i is now 3
```
제 느낌상 forEach는 더욱 표현적인데 개인적인 생각으론 user가 users[i] 보다 보기 좋습니다.


## #2 array.map(fn)

`Array.map`은 유용한 함수 입니다. 배열을 통해 반복을 하는데 (forEach와 마찬가지로) 반환된 아이템을 가지고 새로운 배열을 생성합니다. 
만약 id를 유저리스트에 추가 하고자 한다면 간단히 `map`을 사용하여 해결 할 수 있습니다.

```js
var usersDb = users.map(function (user, index) {
    user.id = index + 1;
    return user;
});
console.table(usersDb);
```
출력결과는 아래와 같습니다.
![image](https://user-images.githubusercontent.com/47220755/73755867-09a45b00-47aa-11ea-9225-05d85964feae.png)

## #3 array.filter(fn)
`Array.filter`은 `map`과 약간 비슷합니다. 새로운 배열을 생성하지만 오직 함수의 반환 값이 `true`인 아이템만 포함합니다.

```js
var guys = users.filter(function (user) {
    return user.gender === 'M';
});
console.table(guys);
```

![image](https://user-images.githubusercontent.com/47220755/73755927-22147580-47aa-11ea-94af-738c11f73f1a.png)


최근에는 간단히 한줄로 배열에서 숫자가 아닌 문자열을 제거하는데 사용하였습니다. `[1, 2, 3, 'banana', 4, {}].filter(Number)`는  `[1, 2, 3, 4]`반환합니다.

## #4 array.reduce(fn, startingValue)

많은사람들은 `reduce`가 복잡하고 어렵다 생각하는데  실제로는 굉장하고 쉬운 메소드라는 것을 알기 전 까지는 저도 마찬가지라고 생각 했었습니다.

배열을 한개의 변수로(숫자가 될 수도 있고 객체 심지어 문자열이 될 수도 있습니다.) "reduce" 하고 싶을 때 `reduce`를 사용하길 원 할 것입니다.

첫번째 인수는 4가지의 인수를 가진 함수인데, 마지막 2개는 선택사항 입니다. 
  - previousValue - 다음 반복에서의 이전 변수, 첫번째에서는 시작 변수가 됩니다.
  - currentValue - 반복하고 있는 배열의 현재 항목
  - index -  현재 아이템의 인덱스
  - originalArray - `.reduce`를 실행중인 배열
  
함수에서 반환되는 것은 `previousValue`가 될 것입니다.

이를 바탕으로 배열로 부터 손님 리스트 문자열을 만들 수 있습니다.

```js
var namesList = users.reduce(function (previous, current, index, originalArray) {
    var end = index + 1 === originalArray.length ? '.' : ', ';
    return previous + current.firstName + end;
}, '');
console.log(namesList); // Jilles, Justin, Miley.
```

## #5 array.every(fn)

마지막을 아주 흔하진 않지만 유용합니다. `filter`와 비슷하지만 `boolean`을 배열에 반환합니다.

```js
function isMillionaire (person) {
    return ['Justin Bieber', 'Miley Cyrus'].indexOf(person.firstName + ' ' + person.lastName);
}

if (users.every(isMillionaire)) {
    console.log('They are all rich!');
} else {
    console.log('Someone in our group is not rich...');
}
```

보너스로 `Array.some`은 `every`와 거의 비슷하지만 전부 참이 아니라 한가지 조건만 참이여도 `true`를 반환합니다.

끝입니다.
