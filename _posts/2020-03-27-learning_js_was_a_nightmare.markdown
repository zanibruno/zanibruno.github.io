---
layout: post
title:      "Learning JS was a nightmare, and how I did it!"
date:       2020-03-27 10:03:10 -0400
permalink:  learning_js_was_a_nightmare
---


This has been the most difficult part of the program so far for me!

All the concepts, syntaxes was a bit tricky for me to get the grip to it. But by far the hardest part, is the organization of a JavaScript project. 

Learning Ruby and Ruby on Rails before hand, has been very beneficial. But at the other hand, a bit of a bad move, because in Rails, everything has its onwn place, if it is not in the correct place and with the correct name, it will not work. Javascript on the other hand, at least on my head, is a very unnorganized Language, classes can be together on the same file, variables declared after calling them, functions without name, arrow functions, functions that are assigned to variables and so on. 

And after speaking with a few of my colleagues from my cohort, i came to the conclusion that i will use file called adapters to take care of my fetch requests, and components to take care of my logic for each class. 

The trickies thing after coming from rails... Is that JavaScript does not come with Implicit returns, so I caught myself a LOOOOOT trying to debug something, looking everywhere, to figure it out that I was only missing the return on my fetch or something similar.

```getTrips() {
        fetch('http://www.localhost:3000/trips')
				.then(res => res.json())
				}
				```
				
		This code will kinda do what I want it to do. But if i am planning on using the Promise of this fetch, somewhere else, i will not be able. because JavaScript will not return the value of the Promise. For this I will have to use the 'return' keyword just before my fetch request.
		
		I was not understanding the flow of Javascript very well. So i restarted my mind with one day off, and went back to the studies, with something in my head that helped me a lot, The Three Pilars of JS(Listen to event, Manipulate the DOM, Display to the user).
		
		With this in my head I managed to understand Javascript a lot better than before. But there is still a looooot to learn.
		
		So lets say we want to get the user to tell us his name through a simple form.
		
		Lets suppose we already have a form created on the HTML file. 
		
		the first step will be to find the form and assign a eventListener to it. 
		
		`const formName = document.getElementById('form-name')`
		
		the second step will be to listen to any event that is happening on that form, such as a submit button being clicked. 
		
		`this.formName.addEventListeners('submit' , this.renderName.bind(this))`
		
		the third step would be to get the function to display the name of the user.
		
		`renderName(e) {
	     e.preventDefault()
			 const value = e.target.parentElement.value
			 console.log(value)
			 }`
			 
			 and with this 3 steps we are able to display some data to our console that has been inputed by the user on our form. 
			 
			 
			 
			 
		}
		
	
		
	
		
		
		
	





