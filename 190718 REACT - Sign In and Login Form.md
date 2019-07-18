## 190718 REACT - Sign In and Login Form

- Index.js

~~~ 
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';

import Loginform from './Loginform.js';
import Signup from './Signup.js';

import * as serviceWorker from './serviceWorker';

ReactDOM.render(<Loginform />, document.getElementById('root'));
ReactDOM.render(<Signup />, document.getElementById('root'));


// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://bit.ly/CRA-PWA
serviceWorker.unregister();

~~~





- Signup.js

~~~javascript
import React, { Component } from 'react';
import 'bootstrap/dist/css/bootstrap.min.css';
import { Button, Form, FormGroup, Label, Input} from 'reactstrap';
import "./Loginform.css"

class Loginform extends Component {
    render() {
        return (
            <Form className="signupform">

                <h1>Carhistory.com</h1>
                <h3>Become Our Member!</h3>


                <FormGroup>
                    <Label>Name</Label>
                    <Input type="text" placeholder="First Name"></Input>
                </FormGroup>

                <FormGroup>
                    <Label>ID</Label>
                    <Input type="text" placeholder="ID"></Input>
                </FormGroup>

                <FormGroup>
                    <Label>Password</Label>
                    <Input type="password" placeholder="Password"></Input>
                </FormGroup>

                <FormGroup>
                    <Label>email</Label>
                    <Input type="email" placeholder="Email Address"></Input>
                </FormGroup>
                <br />
                <FormGroup>
                <Label>Would you like to recieve emails from us?</Label>
                    <Input type="checkbox" id="checkbox" />Yes &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                    <Input type="checkbox" id="checkbox" />No
                </FormGroup>

                <Button className="btn btn-lg btn-primary btn-block">Done</Button>
                
         </Form>
        );
    }
}

export default Loginform;
~~~



- Signup.css

~~~ html
.signupform {
    width: 400px;
    padding: 50px;
    border: 1px solid;
    margin: 50px auto;
}

h3 {
    text-align: center;
    color: tomato;
}

h1 {
    text-align: center;
    color: skyblue;
}
~~~





- LoginForm.js

~~~ javascript
import React, { Component } from 'react';
import 'bootstrap/dist/css/bootstrap.min.css';
import { Button, Form, FormGroup, Label, Input} from 'reactstrap';
import "./Loginform.css"

class Loginform extends Component {
    render() {
        return (
            <Form className="loginform">

                <h1>Carhistory.com</h1>
                <h3>Welcome!</h3>

                <FormGroup>
                    <Label>Email</Label>
                    <Input type="email" placeholder="Email"></Input>
                </FormGroup>

                <FormGroup>
                    <Label>Password</Label>
                    <Input type="password" placeholder="Password"></Input>
                </FormGroup>

                <Button className="btn btn-lg btn-dark btn-block">Login</Button>

                <FormGroup>
                    <Input type="checkbox" id="checkbox" />Keep me logged in
                </FormGroup>

            <div className="text-center">
                <a href="/sign-up">Sign-up</a>
                <span> | </span>
                <a href="/sign-up">Forgot password?</a>
            </div>
         </Form>
        );
    }
}

export default Loginform;
~~~



- LoginForm.css

~~~ 
.loginform {
    width: 400px;
    padding: 50px;
    border: 1px solid;
    margin: 50px auto;
}

h3 {
    text-align: center;
    color: tomato;
}

h1 {
    text-align: center;
    color: skyblue;
}
~~~

