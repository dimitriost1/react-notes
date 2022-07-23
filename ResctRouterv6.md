App.js

```js
import logo from "./logo.svg";
import "./App.css";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Dashboard from "./pages/Dashboard";
import Profile from "./pages/Profile";
import Home from "./pages/Home";
import ProfileData from "./components/ProfileData";

function App() {
  return (
    <BrowserRouter>
      <nav>NavBAr</nav>
      <Routes>
        <Route path="" element={<Home />} />
        <Route path="dashboard" element={<Dashboard />} />
        {/* <Route path="profile" element={<Profile />} />
        <Route path="profile/:userId" element={<Profile />} /> */}
        <Route path="profile" element={<Profile />}>
          {/* η παρακάτω γραμμή καλύτερα ν παει απ'εξω */}
          <Route path=":userId" element={<Profile />} /> 
          <Route path="data" element={<ProfileData />} />
        </Route>
        <Route path="*" element={<h1>Not Found</h1>} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;

```
---

./pages/Home.js

```js
import React from 'react'

function Home() {
  return (
    <h1>Home</h1>
  )
}

export default Home
```

./pages/Dashboard.js

```js
import React from "react";
import { Link, useNavigate } from "react-router-dom";

function Dashboard() {
  const navigate = useNavigate();

  const onClick = () => {
    setTimeout(() => {
      navigate("/profile");
    }, 2000);
  };

  return (
    <>
      <h2>Dashboard</h2>
      <Link to="/profile">Go to Profile</Link>
      <button onClick={onClick}>Go to Profile</button>
    </>
  );
}

export default Dashboard;

```
./pages/Profile.js

```js
import React from "react";
import { useParams, Outlet } from "react-router-dom";

function Profile() {

  const {userId} = useParams()


  return (
    <>
      <h2>Profile {userId}</h2>
      <Outlet/>
    </>
  );
}

export default Profile;

```
---

./components/ProfileData

```js
import React from 'react'

function ProfileData() {
  return (
    <div>ProfileData</div>
  )
}

export default ProfileData
```
