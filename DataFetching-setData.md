App.js

'''js
import axios from "axios";
import { useState } from "react";

const defaultFormData = {
  title: "",
  body: "",
  userId: 1,
};

export default function App() {
  const [formData, setFormData] = useState(defaultFormData);
  const [success, setSuccess] = useState(false);
  const [error, setError] = useState(false);

  const { title, body } = formData;

  const onChange = (e) => {
    setFormData((prevState) => ({
      ...prevState,
      [e.target.id]: e.target.value,
    }));
  };

  const onSubmit = async (e) => {
    e.preventDefault();

    try {
      // const response = axios.post(
      //   "https://jsonplaceholder.typicode.com/posts",
      //   formData
      // );

      await axios.post("https://jsonplaceholder.typicode.com/posts", formData);
      // console.log(response);
      setSuccess(true);
      setError(false);
    } catch (error) {
      setError(true);
      setSuccess(false);
      console.log("yo");
    }

    setFormData(defaultFormData);
  };

  return (
    <>
      <h1>Form</h1>
      <p>Create a post</p>

      <form onSubmit={onSubmit}>
        <label htmlFor="title">Title</label>
        <br />
        <input type="text" id="title" value={title} onChange={onChange} />
        <br />
        <br />
        <label htmlFor="body">Body</label>
        <br />
        <input type="text" id="body" value={body} onChange={onChange} />
        <br />
        <br />
        <button type="submit">Upload post</button>
      </form>

      {error && <p>Oops, could not upload post...</p>}
      {success && <p>Post has successfully uploaded!</p>}
    </>
  );
}

'''
---

FileUpload.jsx

'''js
import axios from "axios";
import { useState } from "react";

function FileUpload() {
  const [file, setFile] = useState(null);

  const onChange = (e) => setFile(e.target.files[0]);

  const onSubmit = async (e) => {
    e.preventDefault();

    const formData = new FormData();
    formData.append("file", file);

    const response = await axios.post("https://yo232fake.io", formData);
    console.log(response);
  };

  return (
    <>
      <form onSubmit={onSubmit}>
        <label htmlFor="file">Image Upload</label>
        <br />
        <input type="file" id="file" accept=".png,.jpg" onChange={onChange} />
        <br />
        <br />
        <button>Upload file</button>
      </form>
    </>
  );
}

export default FileUpload;

'''

--Upload Files--

FileUpload.jsx
```js
import axios from "axios";
import { useState } from "react";

function FileUpload() {
  const [file, setFile] = useState(null);

  const onChange = (e) => setFile(e.target.files[0]);

  const onSubmit = async (e) => {
    e.preventDefault();

    const formData = new FormData();
    formData.append("file", file);

    const response = await axios.post("https://yo232fake.io", formData);
    console.log(response);
  };

  return (
    <>
      <form onSubmit={onSubmit}>
        <label htmlFor="file">Image Upload</label>
        <br />
        <input type="file" id="file" accept=".png,.jpg" onChange={onChange} />
        <br />
        <br />
        <button>Upload file</button>
      </form>
    </>
  );
}

export default FileUpload;

```

