# Context API :
- The Context API in React is a built-in feature that allows you to share state (data) across your entire app—or part of it—without having to pass props down manually at every level (also known as "prop drilling").

## Why Use Context API? 
- Imagine you have a deeply nested component tree, and you want to pass data from the top-level component to a component several levels down. Passing props through each component can get tedious and messy. Context solves this problem by letting you create global-like state for your app.

## How It Works ?
### The Context API has three main parts ->
- React.createContext()

- Provider

- Consumer (or use the useContext hook in functional components)

### ✅ Benefits :
- No more prop drilling

- Cleaner code

- Centralized state sharing

###  When Not to Use Context
- For every piece of state: Only use it for global/shared state. For local state, stick to useState.

- Performance concerns: All components using the context will re-render when the value changes.

### 🧰 Common Use Cases
- Auth/user data

- Theme (dark/light mode)

- Language/localization

- App settings

## Example :
## UserContext.js file // inside Context folder
```
import React from 'react'

const UserContext = React.createContext()

export default UserContext;
```

## UserContextProcider.jsx file // inside Context folder
```
import React from "react";
import UserContext from "./UserContext";

const UserContextProvider = ({children}) => {
    const [user, setUser] = React.useState(null)
    return(
        <UserContext.Provider value={{user, setUser}}>
        {children}
        </UserContext.Provider>
    )
}

export default UserContextProvider
```

## Login.jsx // inside Component folder
```
import React, {useState, useContext} from 'react'
import UserContext from '../context/UserContext'

function Login() {
    const [username, setUsername] = useState('')
    const [password, setPassword] = useState('')

    const {setUser} = useContext(UserContext)

    const handleSubmit = (e) => {
        e.preventDefault()
        setUser({username, password})
    }
  return (
    <div>
        <h2>Login</h2>
        <input type='text'
        value={username}
        onChange={(e) => setUsername(e.target.value) }
        placeholder='username'  />
        {" "}
        <input type='text' 
        value={password}
        onChange={(e) => setPassword(e.target.value) }
        placeholder='password'  />
        <button onClick={handleSubmit}>Submit</button>
    </div>
  )
}

export default Login
```

## Profile.jsx // inside Component folder
```
import React, {useContext} from 'react'
import UserContext from '../context/UserContext'

function Profile() {
    const {user} = useContext(UserContext)
    
    if (!user) return <div>please login</div>

    return <div>Welcome {user.username}</div>
}

export default Profile
```

## App.jsx
```
import { useState } from "react"
import reactLogo from "./assets/react.svg"
import viteLogo from "/vite.svg"
import "./App.css"

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
    
    </>
  )
}

export default App
```
