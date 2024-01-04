# Regular Expression Tutorial

This tutorial explains what a Regular Expression, or regex for short, is. A regex is a series of characters that together define a pattern that needs to match a user input. These expressions are universal and can be used by any programming language, although there may be some differences among the way characters work or what they represent. In this tutorial we will focus on JavaScript.

## Summary

In this tutorial we will explain a regex for a passcode.
`/^[a-zA-Z0-9~!@#$%^&*()_-=]{7,21}$/`
In this example, the password chosen by the user can be formed by upper and lowercase letters, numbers from 0 to 9, and the following symbols: ~!@#$%^&*()_-=. The password must also contain between 7 and 21 characters.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Character Escapes](#character-escapes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)

## Regex Components
Regular expressions are composed of a series of characters, made of numbers, letters and symbols. Each one of the characters either by itself or in conjunction with others can mean something different within the regex. However, every regex begins and ends with a backslash(/), as shown in our example.
`/^[a-zA-Z0-9~!@#$%^&*()_-=]{7,21}$/`
In order to better understand the characters that compone a regex, we can divide them into categories.

### Anchors
There are two characters that represent anchors: the caret ‘^’, and the dollar sign ‘$’. Anchors ensure that the regex matches the characters that come after the ‘^’ and before the ‘$’. These characters could appear as a string, where they would match the exact input (yes, it is case sensitive) or as a possibilities of matches, which happens when the bracket expressions are used. In our example we are using the second option, but we will explain that in more detail later.
`^[a-zA-Z0-9~!@#$%^&*()_-=]`

### Quantifiers

Quantifiers specify how many instances of a character or group must appear in the inputted string for the regex to match it. Most frequently, the quantifier will set the minimum and maximum number of characters allowed, as shown in our example: 
`{7,21}`
This means that the password must contain between 7 and 21 characters. But there are other characters that form a quantifier. Those are: 

'*' matches the pattern zero or more times
'+' matches the pattern one or more times
'?' matches the pattern zero or one time
'{ n }' matches the patterns exactly 'n' times
'{ n ,}' matches at least 'n' times
'{ n , m }' matches from 'n' to 'm' times. 

It's important to take into consideration that adding a question mark after the curly brackets ‘{}’ makes the quantifier lazy, meaning that it will cause the regex to match the least amount of occurrences possible.

### Grouping Constructs

Grouping Constructs are used to specify a subexpression inside the regular expression, and to simplify them as they may grow larger and more complicated. One of the most used examples are parentheses. If in our example we would like to match either uppercase letters and lowercase letters, we could do it as follows: (a-z):(A-Z).
It's important to highlight that subexpressions look for exact matches, which is why if the uppercase appeared before lowercase letters, it would not match.

### Bracket Expressions

Bracket expressions are defined by square brackets ‘[]’, and they represent a range of characters to match. For example, if we want to match any letter in the entire alphabet, we can use bracket expressions to easily include them all by adding a hyphen between the letters. Then this expression [a-z] will try to match the same characters as [abcdefghijklmnopqrstuvwxyz]. The same happens with numbers, if we add [0-9] to our expression, it will try to match any numbers between 0 and 9. It may also match symbols like [!@#$%^&*()] used for example in password, just like our example.
Something to be cautious about when creating regex, is that, again, they are case sensitive. Therefore, if we would like to also add uppercase letters, we would need to add [A-Z] to our expression.
`^[a-zA-Z0-9~!@#$%^&*()_-=]`
In our example, we chose for the user to be able to use lower and uppercase letters, numbers from 0 to 9 and the following symbols ~!@#$%^&*()_-=.

### Character Classes

Character classes consist of a set of characters that can appear in a string to be matched by the regex. In other words, they are the characters located within the square brackets as we covered in the bracket expressions. But there are other common character classes: 

'.' matches any character except for the newline character (\n)
'\d' matches any number between 0 and 9 
'\w' matches any alphanumeric character from the basic Latin alphabet, including the underscore symbol, meaning that its equivalent is the bracket expression [a-zA-Z0-9_]
'\s' matches a single whitespace character, including tabs and line breaks.

### Character Escapes

A character escape is a symbol that allows the regex to omit interpreting a character. This symbol is a backslash '\', and it tells the regex engine to not interpret a character literally. For example, if we add a backslash in front of a curly bracket, otherwise used as a quantifier, the regex engine will look for the open curly bracket character in the input.

### The OR Operator

The OR operator allows a regex to match two different options in the string. This is how our example would appear if we added OR operators: 
`[a-z|A-Z|0-9|~!@#$%^&*()_-=]`.
This means that the regex is looking to match lowercase letters OR uppercase letters OR numbers OR symbols, since they don't need to match every single component.
Another example to understand better this operator would be:
^Some colors that go well together are (olive|light brown) and (white)$. In this case, we are saying that white goes well with either olive or light brown, but olive and light brown do not. Therefore, the regex will try to match a string that contains either the word light brown or the word olive.

### Flags
Even though most of the time regex will end with a backslash, there are some cases where flags come into play. Flags add extra functionality to the regex, and there are 6 of them available in JavaScript, but the most popular ones are: 'g', that adds a global search, 'i', that adds case insensitivity, and 'm', that adds a multi-line search. This is how our example would look like if adding a flag:
`/^[a-zA-Z0-9~!@#$%^&*()_-=]{7,21}$/g`

## Author
Irina Meroi, Web Development student at UCLA Bootcamps. If you want to find more of my work, please visit my GitHub page: https://github.com/irimeroi.
