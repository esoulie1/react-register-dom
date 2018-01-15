## Usage

### Install from npm:
`npm i --save react-register-dom`

### Integrate into your app:
*index.html*
```html
(...)

  <div class="container">
    <span id="root-login"></span>
    <span id="root-signup" data-referer="https://hostname/path/name"></span>
  </div>

(...)

  <article>
    <h4>...</h4>
    <span class="root-likebutton" data-id="37"></span>
  </article>

  <article>
    <h4>...</h4>
    <span class="root-likebutton" data-id="38"></span>
  </article>

  <article>
    <h4>...</h4>
    <span class="root-likebutton" data-id="39"></span>
  </article>

(...)
```

*app.js*
```javascript
import register from 'react-register-dom';

import Login from './components/Login';
import Signup from './components/Signup';
import LikeButton from './components/LikeButton';

// With DOM id -> #root-login
register('root-login', render => render(<Login />));

// With DOM id -> #root-signup
register('root-signup', (render, rootElement) => {

  // Do something with root element
  const referer = rootElement.dataset.referer;
  render(<Signup referer={referer} />, () => {
    // Signup mounted or updated
    (...)
  });
});

const likeButtonHTMLCollection = document.getElementsByClassName('root-likebutton');

register(likeButtonHTMLCollection, (render, rootElement) => {
  const id = rootElement.dataset.id;
  render(<LikeButton id={id} />);
});
```

Or in component file like *HomeDropdown.js*
```javascript
import React, { Component } from 'react';
import register from 'react-register-dom';

class HomeDropdown extends Component {
  (...)
}

register('root-homedropdown', r => r(<HomeDropdown />));
```

**Pull request is welcomed ! :coffee:**
