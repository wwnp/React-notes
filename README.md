
npx create-react-app project_name (new dir) <br />
npx create-react-app .project_name <br />
or <br/>
https://codesandbox.io/ <br />
– – – – - <br />
without JSX :
  ```
    const App = () => {
      return React.createElement("h1", {id:'hello, className: 'cls1'},'App')
    }
    ReactDOM.render(React.createElement(App), document.getElementById('root'))
  ```
jsx - syntax extentions for js

