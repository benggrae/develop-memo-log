

## 개요 

[`useState`](https://ko.reactjs.org/docs/hooks-reference.html#usestate)의 대체 함수입니다. `(state, action) => newState`의 형태로 reducer를 받고 `dispatch` 메서드와 짝의 형태로 현재 state를 반환합니다. (Redux에 익숙하다면 이것이 어떻게 동작하는지 여러분은 이미 알고 있을 것입니다.)

## 왜?
기존의 상태관리를 useState를 활용하여 작성하였다 set... 이런 느낌의 함수는 뭔가 괴리감이 느낀다고 개인
적으로 생각된다 맹목적으로 값을 셋팅하는 느낌 나중에 복잡성을 해결하기 위해선 useReducer의 도움이 필요할꺼 같다.

또한, 성능 최적화에도 도움이 된다 


##  예시 

``` javascript 
const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}```

>  카운터에서 행위를 (증가, 감소) 를 뽑아내서 사용하고 있다 (행위 기반으로 명확해진다!)


## useReducer의 추가 효과  - 콜백 전달을 피할 수 있다.
 Context로 리듀서를 전달!

* 선언 
```javascript 
const TodosDispatch = React.createContext(null);

function TodosApp() {
  // 주의: `dispatch`는 다시 렌더링 간에 변경되지 않습니다
  const [todos, dispatch] = useReducer(todosReducer);

  return (
    <TodosDispatch.Provider value={dispatch}>
      <DeepTree todos={todos} />
    </TodosDispatch.Provider>
  );
}
```
* 구현
``` javascript
function DeepChild(props) {
  // 작업을 수행하려면 context에서 dispatch를 얻을 수 있습니다.
  const dispatch = useContext(TodosDispatch);

  function handleClick() {
    dispatch({ type: 'add', text: 'hello' });
  }

  return (
    <button onClick={handleClick}>Add todo</button>
  );
}
```

