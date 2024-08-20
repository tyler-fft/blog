---
layout: _posts/20240817
title: React Learning
date: 2024-08-20 18:28:20
tags:
---

[01 - React re-render 1](#p01) 

### <a name="p01"></a> 01 - React re-render 1  
Code :
```javascript
import * as React from 'react'
import { useState, useEffect} from 'react'
import { createRoot } from 'react-dom/client'

function A() {
  console.log('A')
  return <B/>
}

function B() {
  console.log('B')
  return <C/>
}

function C() {
  console.log('C')
  return null
}

function D() {
  console.log('D')
  return null
}

function App() {
  const [state, setState] = useState(0)
  useEffect(() => {
    setState(state => state + 1)
  }, [])
  console.log('App')
  return (
    <div>
      <A state={state}/>
      <D/>
    </div>
  )
}

const root = createRoot(document.getElementById('root'));
root.render(<App/>)
```
Answer:
```js
"App"
"A"
"B"
"C"
"D"
"App"
"A"
"B"
"C"
"D"
```
