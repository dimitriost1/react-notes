ComponentA.jsx

```js
import React from "react";
import useIsMobile from "./hooks/useIsMobile";
import useNumber from "./hooks/useIsMobile";

function ComponentA() {
  console.log("render A");
  const isMobile = useIsMobile();
  console.log(isMobile);
  return <div>ComponentA</div>;
}

export default ComponentA;
```

useIsMobile.js
```js
import { useEffect, useState } from "react";

export default function useIsMobile() {
  const [isMobile, setIsMobile] = useState(null);

  const calculateIsMobile = () => {
    console.log("yo");
    if (window.innerWidth <= 768) return setIsMobile(true);
    setIsMobile(false);
  };

  useEffect(() => {
    window.addEventListener("resize", calculateIsMobile);
    calculateIsMobile();
  }, []);
  return isMobile;
}

```