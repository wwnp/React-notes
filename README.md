
<details>
  <summary>NPM NPX</summary>
  <p>
    
  npx create-react-app project_name (new dir) <br />
  npx create-react-app .project_name <br />
  npm start <br />
  npm run build <br />
    
  https://codesandbox.io/s/react-quick-start-p7m0g <br />
  </p>
</details>

<details>
  <summary>without JSX</summary>
  <p>
    
    ReactDOM.render(
        React.createElement('div', {className:'App', sex:'sex'}, [
          React.createElement('h1', null, 'App'),
          React.createElement('p', null, '2010')
        ]),
        document.getElementById('root')
    );
    
  </p>
</details>
<details>
  <summary>jsx - syntax extentions for js; шаблонизатор( есть еще pug(former jade), twig ...)</summary>
  <p>
    
  inside {}: <br />
  not permitted instructions: if ,switch, for,while <br />
  permitted expression: fn(), exp ? [ifTrue] : [ifFalse] 
    
  </p>
</details>

// Do not lose this:
// 
// 2
//  2.1  (this.counterHandler.bind(this) ) *2 
//  2.2 use () => this.counterHandler() *3
// 3 use arrow fn
//  const = counterHandler = (vector) {
//   this.setState({
//     counter: this.state.counter + 1
//   });
// }

<details>
  <summary>1. binding in constructor </summary>
  <p>
    
    constructor(props) {
      super(props);
      this.state = {
        counter: 0
      };
      this.counterHandler = this.counterHandler.bind(this) // *1
    }
    
  </p>
</details>
<details>
  <summary>2. binding in onClick </summary>
  <p>
    
  this.counterHandler.bind(this)
    
  </p>
</details>
<details>
  <summary>3. use arrow in onCLick</summary>
  <p>
    
    <button onClick={() => this.counterHandler}>Add</button>
    
  </p>
</details>
<details>
  <summary>4. use arrow fn</summary>
  <p>
    
  const = counterHandler = () => {
    this.setState({
      counter: this.state.counter + 1
    });
    
  </p>
</details>
