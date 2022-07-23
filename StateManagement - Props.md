Για να χρησιμοποιήσουμε κοινό state σε 2 component, θα βάλουμε το state στον κοντινότερο κοινό τους πρόγονο.

App.jsx

```js
import React, { useState } from "react";
import Input from "./components/Input";
import MultipliedByTwo from "./components/MultipliedByTwo";

function App() {
  const [inputValue, setInputValue] = useState(0);

  return (
    <>
      <h1>Multiplied by two App</h1>
      <Input setInputValue={setInputValue} />
      <MultipliedByTwo inputValue={inputValue} />
    </>
  );
}

export default App;
```

./components/Input.jsx

```js
import React from "react";

export default function Input({ setInputValue }) {
  return (
    <>
      <input
        type="number"
        onChange={(e) => {
          setInputValue(e.target.value);
        }}
      />
    </>
  );
}
```

./components/MultipliedByTwo.jsx

```js
import React from "react";

// export default function MultipliedByTwo(props) {
//     console.log(props);
export default function MultipliedByTwo({ inputValue }) {
  console.log(inputValue);
  return (
    <>
      <p>Multiplied number: {inputValue * 2}</p>{" "}
    </>
  );
}
```

---

Prop Drilling: στέλουμε το state (ή κπ τιμη) πολλά επίπεδα components κατω (όχο οτι κλύτερο)
