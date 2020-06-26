---
layout: post
title:      "Redux blew my mind... "
date:       2020-06-26 13:40:03 +0000
permalink:  redux_blew_my_mind
---


I had big problem learning JavaScript, I just could not get the grasp of all theses reponses and promises. But in the end I got it haha. 

When Redux came in the picture at the last part of the program. It completely put me off my pace, I could not understand a single thing. What is reducers? Actions ? what about eventListeners and fetch requests that i just worked so hard to understand from Vanilla Javascript ?


So here we go again!

What is Thunk ? 

```
function someFuntion() {
       // do something
return function otherFunction() {
      // do something later
    }
}
```

It is kinda like a function that calls another function and then ... Wait .. What? 
So basically one function returns another function that has some new commands and data to be executed in later stage. Is that right ? 


What is Redux ? 
It is some very deep thing that goes way beyond explanation for me... I think of it like a place that store all the states for the application, and that every component has its own space inside it, and when the state of the component changes, it creates a new instance of that store, because the store is immutable.

Actions ?

```
{type: ACTION, payload: {} }
```

They look like the do something, but they dont, they're plain JS objects with a type and some payload.

Action Creators ?

```
const SOME_ACTION = "SOME_ACTION";

function create_action(data) {
    return {
        type: SOME_ACTION,
        payload: data
    }
}
```

Yeah they do just what you expect them to do. They create new action objects, and then you can dispatch them to the reducers using dispatch(create_action(data))

Reducers ?

```
function someReducer(state, action) {
    switch(action.type) {
        case SOME_ACTION:
            return {
                ...state,
                data: action.payload
            }

        default:
            return state;
    }
}
```

I dont know why they're called this, because it makes no sense to me. From what I know, reducers are just plain functions that receive the state and the action as an argument. Then they do something with it, and return the new state. Unless you're using Thunk, oh yes, Thunk again... Its pretty simple to understand, it will look at every action being dispatched and if that action is calling a function that it will run that function

More on that on the next post!






