---
layout: post
title: "[typescript] Redux 8 버전 dispatch => Promise<void> Error - ts(2345)"
subtitle: typescript Redux / thunk / useAppDispatch
categories: markdown
tags: [React, typescript]
---

typescript에 Redux를 사용하던 도중 `useDispatch` 에러 발생 ❗

> #### typescript에서 Redux를 사용하기 위해 설치하는 모듈
>
> `npm install redux` > `npm install @types/redux` > `npm install react-redux` > `npm install @types/react-redux` > `npm install redux-thunk` > `npm install @types/redux-thunk`

---

### App.tsx

`dispatch` 의 유형을 읽어오지 못하는 에러발생 💫

![](https://velog.velcdn.com/images/-__-/post/b7ac79a8-2abc-4b65-8283-5de0ae42b55d/image.png)

---

### store.ts

store 에서 작성된코드는 문제가 없어보였다

![](https://velog.velcdn.com/images/-__-/post/fec5be63-9c19-4d72-bfff-8631db96abfd/image.png)

---

### package.json 수정작업

혹시 몰라서 버전을 조금 낮춰서 다시 설치를 했는데
에러가 해결되었다...😓

![](https://velog.velcdn.com/images/-__-/post/a7b6d83e-67ff-4f6e-bab0-27b0ca556225/image.png)

package.json 에서
**"react-redux"** 버전을 낮추는 작업
"8.0.2" 👉👉👉 "7.2.1"
**(8 버전 이하면 다 실행이 된다)**

버전을 임의로 낮추고 수정 후에는 `npm install` 을 해줘야 적용이 된다 !

> redux 8 버전으로 업데이트 되면서 `Dispatch` 호출방법이 바뀐듯한데 알아봐야겠다... ✍
> 👉 `useAppDispatch` 으로 호출해주는 방식

---

### 참고 했던 사이트 🖥

- https://github.com/reduxjs/redux-toolkit/issues/2294

- https://stackoverflow.com/questions/72396293/argument-of-type-dispatch-dispatchshopdispatchtypes-promisevoid-is-n

- https://redux.js.org/tutorials/typescript-quick-start

---

> ### <span style="background-color:#FFC701; color:#000;">발생했던 에러 내용</span>
>
> `(alias) fetchPokemonData(pokemonNames: string): (dispatch: Dispatch<PokemonDispatchType>) => Promise<void> import fetchPokemonData Argument of type '(dispatch: Dispatch<PokemonDispatchType>) => Promise<void>' is not assignable to parameter of type 'AnyAction'.ts(2345)`
