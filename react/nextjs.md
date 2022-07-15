### NEXTJS 설치 및 셋팅
```
npx create-next-app --ts my-app
cd my-app
yarn add @emotion/react @emotion/styled @mui/icons-material @mui/material @mui/style
```

```js
// _app.tsx
import type { AppProps } from "next/app";
import CssBaseline from "@mui/material/CssBaseline";

const App = (props: AppProps) => {
  const { Component, pageProps } = props;

  return (
    <>
      <CssBaseline />
      <Component {...pageProps} />
    </>
  );
};

export default App;
```

.babelrc
```json
{
  "presets": ["next/babel"],
  "plugins": [
    [
      "babel-plugin-styled-components",
      { "fileName": true, "displayName": true, "pure": true, "ssr": true }
    ]
  ]
}
```
