Αποφεύγουμε το prop drilling

App.jsx

```js
import React, { useState } from "react";
import CalculationOverview from "./components/CalculationOverview";
import Input from "./components/Input";
import MultipliedByTwo from "./components/MultipliedByTwo";
import MultipliedCalculations from "./components/MultipliedCalculations";

function App() {
  const [inputValue, setInputValue] = useState(0);

  return (
    <>
      <h1>Multiplied by two App</h1>
      <Input setInputValue={setInputValue} />
      <CalculationOverview>
        <MultipliedCalculations>
          <MultipliedByTwo inputValue={inputValue} />
        </MultipliedCalculations>
      </CalculationOverview>
    </>
  );
}

export default App;

```

./components/CalculationOverview.jsx

```js
function CalculationOverview({ children }) {
  console.log(children);
  return <>{children}</>;
}

export default CalculationOverview;

```

./components/MultipliedCalculations.jsx

```js
function MultipliedCalculations({ children }) {
  return <>{children}</>;
}

export default MultipliedCalculations;

```
./components/MultipliedByTwo.jsx

```js
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

-Μειονεκτήματα του Component Composition-

--Can be hard to use when:--
- You need to nest a lot of comonents (wrapper hell)
- Data needs to be accesible by many compontnts at all different nesting levels
