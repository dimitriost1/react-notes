App.js

'''js
import axios from "axios";
import { useState } from "react";
import { useEffect } from "react";
import "./App.css";

function App() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(false);

  // console.log("render...");

  useEffect(() => {
    const fetchPosts = async () => {
      try {
        setLoading(true);
        const response = await axios(
          "https://jsonplaceholder.typicode.com/posts"
        );
        setData(response.data);
        setLoading(false);
      } catch (error) {
        console.log(error);
        setError(true);
      }
    };

    fetchPosts();
  }, []);

  return (
    <>
      <h1>Yo</h1>
      {loading && !error && <h4>Loading...</h4>}
      {error && (
        <h4>Oops, could not fetch the posts, please try again later.</h4>
      )}
      {data &&
        data.map((post) => {
          const { id, title, body } = post;
          return (
            <article key={id}>
              <p>title: {title}</p>
              <p>id: {id}</p>
              <p>
                post: <br /> {body}
              </p>
              <hr />
            </article>
          );
        })}
    </>
  );
}

export default App;

'''
