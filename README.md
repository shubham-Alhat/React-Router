# React Routing

## React does not have inbuilt routing feature. so we need to install "react-router-dom".

After installation, we can check the **react-router-dom** in **package.json** file. it is installed as dependency.

Now we can import its components and methods to enable routing in our app.

## Components: _NavLink_, _Link_, _Outlet_, _RouterProvider_ and much more.

## methods: _createBrowserRouter_, _createRoutesFromElements_, etc.

**NavLink**
it is used to navigate through different routes without reloading. Means it changes the URL or address when it is clicked without reload. it allows styling based on active link.

```jsx
<NavLink
  to="/"
  className={({ isActive }) =>
    `block py-2 pr-4 pl-3 duration-200 ${
      isActive ? "text-orange-700" : "text-gray-700"
    } border-b border-gray-100 hover:bg-gray-50 lg:hover:bg-transparent lg:border-0 hover:text-orange-700 lg:p-0`
  }
>
  Home
</NavLink>
```

**Link**
it is same as NavLink. it changes URL without reload but it does not have feature of styling based on active link.

```jsx
<Link to="/about" className="hover:underline">
  About
</Link>
```

**Outlet**
It is placeholder for child elements. it is used inside the parent element. it shows where the child element should render. whenever the URL or address matches the child URL path, react router renders that corresponding child element in place of Outlet component.

```jsx
function App() {
  return (
    <>
      <Header />
      <Outlet />
      <Footer />
    </>
  );
}
```

**RouterProvider** : it is used to manage navigation in your app using a prop. it takes router object as prop created using _createBrowserRouter()_. On the basis of router object, it manage navigation in your app.

**_createRoutesFromElements()_** allows us to define routing in jsx syntax i.e using jsx element.

#### **App.jsx**

```jsx
function App() {
  return (
    <>
      <Header />
      <Outlet />
      <Footer />
    </>
  );
}
```

#### **main.jsx**

```jsx
// import statements are skipped.

const router = createBrowserRouter(
  createRoutesFromElements(
    <Route path="/" element={<App />}>
      <Route path="" element={<Home />} />
      <Route path="about" element={<About />} />
      <Route path="contact" element={<Contact />} />
      <Route path="user/:userId" element={<User />} />
    </Route>
  )
);

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <RouterProvider router={router} />
  </StrictMode>
);
```

Now our app has seamless routing...
