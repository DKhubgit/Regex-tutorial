# Regular Expressions

As an aspiring web developer, you are probably here to get a quick understanding of what regular expressions are. Learning a new concept can be challenging, but this tutorial will help you learn about Regular Expressions, or in short **Regex**, in a concise and easy way. 

# Summary

This tutorial will cover the basics of regex and we will take it step by step. First off, what is a regular expression? Regular expressions are series of characters such as `/^[a-z]/` that helps us find and match patterns in certain strings like `"Hello World"`. This tutorial specifically will use the expression as an example
```
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
``` 
I know it's a lot, but this specific regex helps developers check whether a string is an email! We will go over, step by step, on how to utilize this 'fascinating beast' to validate user emails. 


