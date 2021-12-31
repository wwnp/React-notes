
npx create-react-app project_name (new dir) <br />
npx create-react-app .project_name <br />
or <br/>
https://codesandbox.io/ <br />
– – – – - <br />
without JSX :
  ```
ReactDOM.render(
    React.createElement('div', {className:'App', sex:'sex'}, [
      React.createElement('h1', null, 'App'),
      React.createElement('p', null, '2010')
    ]),
    document.getElementById('root')
);
  ```
jsx - syntax extentions for js
```
index.js:
import ReactDOM from "react-dom";
import { React } from "react";
import {App} from './App'

ReactDOM.render(<App />, document.getElementById("root"));
-----
App.jsx
export const App = (props) => {
  return <h1>App</h1>;
};
```
