# React `useRef` Хук

## Введение

`useRef` — это один из хуков в React, который позволяет вам сохранять мутируемое значение, которое не вызывает повторного рендеринга компонента при изменении. Этот хук полезен в различных сценариях, включая доступ к DOM-элементам, сохранение состояния между рендерами и управление таймерами.

## Как работает `useRef`?

Когда вы вызываете `useRef` в компоненте, он возвращает объект с единственным свойством `current`. Это свойство может быть использовано для хранения любого значения. Важно отметить, что изменение значения `current` не вызывает повторного рендеринга компонента.

```javascript
import React, { useRef, useState } from 'react'

const App = () => {

const [count, setCount] = useState(0)

let someNumber = useRef(0)
const hisob =()=>{
  setCount(count+1)
  someNumber.current = someNumber.current + 1
}

  return (
    <div>
      <h1>Count:{count}</h1>
      <h2>Number:{someNumber.current}</h2>
      <button onClick={hisob}>hisob</button>
    </div>
  )
}

export default App
```


```javascript
import React, { useRef, useState } from 'react'

const App = () => {

  const [name,setName]=useState("")
  const [email,setEmail]=useState("")
  const nameInputRef = useRef();
  const emailInputRef = useRef();
  const handleKeyup =(e)=>{
    if (e.key === "ArrowDown"){
      emailInputRef.current.focus();
    }
  }

  const handleKeyup2 =(e)=>{
    if (e.key === "ArrowUp"){
      nameInputRef.current.focus();
    }
  }


  return (
    <div>
        <form action="">
          <input ref={nameInputRef} type="text" placeholder='Name' value={name} onChange={(e)=>setName(e.target.value)} onKeyUp={handleKeyup}/> <br />
          <input ref={emailInputRef} type="text" placeholder='Email' value={email} onChange={(e)=>setEmail(e.target.value)} onKeyUp={handleKeyup2} />
        </form>
    </div>
  )
}

export default App


```




## useRef — это хук в React, который позволяет сохранить изменяемое значение без повторного рендеринга компонента. Это значение хранится в свойстве current объекта, созданного с помощью useRef. Ты можешь изменять и использовать это значение как угодно, и оно остается неизменным между рендерами компонента. useRef особенно полезен, когда нужно работать с DOM-элементами или хранить данные, которые не должны вызывать повторный рендер.







# Ты можешь использовать useRef, чтобы получить доступ к div элементу и изменить его содержимое, например, текст внутри.

```java script
import React, { useRef } from 'react';

const App = () => {
  const divRef = useRef(null);

  const changeText = () => {
    divRef.current.textContent = "Новый текст внутри div";
  };

  return (
    <div>
      <div ref={divRef}>Это изначальный текст</div>
      <button onClick={changeText}>Изменить текст</button>
    </div>
  );
};

export default App;

```

### Ты можешь изменить текст внутри div с помощью useRef без кнопки, но для этого нужно вызвать изменение после рендера компонента. Например, это можно сделать внутри useEffect. Вот как это будет выглядеть:

```java script
  
  import React, { useRef, useEffect } from 'react';

const App = () => {
  const divRef = useRef(null);

  useEffect(() => {
    divRef.current.textContent = "Новый текст внутри div";
  }, []); // [] означает, что это сработает только после первого рендера

  return (
    <div>
      <div ref={divRef}>Это изначальный текст</div>
    </div>
  );
};

export default App;


```




