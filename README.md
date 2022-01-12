
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
    const [count, setCount] = useState(0)        
  </p>
</details>
