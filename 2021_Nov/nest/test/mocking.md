### mocking

[참고](https://bluehorn07.github.io/2021/01/13/nestjs-testing.html#mockrepository)

#### mocking?

- 단위테스트 작성시 해당 코드가 의존하는 부분을 가짜(mock)로 대체하는 기법
- 테스트하려는 코드가 의존하는 부분을 직접 생성하기 부담스러울 때 사용

#### jest.fn()

Jest는 가짜 함수를 생성할 수 있도록 jest.fn() 함수 제공

```
Const mockFn = jest.fn();
```

해당 mock function은 일반 js 함수와 동일한 방식으로 인자를 넘겨 호출할 수 있음

```
mockFn();
mockFn(1);
mockFn(‘a’);
```

위 함수들의 return 값은 전부 undefined

> 어떤 값을 return 해야할지 아직 알려주지 않았기 때문

```
mockFn.mockReturnValue(‘I am a mock’);
```

mockReturnValue로 리턴값을 지정해줄 수 있음

비동기 함수를 만들기 위해서는 비슷한 방식으로
mockResuolvedValue(Promise.resolve()) 로 지정할 수 있음

mockImplementation(구현코드) 함수 이용하면 해당 함수를 통쨰로 재구현 가능

```
mockFn.mockImplementation((name) => `I am ${name}`);
```

가짜함수는 자신이 어떻게 호출되었는지 모두 기억함

```
mock(‘a’);

expect(mockFn).toBeCalledWith(‘a’);
```

#### jest.spyOn()

테스트 작성시 어떤 객체에 속한 함수 구현을 가짜로 대체하지 않고
해당 함수의 호출여부와 어떻게 호출되었는지만을 알아내야할 때 사용

```
jest.spyOn(object, methodName);
```

```
Const calculator = {
	add: (a, b) => a + b;
};

Const spyFn = jest.spyOn(calculator, ‘add’);
Const result = calculator.add(2, 3);

expect(spyFn).toBeCalledTimes(1);
expect(spyFn).toBeCalledWith(2,3);
expect(result).toBe(5);

```

Jest.spyOn() 함수를 통해 calculator 객체의 add라는 함수에 스파이를 붙임
따라서 add 함수 호출 후에 호출 횟수와 어떤 인자가 넘어갔는지 검증 가능
하지만 가짜 함수로 대체한 것이 아니기 때문에 결과값은 원래 구현대로 2, 3의 합인 5

#### mocking이 필요한 시점을 잘 보자

가짜로 데이터를 만들어 써야하는 부분같이
