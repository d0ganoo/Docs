


# react-router-dom

#### Ces deux exemples font exactement la même chose

```Javascript

import React, { Component } from 'react';
import { render } from 'react-dom';
import { BrowserRouter as Router, Route, Switch,Link } from 'react-router-dom';

const Home = () => (
  <div>
      <h2>Home</h2>
  </div>
);

const About = () => (
  <div>
      <h2>About</h2>
  </div>
);

const Topic = ({ match }) => (
  <div>
      <h3>{match.params.topicId}</h3>
  </div>
);

const Topics = ({ match }) => (
  <div>
    <h2>Topics</h2>
    <ul>
      <li>
        <Link to={`${match.url}/rendering`}>Rendering with React</Link>
      </li>
      <li>
        <Link to={`${match.url}/components`}>Components</Link>
      </li>
      <li>
        <Link to={`${match.url}/props-v-state`}>Props v. State</Link>
      </li>
    </ul>

    <Route path={`${match.path}/:topicId`} component={Topic} />
    <Route
      exact
      path={match.path}
      render={() => <h3>Please select a topic.</h3>}
    />
  </div>
);

const BasicExample = () => (
  <Router>
      <div>
          <ul>
              <li>
                  <Link to="/">Home</Link>
              </li>
              <li>
                  <Link to="/about">About</Link>
              </li>
              <li>
                  <Link to="/topics">Topics</Link>
              </li>
          </ul>

          <hr />

          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
          <Route path="/topics" component={Topics} />
      </div>
  </Router>
);


render(
    <BasicExample />,
    document.getElementById('root')
);

```

```Javascript

import React, { Component } from 'react';
import { render } from 'react-dom';
import { BrowserRouter as Router, Route, Switch,Link } from 'react-router-dom';

const Home = () => (
  <div>
      <h2>Home</h2>
  </div>
);

const About = () => (
  <div>
      <h2>About</h2>
  </div>
);

const Topic = ({ match }) => (
  <div>
      <h3>{match.params.topicId}</h3>
  </div>
);


class Topics extends Component {
  constructor(props){
    super(props)
  }
  render(){
    const {match} = this.props;
    
    return(
      <div>
        <h2>Topics</h2>
        <ul>
          <li>
            <Link to={`${match.url}/rendering`}>Rendering with React</Link>
          </li>
          <li>
            <Link to={`${match.url}/components`}>Components</Link>
          </li>
          <li>
            <Link to={`${match.url}/props-v-state`}>Props v. State</Link>
          </li>
        </ul>

        <Route path={`${match.path}/:topicId`} component={Topic} />
        <Route
          exact
          path={match.path}
          render={() => <h3>Please select a topic.</h3>}
        />
      </div>
    );
  }
}

const BasicExample = () => (
  <Router>
      <div>
          <ul>
              <li>
                  <Link to="/">Home</Link>
              </li>
              <li>
                  <Link to="/about">About</Link>
              </li>
              <li>
                  <Link to="/topics">Topics</Link>
              </li>
          </ul>

          <hr />

          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
          <Route path="/topics" component={Topics} />
      </div>
  </Router>
);


render(
    <BasicExample />,
    document.getElementById('root')
);

```

#### Router variable en paramètre, component statefull mais perte de la fonctionnalité pour récupérer les données via url

```Javascript

const Home = () => (
  <div>
      <h2>Home</h2>
  </div>
);

const About = () => (
  <div>
      <h2>About</h2>
  </div>
);

class Topic extends Component{
  constructor(props){
    super(props);
  }
  render(){
    return(
      <div>
        <h3>Bonjour {this.props.extra}</h3>
      </div>
    );
  }
}

class Topics extends Component {
  constructor(props){
    super(props);
    this.state = {
      profils: [1,2,3,4,5,6,7,8,9]
    };
  }
  render(){
    const {match, nom} = this.props;
    let prenom = 'Francois';

    return(
      <div>
        <h2>Topics</h2>
        <ul>
          <li>
            <Link to={`${match.url}/rendering`}>Rendering with React</Link>
          </li>
          <li>
            <Link to={`${match.url}/components`}>Components</Link>
          </li>
          <li>
            <Link to={`${match.url}/props-v-state`}>Props v. State</Link>
          </li>
        </ul>
          <Route path={`${match.path}/:topicId`}  render={() => <Topic {...this.props} extra={`${prenom} ${nom}`}  state={this.state.profils}/>} />
          <Route
            exact
            path={match.path}
            render={() => <h3>Please select a topic.</h3>}
          />
      </div>
    );
  }
}

const BasicExample = () => {
  const tata = "FF";
  return (
    <Router>
      <div>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
          <li>
            <Link to="/topics">Topics</Link>
          </li>
        </ul>

        <hr />

        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
        <Route path="/topics" render={props => <Topics {...props} nom={tata}/>}/>
      </div>
    </Router>
    );
};


render(
    <BasicExample />,
    document.getElementById('root')
);

```





