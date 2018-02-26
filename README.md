# Lua-OOP-modules
Sample which shows classes and subclass inheritance using different modules. 

There are many lua examples of OOP as coded in a single module.  In this example I will show how to accomplish this using various separate modules. 

Usage: 
In your main module you will need the following:  
The following defines the separate modules to your main module. 

local baseclass = require "baseclass"  -- this is the base class on top of which all subclasses are built. 
local subclass = require "subclass"  -- first subclass
local subsubclass = require "subsubclass"  -- second subclass

Since baseclass stands alone, you could start using functions from this module immediately. 
S1inst = baseclass:new()
S1inst:classname()
Output:  baseclass: classname function 

However, the subclasses only contain a fraction of the functions available from the base.  So you will need to inherit all the functions from the base to build the sublass.  
local S2class = subclass:inheritsFrom(baseclass)
Now we have an S2class that contains all the functions from baseclass plus whatever is in subclass.  Note that if the function names are the same the subclass function is then classed.  

You can build on your newly created S2class and build a subsubclass.  
local S3class = subsubclass:inheritsFrom(S2class)

We now have our classes so let's start using them.  First create instance of the class by classing the new function. 

local S2inst = S2class:new()
local S3inst = S3class:new()

S2inst:classname() 

Output:  sub:  classname

S2inst:classname2() 

Output: baseclass: classname function  -- note subclass didn't have a function called classname2 so the function located in baseclass is used.  
S3inst:classname() 

Output:  subsub: classname 
S3inst:classname2() 

Output: baseclass: classname function  -- note subclass nor subsubclass have a function called classname2 so the function located in baseclass is used.

Using these simple modules an OOP inheritence may be implemented. 
