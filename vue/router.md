### static html
```js
{
    test: /\.(html)$/,
    exclude: /(node_modules)/,
    use: {
      loader: "html-loader"
    }
}
Then you can import your .html files like you would components:

import Destination from '/path/to/destination.html'
Now treat component as an Object and leverage the template property to serve static HTML files:

 {
  path: '/destination',
  mode: history,
  name: 'destination',
  component: { template: Destination }
}
```
