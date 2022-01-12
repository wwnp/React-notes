
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

<hr /> 

#### Do not lose this:
<details>
  <summary>Example</summary>
  <p>
    
    import React from "react";

    export class HomeClass extends React.Component {
      state = { counter: 0 };
      // or
      // constructor(props) {
      //   super(props);
      //   this.state = {
      //     counter: 0
      //   };
      //   this.counterHandler = this.counterHandler.bind(this) // *1
      // }

      counterHandler(vector) {
        this.setState({
          counter: this.state.counter + 1
        });

        // to add 3 to counter at once
        this.setState(
          (prevState) => {
            return { counter: prevState.counter + 1 };
          },
          () => {
            console.log("cb counter 1");
          }
        );
    
        // short -v (without return)
        this.setState(
          (prevState) => ({ counter: prevState.counter + 1 }),
          () => {
            console.log("cb counter 2");
          }
        );
        this.setState(
          (prevState) => ({ counter: prevState.counter + 1 }),
          () => {
            console.log("cb counter 3");
          }
        );
      }
      render() {
        return (
          <div className="Home">
            <h1
              data-name="dataHome"
              onClick={(e) => console.log(e.target.dataset.name)}
            >
              HomeClass
            </h1>
            <p>{this.state.counter}</p>
            
            <button onClick={this.counterHandler.bind(this)}>Add</button>
            {/*  or  */}
            <button onClick={() => this.counterHandler}>Add</button>
          </div>
        );
      }
    }

    
  </p>
</details>
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
    
    <button onClick={this.counterHandler.bind(this)}>Add</button>
    
  </p>
</details>
<details>
  <summary>3. use arrow in onCLick</summary>
  <p>
    
    <button onClick={() => this.counterHandler()}>Add</button>
    
  </p>
</details>
<details>
  <summary>4. use arrow fn</summary>
  <p>
    
    const = counterHandler = () => {
      this.setState({
        counter: this.state.counter + 1
      });
    }
  </p>
</details>

<hr /> 


<details>
  <summary>ref - ссылка на пределенный элемент в доме</summary>
  <p>
    
    export class FormClassPage extends React.Component {
      constructor(props) {
        super(props)
        this.state = {
          firstName: "",
          ...
        };
        this.emailRef = React.createRef()  // for focus()

        this.cardRef = React.createRef() // uncontrollable input
        this.telRef = React.createRef()// uncontrollable input
      }
      handleInputs = (event) => {
        this.setState({
          [event.target.name]: event.target.value
        }, () => {
          if (this.state.firstName.length === 16) { // for bank card
            this.emailRef.current.focus()
          }
        });
      };

      render() {
        return (
           <div>
              <input
                name={"firstName"}
                placeholder={"first name"}
                type="text"
                value={this.state.firstName}
                onChange={this.handleInputs}
              />
              <br />
              <input
                name={"email"}
                placeholder={"email"}
                type="email"
                value={this.state.email}
                onChange={this.handleInputs}
                ref={this.emailRef}
              />
            </div>
            <hr />
            <form onSubmit={this.formCardSubmit}>
              <input
                name={"card"}
                placeholder={"card"}
                type="text"
                ref={this.cardRef}
              />
              <input
                name={"tel"}
                placeholder={"tel"}
                type="tel"
                ref={this.telRef}
              />
              <button>Send</button>
            </form >
          </div>
        );
      }
      // --------------
      formCardSubmit = (e) => {
        console.log(this.cardRef.current)
        e.preventDefault()
        if (this.cardRef.current.value.length < 16) {
          alert('this.cardRef.current.value.length < 16')
          return
        }
        if (this.telRef.current.value.length < 11) {
          alert('this.telRef.current.value.length < 11')
          return
        }
        this.cardRef.current.value = ''
        this.telRef.current.value = ''
        alert('data sent')
      }
    }
       
  </p>
</details>
<hr/>
<details>
  <summary>useState</summary>
  <p>
    
    export const App = props => {
      const [count, setCount] = useState(0)      
      const add = () => {
    
      }
      return (
        <div >
        
        </div>
      )
    }
      
    
  </p>
</details>

<details>
  <summary>materialize CSS React</summary>
  <p>
    
    With NPM:

    Step 1) Install materialize

    npm install materialize-css@next 
    Check the materialize documentation for any updates. Don't miss the @next at the end. The installed version will be something like: ^1.0.0-rc.2 or ^1.0.0-alpha.4

    Step 2) Import materialize JS:

    import M from 'materialize-css'
    Or if that doesn't work you can try import M from 'materialize-css/dist/js/materialize.min.js'

    Step 3) Import materialize CSS:

    In index.html

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-rc.2/css/materialize.min.css">
    OR in javascript

    import 'materialize-css/dist/css/materialize.min.css'
    In order for the css import to work, you would need a css loader. Note that this loader is already included in projects built using create-react-app so you don't need the  next steps. If instead, you are using custom webpack config, then run:

    npm install --save-dev style-loader css-loader
    Now add css-loader and style-loader in webpack config

    const path = require("path");

    module.exports = {
        entry: "./src/index.js",
        output: {
            filename: "bundle.js",
            path: path.join(__dirname, "build")
        },
        module: {
            rules: [
                {
                    test: /\.css$/,
                    use: [
                        'style-loader',
                        'css-loader'
                    ]
                },
                {
                    test: /.js$/,
                    exclude: /(node_modules)/,
                    use: {
                        loader: "babel-loader",
                        options: {
                            presets: ["env", "react"]
                        }
                    }
                }
            ]
        }
    }
    Now you can initialize components individually, or all at once using M.AutoInit();

    Step 4) Import materialize icons:

    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    With CDN:

    Add the following in your HTML file.

    <!-- Materialize CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-rc.2/css/materialize.min.css">

    <!-- Materialize JS -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-rc.2/js/materialize.min.js"></script>

    <!-- Materialize Icons -->
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
      
    
  </p>
</details>

