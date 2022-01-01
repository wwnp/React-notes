
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
jsx - syntax extentions for js; шаблонизатор( есть еще pug(former jade), twig ...) <br />
inside {}: <br />
not permitted instructions: if ,switch, for,while <br />
permitted expression: fn(), exp ? [ifTrue] : [ifFalse] 
```
https://codesandbox.io/s/react-quick-start-p7m0g
```
