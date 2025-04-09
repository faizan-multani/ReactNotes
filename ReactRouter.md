# React Router :
- React Router is a standard library used to manage routing in React applications. It enables navigation between different components in a React app, allowing you to create a single-page application (SPA) where different content can be displayed dynamically based on the URL.

## Key Points :
- Routing: It allows developers to define "routes" that map a URL to a component. When the URL changes, the corresponding component is rendered without reloading the entire page.

- Declarative: React Router uses a declarative approach to define routes. This means you describe how the routing should behave in your component, rather than manually managing URL changes.

- Dynamic URL Matching: It supports dynamic routing, where you can define parts of the URL as parameters (e.g., /profile/:id), and React Router can capture the values and pass them to the components.

- Nested Routes: React Router supports nested routes, allowing for complex URL structures and layouts.

- History and Navigation: It manages browser history, which means you can use the browser's back and forward buttons, and programmatically navigate using hooks like useNavigate().

- Linking: You can use the Link component to create links between routes, ensuring that the navigation happens without reloading the page.

## Commonly Used Components and Hooks :
- BrowserRouter: The wrapper that holds all the routing logic. It listens to the URL changes in the browser.

- Route: Defines a route. It maps a URL path to a component that should render when the path is matched.

- Link: Provides navigation by creating links between routes.

- useNavigate(): A hook that allows you to navigate programmatically.

- useParams(): A hook to access the parameters in the route (e.g., in /profile/:id).

### Example :
```
import React from 'react';
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';

function Home() {
  return <h2>Home Page</h2>;
}

function About() {
  return <h2>About Page</h2>;
}

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}

export default App;
```
- In this example, when the user clicks on "Home" or "About," the corresponding component (Home or About) will be displayed, and the URL will update accordingly without causing a full page reload.
- React Router is essential for building modern, dynamic React applications with smooth navigation and state management!