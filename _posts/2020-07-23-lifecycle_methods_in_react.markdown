---
layout: post
title:      "Lifecycle Methods in React"
date:       2020-07-23 21:13:10 +0000
permalink:  lifecycle_methods_in_react
---

"ReactJs is a JavaScript Library to build user interface" 

**What is a User Interface? **

The user can interact with app, clicking, pressing keys or executing one of many events from the components. Every component is 'born' in the browser and will die at some time. All the interface is handled by a'God', that is the User.

The User Interface is like a playground with many options where one can do whatever they want and, libraries like React help us build the playground. 

**What are Lifecycle Methods and why are they so important?**

Look around us, everything goes through a cycle in life, birth, growth, and at some point, death. Consider a tree, any software application, yourself, a comonent in the UI, all of them, have their creation/birth, growth/update, and then death... 

Lifecycle Methods of a component are invoked at different times of a component life. Lets pretend we are creating Youtube, we know that our app will use the network to buffer the videos and will use energy from the battery. If the user changes to another app after watching the video, we as good developers, need to make sure that we are using resources efficiently, so we need to stop buffering the video to save the user some data and some battery.

This is what Lifecycle methods in React bring to the table so developers can create an application with quality, and to make sure that developers can really plan what and how to make a change in different moments in the life of a component, being on the Mounting, updating or unmounting of the interface.

**The 4 stages of a React Component**

A React component, like everything around is, goes through these stages.

* Initialization
* Mouting
* Updating
* Unmounting


To see a better implementation of Lifecycle methods, we will build a React App of a music player called MyMusic Player. Let's start talking about these stages. 

*** Initialization**
In this stage, the React Component gets ready for its initialization, setting initial states, default prop, if there are any.
The initialization of our App looks like this:

```
class MyMusicPlayer extends React.Component
constructor(props) {
  super(props);
  this.state = {
    volume: 70,
    status: 'pause'
  }
}
MyMusicPlayer.defaultProps = {
  theme: 'dark'
};
```

The component is setting its initial state on the constructor method, this can be change after using the setState()
The defaultProps is a function of the component to set all its default values of its properties. and can be replaced by new values after.

When rendering with <MyMusicPlayer/>, the player will set the volume to 70%, will be paused and with a dark theme. 
When you render like this <MyMusicPlayer theme='light'/> the player will set volume to 70%, will be paused and the theme will be set to light.


*** Mounting**

After setting up all the basics like states and props, our component is ready to be mounted on the DOM. This stage give us a lot of methods that can be invoked before and after the component has been mounted. These methods are:

* componentWillMount: Is invoked when a component is about to be mounted in the DOM. after this method is invoked the component will be mounted. Everythign that you want to do before mounting the component, need to be defined here. This method is executed one time in the lifecycle of a component. 
Use: componentWillMount is used to intialized states or props, there is a bit dilme about to merge this with constructor. 

* render, mounts the component on the DOM. This is a pure method this means that it will return the same thing even with different inputs. 

The render method for our music player can look like this: 

```
render() {
  <div>
     <PlayHeader>
       <Status/>
       <VolumeBar/>
       <SeekBar/>
    </PlayHeader>
   </div>
}
```

* componentDidMount: This method is invoked after the component is mounted to the DOM. This method is invoked once on the lifecycle of the component. With this method we can access the DOM.
Use: In our music app, we want to draw the grafics of sound waves from the whole music, this is the right place to integrade to D3 library and other 3rd party librarys. 
The example bellow show the HighCharts settings when the DOM is ready.

```
componentDidMount() {
 if (this.props.modules) {
            this.props.modules.forEach(function (module) {
                module(Highcharts);
            });
        }
        // Set container which the chart should render to.
        this.chart = new Highcharts[this.props.type || "Chart"](
            this.props.container, 
            this.props.options
        );
}
```

**ALL API REQUEST NEEDS TO BE MADE ON componentDidMount**


* **Updating**

This stage starts when the React component is already in the browser, and it will grow receiving updates. The component can be updated in two ways, by sending receiving props or updating the state.

Lets see the list of methods availble when we update the state is updated using seState: 

1. shouldComponentUpdate: it tells react that, when the component receives new props os states, the reacts needs to re-render or ignore the rendering of that component. This method is a questions like: 'Has this component been updated?' So this method returns a boolean value, so the component is re rendered or ignored. By default the method returns true. 

Use: The explame below is one case that I wanted to re-render the component when the the status of the props changed.

```
shouldComponentUpdate(nextProps, nextState) {
  let shouldUpdate = this.props.status !== nextProps.status;
  return shouldUpdate;
}
```

This method is commonly used when the rendering is a very heavy method, so you want to avoid rendering that component. Lets say that for each render, the component generates a thousand prime numbers, considering an app that has this kind of logic, we can control the render for only when its necessary. 

2. componentWillUpdate: is invoked only when shouldComponentUpdate returns true. This method is used only to prepare the next rendering, similar to componentWillMount and constructor. There can be a time where you will need to do some calculation ou preparation to render something, this is a good place to do it. 

3. render(): Here the component is rendered on the screen.

4. componentDidUpdate: This is invoked when the new component(already updated) has been updated on the DOM. This method is used to reactivate all 3rd party libraries, used to make sure that the libraries update and reload as well.

The list of methods that will be called on the parent component sends to the child component is: 
* componentWillReceiveProps: is invoked when the props changed and are still not processed for the first time. Sometimes the state depends on props, so everytime the props change the state can be synchronized. This is the method where this has to be done.

This way you can keep the state synchronized with props. 

```
componentWillReceiveProps(nextProps) {
  if (this.props.status !== nextProps.status) {
    this.setState({
      status: nextProps.status
    });
  }
}
```

The rest of the methods behaves exactly the same way defined above. in term of state as well. 
* componentUpdate()
* componentWillUpdate()
* render()
* componentDidUpdate()



* **UNMOUNT**

In this stage the component is no longer necessary and will be dismounted.

* componentWillUnmount: this method is the last method in the lifecycle. This is invoked just before the component is removed from the DOM.

Use: this method,we can do all the limitations related to the component. On Logout all the user details and tokens can be deleted before dismount the main component. 

```
componentWillUnmount() {
  this.chart.destroy();
  this.resetLocalStorage();
  this.clearSession();
}
```















