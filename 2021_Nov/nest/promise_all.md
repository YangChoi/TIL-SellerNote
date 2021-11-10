### Promise.all

[Promise.all](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise/all) 로 비동기 처리를 병렬로 실행하도록 만들 수 있음

각 비동기 처리를 위한 Promise를 반환하는 function을 map 메서드로 묶어
Promise 배열을 반환하고 이를 Promise.all 을 통해서 한 번에 처리하도록 만듦

```
async function processArray(array) {
  // map array to promises
  const promises = array.map(delayed);

  //wait unitl all promises are resolved
  await Promise.all(promises);
  console.log('done');
}
```

위와 같은 비동기 처리방법은 각 비동기 처리의 delay 시점에 따라 순서가 바뀔 수 있음

---

Promise 객체들을 배열 형태로 받아 resolve된 값들의 배열로 만들어줌
하나라도 reject이 발생시 바로 다른 Promise의 resolve 여부와 상관없이 반환

```
const exAllPromise = <T>(promises: Promise<T>[]) => {
  Promise.all(promises);
}

// 배열로 Promise를 넣어서 돌리면 결과값을 배열로 반환
const output = exAllPromise([
  Promise.resolve(1),
  Promise.resolve(2),
  Promise.resolve(3),
  Promise.resolve(4),
]).then((res) => console.log(res));
// [1, 2, 3, 4]

// 하나라도 reject되면 실패
const output = exAllPromise([
  Promise.resolve(1),
  Promise.reject(new Error('err1')),
  Promise.reject(new Error('err2')),
]).then((res) => console.log(res))
  .catch((err) => console.log(err));
```

#### 여러개의 비동기 처리를 병렬적으로 처리할 떄 사용하자!
