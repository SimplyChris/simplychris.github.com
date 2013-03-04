---
layout: post
title: "Using Json.NET to deserialize JSON into anonymous objects"
date: 2013-03-03 12:50
comments: true
categories: [C#, .net]
---

The problem: Wanting to deserialize some simple JSON into an object without having to add a new type to your domain model. 

Turns out, Json.NET has a method that allows you to do just that. 

JsonConvert.DeserializeAnonymousType to the rescue. 

At first glance, the IntelliSense can be confusing and in reality is a bit misleading. 

{% img left /images/jsonconvert_anonymous_intellisense.png %}
Notice how it looks like the method is expecting a Type for the second parameter but in actuality all you need to do is pass in an instance of the anonymous type you create. Here is an example of usage.

```
var jsonString = "{color:\"red\",value:\"#f00\"}";
var htmlColor = new {color = "", value = ""};            
htmlColor = JsonConvert.DeserializeAnonymousType(jsonString, htmlColor);
```

