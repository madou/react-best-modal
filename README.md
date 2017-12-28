# react-simple-modal

Opinionated tiny API. No styling. Accessible. React 16 only.

## Usage

```sh
npm install styled-components focus-trap-react react-simple-modal --save
```

```javascript
import React from 'react';
import SimpleModal from 'react-simple-modal';
import { render } from 'react-dom';

const appRoot = document.getElementById('root');

const App = ({ showModal, closeModal }) => (
  <div>
    Hi Mom!
    {showModal && (
      <SimpleModal onRequestClose={closeModal} appRoot={appRoot}>
        <button>Hello, World!</button>
      </SimpleModal>
    )}
  </div>
);

render(<App />, appRoot);
```

**NOTE**: It is _required_ that you have an element inside your modal that is focusable. Essentially, any input or button.

## Styling

It's up to you to style and position your modal. `react-simple-modal` will only set a `className` on the body to disable scrolling when mounted.

### Transitions

`react-simple-modal` works perfectly with [`ReactTransitionGroup`](https://reactcommunity.org/react-transition-group/).

## Even. More. Accessible.

If you're driving home for the ultimate accessible modal, make sure to use `aria-labelledby` and `aria-describedby`, for title and description of the modal, like so:

```javascript
<SimpleModal
  onRequestClose={closeModal}
  appRoot={appRoot}
  aria-labelledby="modal-title"
  aria-describedby="modal-description"
>
  <h2 id="modal-title">Hello, World!</h2>
  <p id="modal-description">This is a modal, hello worlding!</p>
</SimpleModal>
```

## Focus

* Focus will be trapped inside the modal when mounted. You can't disable this.
* Focus will automatically jump to the modal's first element when mounted, and will return to the previous focused element when unmounted.

## Multiple modals (modals in modals)

This isn't supported. It's also bad practice to show many modals at a time.

## API

### `SimpleModal`

```javascript
import SimpleModal from 'react-simple-modal';
```

#### Props

| prop           | type        | required | description                                                                                     |
| -------------- | ----------- | -------- | ----------------------------------------------------------------------------------------------- |
| children       | ReactNode   | yes      | Your modal markup.                                                                              |
| onRequestClose | Function    | yes      | Callback when the modal wants to close. Up to you to action it.                                 |
| appRoot        | HTMLElement | yes      | Root of your application. The modal will add and remove accessible attributes when appropriate. |

All other props that are valid on a `HTMLElement` are passed through.
