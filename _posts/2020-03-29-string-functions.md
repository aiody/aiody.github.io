---
title: "[공부 기록] JavaScript - String functions"
date: 2020-03-29 20:30:00
categories: JavaScript
---
JavaScript에서 String을 쓰면서 익숙해지지 않은 함수들을 모아서 정리해보았다.

## 1. toLowerCase
toLowerCase는 문자열에 있는 모든 대문자를 소문자로 바꿔주는 함수이다. 기존의 문자열에는 영향을 미치지 않는다.

```js
const sentence = 'The quick brown fox jumps over the lazy dog.';

console.log(sentence.toLowerCase());
// expected output: "the quick brown fox jumps over the lazy dog."
```

출처  
[mdn String.prototype.toLowerCase()]  

[mdn String.prototype.toLowerCase()]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase
