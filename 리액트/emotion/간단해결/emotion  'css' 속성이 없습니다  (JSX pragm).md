s
## 현상
React의 JSX를 사용하기 때문에 발생함, 해당 현상을 해결하기 위해서는 Emotion의 JSX를 사용하도록 
JSX Pragma를 추가해야한다.

## JSX pragma
눈썰미가 좋으신 분들은 위 예제 코드에서 `/** @jsxImportSource @emotion/react */` 부분이 눈에 띄셨을 거 같은데요. 이 것을 소위 JSX pragma라고 하는데 쉽게 설명하면 Babel 트랜스파일러한테 JSX 코드를 변환할 때, React의 `jsx()` 함수를 사용하지 말고, Emotion의 `jsx()` 함수를 대신 사용하라고 알려주기 위함입니다.


## 해결 

1. 
`
```typescript 
/** @jsxImportSource @emotion/react */
import { css } from '@emotion/react';

```
2. 

```bash
npm install --save @emotion/react
npm
install --save @emotion/styled
```

3. babel 설정파일 수정 (이 부분 해결)
```json

"@babel/preset-react",

{ "runtime": "automatic", "importSource": "@emotion/react" }

```