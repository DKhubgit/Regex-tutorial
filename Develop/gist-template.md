# Regular Expressions

As an aspiring web developer, you are probably here to get a quick understanding of what regular expressions are. Learning a new concept can be challenging, but this tutorial will help you learn about Regular Expressions, or in short **Regex**, in a concise and easy way. 

# Summary

This tutorial will cover the basics of regex and we will take it step by step. First off, what is a regular expression? Regular expressions are series of characters such as `"/^[a-z]/"` that helps us find and match patterns in certain strings like `"Hello World"`. This tutorial specifically will use the expression as an example
```
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
``` 
I know it's a lot, but this specific regex helps developers check whether a string is an email! Note, Regular expression are always contained within two 'slashes' like `/{some expression}/`. We will go over, step by step, on how to utilize this 'fascinating beast' to validate user emails. 

# What is the Anchor?

The first character in our example regex is what I call 'carrot' or `^`. What exactly does this character do? It checks/matches the at the start of the string, for example the 'H' in "Hello World" or the '1' in "1st place". Now this carrot is called an anchor character in regex. **Note**, the carrot also has a different meaning in a different context called 'negation'. Don't worry about it for now, let's look at the example only.

Another anchor character we see in our example is the money symbol `$`. This character is similar to the carrot but checks the end of the input instead, for example the 'd' in "Hello World" and the 'e' in "1st place". 

So how would we see it in actual code? This is how it would look.

```
const regex1 = /^H/   //Match 'H' at the first input of string
console.log(regex1.test("Hello World")) //output "true"

const regex2 = /e$/   //match 'e' at the end of the string
console.log(regex2.test("1st place")) //output "true"
```
These anchor characters positions the 'matching', or says 'hey, start checking at this position.'

<br>

# What is a Grouping and Capturing?

The next part of our example regex is called Grouping and Capturing, as the title suggests we will be grouping 'patterns' that we would like to match in our strings and capturing it. In our example:
```
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
we see after the carrot is the parentheses `()` and it encapsulates an expression. So in our example we have `([a-z0-9_\.-]+)`. Now the cool thing about this is that it groups the pattern AND captures anything that matches the pattern, meaning if we find a match in the string then it is stored in an array! Now we can access those matched words easily! Lets see it in code!
```
const regex = /^(hello)/  //find "hello" starting at the beginning
const string = "hello world"
const array = string.match(regex) //"match" is a string method
console.log(array)   //outputs array: ["hello", "hello"]
```
Pretty cool! Now we add 1 more functionality then just checking a string.  

<br>


# What are Character classes?

In our previous explanation we saw that within the parethesis (grouping) there was a series of alpha numeric and special characters enclosed in a bracket and the plus symbol(we will go over that symbol in another section). Now what do each of them mean?

```
[a-z0-9_\.-]
```
Now these are what are called character classes(denoted within brackets) and they are specific key characters we want to check/match for in a string. In this case the specific characters are:

- `a-z` : indicates the alphabet in lowercase ONLY
- `0-9` : indicates the numeric value from 0 to 9.
- `_` : this is the underscore symbol
- `\.` : this is the dot symbol. **
- `-`: this is the 'hyphen' or 'dash' symbol

** Note: the `\` or the 'backslash' symbol is call the 'escape' character. Use this when we want to use the ACTUAL symbol rather than the syntax/literal. For instance, `/^(user\/downloads)/` will match in the string for `user/downloads`. If we hadn't use the escape character then it would terminate the expression at `/^(user/` and it would result in an error (which is no bueno for us). 

So what does this mean? It means that `[a-z0-9_\.-]` is matching for **ONE** character that is either a letter, number, underscore, dot, or hyphen. Let's see and example in code!
```
//starting at the beginning, find any word that satifies pattern
const regex = /^([a-z0-9_\.-])/ 
const string = "hello world"
const array = string.match(regex) //"match" is a string method
console.log(array)   //outputs array: ["h", "h"]
```
**NOTE**: The space is also a character that can be added to the character class. So, for example, `[ a-z0-9_\.-]` (the space is at the beginning), will check for spaces. Also note that the dash symbol at the end is specifically searching for that symbol, if it was between two characters then it's trying to match something else. 

Now you are probably wondering, what if we want to check through all the strings and not for one? The answer IS?... It's in the next section.

<br>

# What are Quantifiers?

Quantifiers help finds/checks the 'quantity' of a certain character. Basically, how many times does one character occur in a certain string? We use quantifiers to find out! Remember the plus symbol? That is a quantifier that will be explained right now. 

The plus symbol `+` denotes 1 or more occurances. For example, "Hello World" has one occurance of "h" and two occurance of "l". So the plus symbol, really, matches something and checks for how many times we see that same letter in the same string. Lets get coding!
```
//matches any character within the class
//PLUS checks for more than one occurance of that character 
const regex = /^([a-z0-9_\.-]+)/
const string = "hello world"
const array = string.match(regex)
console.log(array)  //outputs array: ['hello', 'hello']
```
**NOTE**: The `+` is essentially `{1, }` which denotes 1 to infinite occurances. If we add a number at the end like `{1,5}` then it denotes 1 or 5 occurances.

<br>

# What are Word Boundaries?

Last component we will go over are the word boundaries. What are they? They are specific 'boundaries' denoted by `\{some letter}`. Here are some examples of word boundaries:

- `\b` (denotes the position of a boundary)
- `\d` (denotes the character class "[0-9]")
- `\w` (denotes the character class "[A-Za-z0-9_]")

In the regex example we are using
```
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
we have a word boundary `\d` which denotes the numeric values from 0-9. Basically another way to simplify our character classes. There are other word boundaries that have their respective character classes. 

# Let's Analyze!

Finally, we have all the components covered and now we will break down how our example regex works!
```
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

As stated in the beginning, this regex checks strings whether or not they are an email. Most often is used during signing up or registering a user credentials, validates whether the email or username is an actual email. 

Lets break it down into smaller parts!

1.  The slash `/` denotes that we are defining a regular expression.
2. The carrot `^` states to start a match at the beginning of the string.
3.  The expression `([a-z0-9_\.-]+)` specifies which characters to match and to look for more than one occurance. Also stores the matched value.
4. The `@` symbol is the next character to match following the previous expression.
5. The expression `([\da-z\.-]+)` specifies the same as #3 but uses a word boundary `\d` to denote numeric values, finds more than 1 occurance of the character. This also stores the match value.
6. The `\.` denotes an escaped character to actually match for the dot symbol rather than another regex syntax.
7. The `([a-z\.]{2,6})$` states to look at the end of the string to match for a word that has letters and dots. The `{2,6}` restricts the number of occurances of 2 or 6. Meaning only 2 characters to only 6 characters within the character class `[a-z\.]`. This also stores the match value.
8. Lastly, the regular expression is finally defined with the closing slash `/`.

<br>

Here is a screenshot of it's usage using [playcode.io](https://playcode.io/javascript/). Remember, whatever is in parenthesis in the regex that matches in the string is stored in the array. We can see which part of the regex matches the value. 

![Picture of regex code](/Develop/images/regex-screenshot.PNG)

<br>

## Author

Daniel Kang - [Github](https://github.com/DKhubgit)
