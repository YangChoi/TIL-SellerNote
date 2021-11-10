### forEach와 await

```
async function processArray(array) {
  array.forEach(async (item) => {
    await func(item);
  })
}
```

forEach function 인자로 실행할 익명함수에 async 키워드 추가시
해당 function은 비동기 처리로 await 실행

하지만 forEach는 해당 loop가 종료되길 기다리지 않음
loop 돌며 function 내의 내용을 처리하기 때문에
관련 array를 병렬로 순차실행하는 것은 다르게 처리해줘야함

##### 결론, forEach 안에 await 쓰지마라!
