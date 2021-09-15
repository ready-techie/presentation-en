## About Svelte

The Svelte is a new approach front-end framework created by Rich Harris.

It has been released up to version 3.


- Nov 2016, 1.0 Release
- Apr 2018, 2.0 Release
- **Apr 2019, 3.0 Release**

v1, 2 didn't make much of a difference from React and Angular. 

Much has changed since the version 3, and it has become popular.

- ...
    1. Rich Harris 가 제작한 새로운 접근 방식의 Front-end Framework 이다. 

        현재 버전 3까지 Release 되었다. 

        - Nov 2016, 1.0 Release
        - Apr 2018, 2.0 Release
        - **Apr 2019, 3.0 Release**

        → 1, 2버전은 React, Angular 와 큰 차이가 없었고, 3버전 부터 많은 부분이 바뀌었고, 급격히 관심을 받게 되었다. 

## Stats

- [https://2020.stateofjs.com/en-US/technologies/front-end-frameworks/](https://2020.stateofjs.com/en-US/technologies/front-end-frameworks/)

According to the 2020 data, the satisfaction level was high in the order of Svelte, React, and Vue.js.

Svelte is also the most Interesting

You can see that the usage has double compared to 2019

The awareness is still low.

- ...
    1. 통계

        2020년 데이터로 Svelte, React, Vue.js 순서대로 만족도가 높은 것으로 조사가 되었다. 

        - 2019년에 처음 나왔는데도 불구하고 만족도가 가장 높은 것을 보실 수 있습니다.
        - 흥미도 역시 svelte 가 가장 높습니다.
        - 사용량은 2019년에 비해 약 2배 정도 늘어난 것을 보실 수 있습니다.
        - 인지도 (Awareness) 는 아직 낮은 편에 속하네요.

## Features

- [https://svelte.dev/](https://svelte.dev/)

Let's take a look one by one 

### Write less code

You can write less codes ! 

- Compare Svelte, Vue, React Codes

![스크린샷 2021-08-30 오후 3.36.44.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e5d4f7d8-1ae6-4af9-bfa9-a74c3c405968/스크린샷_2021-08-30_오후_3.36.44.png)

- It consists of two input boxes.
- The first is Svelte, the second is Vue, and the third is React.
- The applications of the same feature can be simplified using Svelte.
- The advantages of having less codes are as follows.

    1. Maintain high readability

    2. Reduce development time

    3. Easy refactoring

    4. Easy debugging

    5. Smaller Bundle (SPA Optimization)

    1. SPA disadvantage is that initial loading is expensive.

    1. Even in learning Svelte api, a low running curve.
- ...
    - 특징

    ## Write less code

    - 더 적은 코드를 작성할 수 있다!
    - Svelte , Vue, React 코드 비교
    - 두개의 input 박스로 구성되어있습니다.
    - 첫번째는 Svelte , 두번째는 Vue, 세번째는 React 입니다.
    - 같은 기능의 application 을 Svelte 를 이용하여 이렇게 간결하게 만들 수 있습니다.
    - 코드가 적어질때의 장점은 다음과 같아요.
    1. 높은 가독성 유지
    2. 개발 시간 단축
    3. 쉬운 리팩터링
    4. 쉬운 디버깅
    5. 더 작은 번들(SPA 최적화)
        1. SPA 단점은 최초 로딩에 비용이 많이 든다. 
    6. 스벨트 api 를 배움에 있어서도, 낮은 러닝 커브 

### No virtual DOM

There is no virtual Document Object Model.

![스크린샷 2021-08-30 오후 3.52.28.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6a6a623b-aae1-449b-b3de-7720a39045af/스크린샷_2021-08-30_오후_3.52.28.png)

**No virtual DOM →** No Diffing

**No Overhead**

1. Diffing: When data is changed, comparing the existing virtual dom with the one created based on the changed data.
2. And it will be renewed with the changed dom.
3. The disadvantage of virtual dom is that
    1. Creating a virtual dom based on changed data
    2. Comparison with existing dom and newly created dom
    3. The UI should be updated according to the comparable results.

**But ! The svelte is updated, but does not create or compare virtual dom.**

Indirect time spent for processing, or sufficiently fast performance (performance**) because memory is not used.

- ...

    ## No virtual DOM

    - 가상의 Document Object Model 이 없다 .
    1. No Diffing
        1. Diffing : 데이터가 변경되면, 기존에 만들어 놓았던 가상 돔과 변경된 데이터를 기준으로 만들어진 가상돔을 비교 하는 것 
        2. 그리고 변경된 돔으로 갱신해주게 된다. 
        3. 가상돔의 단점은
            1. 변경된 데이터를 기준으로 한 가상돔의 생성
            2. 기존 돔과 새로 생성된 돔과 비교
            3. 비교된 결과물에 따라 화면을 갱신해야한다. 
        4. 스벨트는 갱신은 발생하지만, 가상돔 생성, 비교 하는 행위를 하지 않는다. 
    2. **No Overhead →** 처리를 위해 들어가는 간접적인 시간이나, 메모리를 사용하지 않기 때문에 
    3. 때문에 **충분히 빠른 성능(퍼포먼스**)를 보여준다.

### Truly reactive (Real reactivity without virtual DOM)

- Reactivity is when changes in application status are automatically applied to DOM.
- It's not about finding the changed location and changing it, but knowing the exact location is the real Reactivity.
- The JS output are creates a result using pure JavaScript for the code we write, which works in a browser.

```jsx
<script>
	let name = 'world';
</script>

<h1>Hello {name}</h1>
								//버튼을 클릭하면 데이터가 갱신된다. 
<button on:click={() => {name = 'deveeni'}}>
	Change! 
</button>
```

- User-written code shows when reactivity occurs.
1. Framework-less VanillaJS
    1. Instead of using the framework at runtime, pure JavaScript works in a browser.
2. Only use `devDependencies`
    1. Svelte acts as a compiler. 
    2. Therefore, it can only installed and use as a devDependencies.
    3. Svelte is a **compiler** that dose not work in a browser (runtime) because svelte converts the application to VanillaJS and only works as a result.
3. Creative Action
    1. Like this codes → name = "" 
    2. It is creative because users create their own reactivity.
- ...

    ## Truly reactive (가상돔을 사용하지 않는 진짜 반응성)

    - 반응성 : 애플리케이션 상태(데이터)의 변화가, DOM 에 자동으로 반영되는 현상을 말한다.
    - 변경된 위치를 찾아 변경하는 것이 아니라, 변경된 위치를 정확하게 아는 진짜 반응형입니다.
    - JS output 우리가 작성한 코드를 순수한 자바스크립트 (VanillaJS) 로 결과물을 만들어서 이 결과물을 브라우저에서 동작시킨다.

    ```jsx
    <script>
    	let name = 'world';
    </script>

    <h1>Hello {name}</h1>
    								//버튼을 클릭하면 데이터가 갱신된다. 
    <button on:click={() => {name = 'deveeni'}}>
    	Change! 
    </button>
    ```

    - 사용자가 작성한  코드로 (on:click) 언제 반응성이 일어나는지 (데이터가 갱신 되는 시점)을 알 수 있다.
    1. Framework-less VanillaJS
        1. 프레임워크를 런타임에서 사용하지 않고, 순수한 자바스크립트가 브라우저에서 동작한다. 
    2. Only use `devDependencies`
        1. Svelte 가 컴파일러 역할을 한다. 
        2. 그렇기 때문에 개발 의존성으로만 설치해서 사용 할 수 있다. 
        3. Svelte 가 작업물(애플리케이션)을 VanillaJS로 변환(컴파일)하고 그 결과만 동작하기 때문에, Svelte 는 브라우저(런타임) 에서 동작하지 않는 컴파일러라고 할 수 있습니다. 
    3. 명시적 설계 (창의적 작업)
        1. name = "" 할당하라는 코드를 작성한것 처럼 
        2. 사용자가 직접 반응성을 만들어 내기 때문에 창의적이라고 할 수 있다. 

## Cons..

- small ecosystem
- CDN not available
- Not supported at IE
- ...

    ## 단점

    - 낮은 성숙도(작은 생태계)
    - CDN 미제공
        - runtime에서 동작하지 않기때문에 cdn 제공하여 브라우저 환경에서 직접 동작시키는 것을 할 수 없다.
    - IE 지원하지 않음
