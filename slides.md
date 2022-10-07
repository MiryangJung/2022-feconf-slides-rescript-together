---
theme: geist
title: ReScript 같이 해요
titleTemplate: '%s - Miryang'
highlighter: prism
lineNumbers: true
aspectRatio: 4/3
fonts:
  sans: 'Pretendard'
  mono: 'Elice Digital Coding'
download: false
favicon: 'https://rescript-lang.org/static/nav-logo@2x.png'
---

<h1 class="bg-clip-text text-transparent bg-gradient-to-r from-rose-300 to-red-600">
    ReScript 같이 해요
</h1>

<div class="absolute bottom-10">
  <span class="font-500">
    FEConf 2022
  </span>
</div>

---

# 발표자 소개

<div class="flex mt-10">
  <div class="flex flex-col mr-200px">
    <img class="rounded-full w-200px" src="https://avatars.githubusercontent.com/u/48237511?v=4" />
    <div class="flex items-center mt-10">
      <carbon-logo-github />
      <a class="ml-1" href="https://github.com/MiryangJung" target="_blank">MiryangJung</a>
    </div>
    <div class="flex items-center mt-3">
      <carbon-logo-linkedin />
      <a class="ml-1" href="https://www.linkedin.com/in/miryangjung" target="_blank">정미량 (Miryang Jung)</a>
    </div>
        <div class="flex items-center mt-3">
      <carbon-logo-twitter />
      <a class="ml-1" href="https://twitter.com/MiryangJung" target="_blank">@MiryangJung</a>
    </div>
  </div>
  <ul class="font-semibold">
    <li class="my-3">그린랩스 프론트엔드 엔지니어</li>
    <li class="my-3">여행을 좋아합니다.</li>
    <li class="my-3">지방 거주 재택러.</li>
    <li class="my-3">함수형 프로그래밍 입문자.</li>
    <li class="my-3">개발 블로거. 
      <a href="https://miryang.dev" target="_blank">miryang.dev</a>
      <span class="text-neutral-500 text-sm"> (게스트북 남겨주세요 🫶🏻)</span>
    </li>
  </ul>
</div>

---

# 목차

- 가볍게 알아보기
- 작게 좋았던 점
- 크게 좋았던 점
- 아직도 망설인다면
- 아쉬웠던 점

---
layout: image-right
image: '/images/cookie.png'
---

# 예상 청자

## 내가 만든 발표, 같이하기 위해 구웠지

- 프론트엔드 비기너이신 분
- 새로운 언어를 가볍게 알아보고 싶으신 분
- 함수형 프로그래밍 언어에 관심 있으신 분
- 강력한 타입 언어를 사용해 보고 싶으신 분
- ReScript 도입을 망설이고 있으셨던 분

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tl from-orange-400 to-red-500">
      가볍게 알아보기
  </h1>
</div>
---

# ReScript란?

<div class="flex items-center my-10">
  <img class="mr-10" src="/images/rescript.png" alt="rescript 로고" />
  <h2>읽을 수 있는 JavaScript로 컴파일되는 강력한 타입 언어</h2>
</div>

<div v-click>

- JavaScript 개발자에게 친숙한 구문을 제공
- 모든 JavaScript 라이브러리를 ReScript와 함께 사용 가능

</div>

---

# Hello World!

<video autoplay class="m-auto max-h-120">
  <source src="/images/example.mp4" type="video/mp4">
</video>

---

# ReScript 첫인상

프로그래밍 언어 문법은 금방 익힌다는 자신감 Down

<img class="m-auto max-h-100" src="/images/aoc.png" alt="그린랩스 웹개발팀 스타터킷 깃허브" />

---

# 달랐던 것들

<br />

| 달랐던 점                              | 설명                                                |
| -------------------------------------- | --------------------------------------------------- |
| 😅 let만 있다.                         | const와 비슷한 불변 변수 선언                       |
| 😂 화살표를 사용한다.                  | <KBD>-></KBD> 파이프 연산자, a(b)를 <KBD>b->a</KBD> |
| 😫 return이 없다.                      | 마지막 라인은 암묵적 반환                           |
| 😰 import & export가 없다.             | 모든 모듈은 내보내진다                              |
| 🤯 타입 어노테이션 없이도 타입이 있다. | 타입 추론 시스템                                    |

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tl from-orange-400 to-red-500">
      작게 좋았던 점
  </h1>
</div>

---

# 빌트인 포매터

작은 따옴표 vs 큰 따옴표 / 탭 사이즈 2 vs 4 / 세미콜론 붙이기 vs 말기

### 논쟁할 필요 없다

---

# 좌에서 우로, 위에서 아래로 읽기

```res {1|3-8}
validateAge(getAge(parseData(person)))

person -> parseData -> getAge -> validateAge

person
-> parseData
-> getAge
-> validateAge
```

<v-after>

**파이프 연산자** `->` 책 읽듯이 한 방향으로 읽기

</v-after>

---

# export & import 신경 안쓰기

```ts
export { default as Button } from "./Button";

export { default as Card } from "./Card";

export { default as Modal } from "./Modal";

export { default as Toast } from "./Toast";

export { default as Layout } from "./Layout";

export { default as Footer } from "./Footer";

export { default as Header } from "./Header";

export { default as Container } from "./Container";

export { default as Toc } from "./Toc";

export { default as Title } from "./Title";
```

---

# export & import 신경 안쓰기

## 모든 .res 파일은 모듈

- 모든 모듈은 내보내진다.
- 인터페이스 파일을 사용하면 내보내고 싶은 모듈만 지정할 수도 있다.

```res
// TestComponent.res
module Button = {
  @react.component
  let make = () =>
    <button> {`click`->React.string} </button>
}
```

```js
// Generated by ReScript, TestComponent.js
function Playground$Button(Props) {
  return React.createElement("button", undefined, "click");
}
var Button = { make: Playground$Button };

exports.Button = Button;
```

---

# export & import 신경 안쓰기

```ts
import Container from '../components/Container';

import Button from '../components/Button';

import Button form '../어디더라?';
```

---

# export & import 신경 안쓰기

## 자동으로 프로젝트 안에서 모듈을 찾는다.

import할 파일의 위치를 몰라도, import 한 파일의 위치가 바뀌어도

코드를 변경하지 않아도 된다.

```res
// TestComponent.res

module Button = {
  @react.component
  let make = () =>
    <button> {`click`->React.string} </button>
}
```

```res
// TestPage.res

<TestComponent.Button />
```

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tl from-orange-400 to-red-500">
      크게 좋았던 점
  </h1>
</div>

---

# 타입 추론

### 타입 어노테이션 없이 모든 표현식의 타입을 힌들리-밀너 타입 추론으로 확인

<br />

<div grid="~ cols-2 gap-2" m="-t-2">

```res
let add1 = (a, b) => a + b

let add2 = (a, b) => a ++ b

let add2 = (a, b) => a +. b
```

```plain
(int, int) => int

(string, string) => string

(float, float) => float
```

</div>

---

# 타입 추론

**값의 형태가 맞는 레코드 타입 선언을 찾는다.** data는 person 타입으로 추론된다.

<v-click>

## 타입 검사를 통과한다면 런타임에 잘못 처리되는 값이 없음이 보장된다.

</v-click>

<img class="rounded-xl mt-5" src="/images/record.png" alt="타입 추론" />

---

# Variant

## 합타입

Red 또는 Blue 또는 Yellow 표현한다.

```res
type color = Red | Blue | Yellow

let myColor = Red
```

<br />

<v-click>

배리언트 생성자는 추가 값을 가질 수 있다.

```res {1|3}
type result = Pending | Success | Fail

type result = Pending | Success({data: string}) | Fail
```

</v-click>

---

# 패턴 매칭

## 데이터 형태에 따른 switch 구문

구조 분해를 하고, 각각 분해된 결과의 오른 편에 작성된 코드가 실행된다.

```res
type sns = Facebook(string) | Twitter(string) | None

let name = switch data {
  | Facebook(name) => name
  | Twitter(name) => name
  | None => ""
}
```

---

# 패턴 매칭

누락 된 패턴이 있는지 컴파일 시점에 검사한다.

<img class="rounded-xl mt-5" src="/images/pattern.png" alt="패턴 매칭" />

---

# 패턴 매칭 & 배리언트

<br />

```jsx {1-8|9-11}
<button onClick={() => router.push('/')}>
  Home으로
</button>

<button onClick={() => router.push('/post')}>
  Post로
</button>

<button onClick={() => router.push('/post?id=123')}>
  id와 함께 Post로
</button>
```

---

# 패턴 매칭 & 배리언트

```res {1|3-8,10,14|all}
type page = Home | Post

let toString = page => {
  switch page {
    | Home => "/"
    | Post => "/post"
  }
}

<button onClick={_=> router->Next.Router.push(Route.toString(Home))}>
  {`Home으로`->React.string}
</button>

<button onClick={_=> router->Next.Router.push(Route.toString(Post))}>
  {`Post로`->React.string}
</button>
```

---

# 패턴 매칭 & 배리언트

```res {1,6|15-16|10-13}
type page = Home | Post({id: string})

let toString = page => {
  switch page {
    | Home => "/"
    | Post({id}) => {...}
  }
}
...
<button onClick={_=> 
    router->Next.Router.push(Route.toString(Post{id: 123}))}>
  {`id와 함께 Post로`->React.string}
</button>

// 컴파일 에러 발생
<button onClick={_=> router->Next.Router.push(Route.toString(Post))}>
  {`Post로`->React.string}
</button>
```

---

# Null

```plain
Uncaught TypeError: Cannot read properties of null (reading 'value')
```

<div class="section">
  <span class="text-center italic text-3xl font-serif">
  I call it my billion-dollar mistake.<br />
  It was the invention of the null reference in 1965<br />
  - Tony Hoare -
  </span>
</div>

---

# option

## 타입으로 존재하지 않는 값을 표현한다.

- ReScript에 null 또는 undefined에 대한 개념이 없습니다.
- option 타입은 배리언트입니다.

<br />

```res
type option<'a> = None | Some('a)

let 계세요? = 없음 | 사람(정미량)
```

---

# 예시

## URL 생성하는 API 요청 후 받은 응답을 보여주기

<br />

<div class="flex items-center mt-5">
  <button class="text-3xl bg-gray-300 p-5 rounded-xl font-light text-black">[URL 생성] 요청</button>
  <span class="text-3xl ml-5 font-semibold">요청 중...</span>
</div>

<div class="flex items-center mt-5">
  <button class="text-3xl bg-green-300 p-5 rounded-xl font-light text-black">[URL 생성] 완료</button>
  <span class="text-3xl ml-5 font-semibold">miryang.dev</span>
</div>

<div class="flex items-center mt-5">
  <button class="text-3xl bg-rose-300 p-5 rounded-xl font-light text-black">[URL 생성] 실패</button>
  <span class="text-3xl ml-5 font-semibold">요청 실패</span>
</div>

---

# 예시

```res {1|5|7-13|9-11|16|18-21|15-24} {maxHeight: 100}
type result_t = Pending | Success(string) | Fail

@react.component
let default = () => {
  let (result, setResult) = React.useState(_ => Pending)

  let handleClick = e => {
    e->ReactEvent.Synthetic.preventDefault
    let response {
      | Some(res) => setResult(_ => Success(res))
      | None => setResult(_ => Fail)
    }
  }

  <>
  <button onClick={handleClick}> {`URL 생성` -> React.string} </button>
  {
    switch result {
      | Pending => {`요청 중...` -> React.string}
      | Fail => {`요청 실패` -> React.string}
      | Success(url) => {url -> React.string}
    }
  }
  </>
}
```

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tl from-yellow-300 to-rose-500">
      아직도 망설인다면
  </h1>
</div>

---

# 점진적 채택

<div class="section flex-col">
  <span class="text-center italic text-3xl">
  ReScript를 도입하고 싶은데 <br />
  프로젝트를 폭파하고 새로 시작하기에 <br />
  리스크가 너무 큽니다.
  </span>

  <v-click>
  <div class="text-160px italic absolute top-30 text-rose-500">x</div>
    <span class="text-center font-bold text-3xl mt-20">
    ReScript를 부분적으로 적용하면서 <br />
    원활한 통합이 가능
    </span>
  </v-click>

  <div class="h-150px" />
</div>

---

# 점진적 채택

raw JavaScript 코드를 작성할 수 있다.

```res
let add = %raw(`
  function(a, b) {
    console.log("hello from raw JavaScript!");
    return a + b
  }
`)

Js.log(add(1, 2))
```

- 타입 어노테이션이 없으면 추론이 된다.
- 타입 어노테이션을 줘서 타입 안전하게 할 수도 있다.

---

# genType

[ts-belt](https://github.com/mobily/ts-belt)

```res
// ts-belt/src/Option/Option.res
%comment("Returns `Some(value)` if the provided value is not falsy, otherwise, returns `None`.")
@gentype
let fromFalsy = value => value ? Some(value) : None
```

<div class="text-center text-3xl">↓</div>

```ts
// ts-belt/src/Option/Option.ts
export declare type ExtractValue<T> = Exclude<T, null | undefined>
export declare type Option<A> = A | null | undefined
export declare const Some: <A>(value: NonNullable<A>) => Option<A>
export declare const None: Option<never>

export declare function fromFalsy<A>(value: A): Option<ExtractValue<A>>
```

---

# 점진적 채택

## TypeScript로 작성된 블로그 코드를 ReScript로 변경하고 있습니다.

TypeScript & ReScript & JavaScript 3가지 언어를 동시에 사용할 수 있다.

<img class="w-600px m-auto" src="/images/lan-percent.png" alt="ts67per res19per" />

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-t from-orange-600 to-rose-200">
      아쉬웠던 점
  </h1>
</div>

---

# 바인딩

### 자바스크립트 함수를 사용하기 위해 바인딩을 해야 한다.

<br />

Next.js의 Head 컴포넌트 바인딩 코드

```res
// https://github.com/MoOx/rescript-next
module Head = {
  @module("next/head") @react.component
  external make: (~children: React.element) => React.element = "defalut"
}
```

Web api의 addEventListener, removeEventListener 바인딩 코드


```res
@val @scope("document")
external addEventListener: (string, t => unit) => unit = "addEventListener"
@val @scope("document")
external removeEventListener: (string, t => unit) => unit = "removeEventListener"
```

---

# [rescript-bindings](https://github.com/green-labs/rescript-bindings)

<img class="w-500px m-auto" src="/images/rescript-bindings.png" alt="rescript-bindings" />

---

# 커뮤니티

stackoverflow 또는 검색으로는 도움 받기 힘들다

<v-click>
  
  **[ReScript Forum](https://forum.rescript-lang.org/) 을 이용합니다.**

</v-click>

<img class="w-800px m-auto" src="/images/sof.png" alt="stackoverflow" />

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-t from-orange-100 to-rose-500">
      마무리
  </h1>
</div>

---

# Relay

[relay.dev](https://relay.dev)

- 그래프큐엘 클라이언트 라이브러리

<br />

```res
module Query = %relay(`
  query IndexQuery {
    user {
      name
      age
    }
  }
`)

type props = { data: IndexQuery_graphql.Types.response}
```

---

# 지금 설치하세요

<br />

```shell
npm install rescript --save-dev
```

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tr from-pink-100 to-rose-500">
      감사합니다!
  </h1>
</div>

---

# 레퍼런스

- https://unsplash.com/photos/z8kriatLFdA
- https://www.youtube.com/watch?v=WN5UfUjVTNE
- https://www.youtube.com/watch?v=tn0zt7U7roY
- https://www.youtube.com/watch?v=dr1PskGSdU4
- https://www.youtube.com/watch?v=ZY4n7B0pZFw
- https://www.youtube.com/watch?v=XWgL51JSbGI
- https://www.youtube.com/watch?v=kAWP0laFz6M
- https://green-labs.github.io/why-rescript
- https://rescript-lang.org