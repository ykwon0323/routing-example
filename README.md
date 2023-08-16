# React Routing

## React Router 모듈 설치
~~~ shell
npm install react-router-dom
~~~

## App component 수정
src/App.js
~~~ javascript
import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
import Home from './components/Home';
import About from './components/About';
import Contact from './components/Contact';

const App = () => {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
            <li>
              <Link to="/contact">Contact</Link>
            </li>
          </ul>
        </nav>

        <Routes>
          <Route path="/about">
            <About />
          </Route>
          <Route path="/contact">
            <Contact />
          </Route>
          <Route path="/">
            <Home />
          </Route>
        </Routes>
      </div>
    </Router>
  );
};

export default App;


~~~

## Screen Component 생성 
src/components/Home.js
src/components/About.js
src/components/Contact.js


## Errors 

~~~ shell

One of your dependencies, babel-preset-react-app, is importing the
"@babel/plugin-proposal-private-property-in-object" package without
declaring it in its dependencies. This is currently working because
"@babel/plugin-proposal-private-property-in-object" is already in your
node_modules folder for unrelated reasons, but it may break at any time.

babel-preset-react-app is part of the create-react-app project, which
is not maintianed anymore. It is thus unlikely that this bug will
ever be fixed. Add "@babel/plugin-proposal-private-property-in-object" to
your devDependencies to work around this error. This will make this message
go away.

~~~
Solution 

이 에러 메시지는 babel-preset-react-app 패키지가 "@babel/plugin-proposal-private-property-in-object" 패키지를 의존성으로 선언하지 않고 가져오고 있다는 내용입니다. 이로 인해 현재는 "@babel/plugin-proposal-private-property-in-object" 패키지가 이미 node_modules 폴더 내에 있는 상태이며, 불필요한 이유로 작동 중일 수 있습니다. 그러나 이러한 상태가 언제든지 깨질 수 있습니다.

이 문제를 해결하기 위해 "@babel/plugin-proposal-private-property-in-object" 패키지를 devDependencies에 추가하면 됩니다. 이를 통해 위의 에러 메시지가 사라지게 됩니다.

패키지 설치:
먼저 해당 패키지를 devDependencies에 설치합니다.

bash
~~~ bash
npm install --save-dev @babel/plugin-proposal-private-property-in-object
~~~
확인:
패키지가 제대로 설치되었는지 확인합니다. package.json 파일 내에 devDependencies 항목에 해당 패키지가 나타나야 합니다.

json
~~~ json
"devDependencies": {
  "@babel/plugin-proposal-private-property-in-object": "버전",
  // 다른 devDependencies 항목들...
}
~~~
애플리케이션 다시 시작:
패키지를 추가한 후에는 React 애플리케이션을 다시 시작합니다.

위의 단계를 따라 하면 에러 메시지가 사라지고 문제가 해결될 것입니다.