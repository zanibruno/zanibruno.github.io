---
layout: post
title:      "Lifecycle, approaching visually"
date:       2020-02-27 16:54:52 +0000
permalink:  lifecycle_approaching_visually
---


When I learned Object Oriented Ruby, it was magical, but terrifying at the same time. Things were happening in the background and I did not know what was going on ... 

Then, after practicing for a little bit, it clicked, and I started to think of Object Lifecycle as the lifecycle of something in the real world. This something, gets created, its shown to the public, gets updated, gets destroyed, we can ask for someone to find it for us by giving some details, and it goes kidna like this...

```Class Something < ApplicationRecord

def new 
    @something = Something.new
end 

def create
@something = Something.new(details)
@something.save
end

def update 
@something = Something.find_by(details: params[:details])
@something.update
end 

def show 
@something = Something.find_by(details: params[:details])
end 


end```

There are many more things we can do with this something. We can call validations on it, so it is only created and added to our database it is passes all the criterias we set into our models ... 

Callbacks 

The Callbacks are methods that can be called o a specific time on the Object Lifefycle. In the example below you can see the Callback method before_save being used. 

```Class Something < ApplicationRecord 

before_save :lowercase_name 

def lowecase_name
self.name = name.downcase.titleize
end 

end ```

This callback will be run after our validation and before saving the object to our database, it will make sure that the name of that @something, is lowercase and with only the first letter of every word Capitalized(tears of the sun => Tears Of The Sun).

Object Lifecycle is something amazing, and it is really important to know how it works and it will make your life much easier, RubyGuides has some great documentation on Lifecycles, explaining everything that I mentioned in here but in more details. 


