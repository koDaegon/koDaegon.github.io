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

### Origin : https://medium.com/better-programming/11-extremely-useful-javascript-tips-4484429a5655

https://medium.com/better-programming/11-extremely-useful-javascript-tips-4484429a5655

  1. Converting to Boolean Using the !! Operator
  1. !! 연산자를 이용하여 Boolean 타입 변환
  
Sometimes, we need to check if a variable exists or if it has a valid value, to consider them as a true value. For this kind of validation, you can use the !! (double-negation operator).
A simple !!variable, which will automatically convert any kind of data to a boolean and this variable will return false only if it has some of these values: 0, null, "", undefined, or NaN, otherwise, it will return true.
To understand it in practice, take a look this simple example:


Working in progress..!
