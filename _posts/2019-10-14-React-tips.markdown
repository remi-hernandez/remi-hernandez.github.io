---
layout: post
title:  "React tips "
date:   2019-10-14 16:39:53 +0000
categories: dev javascript react
---

## Redux
The core parts of redux is the store, it holds a single state tree.The store lets you read the state, dispatch actions to update the state, subscribe and unsubscribe for updates to that state, that's about it.
This store is passed around your application. If you're using React, you're probably passing your store to react-redux's <Provider /> component, which lets you access it in other parts of your application by wrapping your component with connect().

### Reducer
A Redux reducer is a function that accepts the current state and an action, and returns the next state (the state after an action has happened). 

### Basic reimplem of redux to understant his logic
{% highlight javascript %}
function createStore(initialReducer, initialState = {}, enhancer) {
  if (enhancer) {
    return enhancer(createStore)(initialReducer, initialState);
  }
  let reducer = initialReducer;
  let subscribers = [];
  let state = reducer(initialState, { type: '__INIT__' });
  return {
    getState() {
      return state;
    },
    dispatch(action) {
      state = reducer(state, action);
      subscribers.forEach(subscriber => subscriber(state));
    },
    subscribe(listener) {
      subscribers.push(listener);
      return () => {
        subscribers = subscribers.filter(subscriber => subscriber !== listener);
      };
    },
    replaceReducer(newReducer) {
      reducer = newReducer;
      this.dispatch({ type: '__REPLACE__' });
    }
  };
}
{% endhighlight %}
###
original post : https://dev.to/selbekk/redux-in-27-lines-2i92?utm_source=additional_box&utm_medium=internal&utm_campaign=regular&booster_org=
