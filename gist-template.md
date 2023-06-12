# RegEx Tutorial

RegEx are sequences of characters that come together to form a search pattern for text(strings). Hex values, emails, IP, dates, even usernames can be paired with RegExs. This tutorial is aimed to better help you under RegEx (regular expressions). 
If you don't know what a hex code is, look into it, it'll be helpful in understanding this tutorial.

## Summary

We will examine the a RegEx expression that matches hex values, as seen below. It'll match any hexidemical code in a string of characters when searched.

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`


## Table of Contents

- [Delimiters](#delimiters)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Delimiters

We open and close our expression with delimiters. `/` is used in our example, but can be different depending on what language you use, feel free to google them.

### Anchors

Anchors are the beginning and end of the RegEx. Here we are using `^` at the beginning and `$` to close it.

If we were searching our table of contents, we'd start with `^Anchors` and end it with `^Character Escapes`.

In our RegEx code above though, we can clearly see we're starting with `^#`, so when we search a string, the first thing we search for is the character `#`.

### Quantifiers

Next we have our quantifiers, in our express we use two, `?` and `{n}`.

`?` looks for matching character zero or one time. As we saw earlier, `#` came right after our anchor and is what we search for first, so this quantifier will search for `#` zero or one time when searching a string.

You'll see there are two uses of `{n}`, `{6}` and then `{3}`, for now just know they're both searching for what is before them. In both cases they're searching for `[a-f0-9]` 6 or 3 times.

### Grouping Constructs

Group constructs allow us to search in large group. `(<group>)`. 

`([a-z])` would search for a to z in the alphabet. `([0-9])` would search for numbers 0 to 9.

For now, lets break the expression in two at the `|`.

`([a-f0-9]){6}` which searches for the group of `([a-f0-9])` 6 times using the quantifier

`([a-f0-9]{3})` which searches for the group of `([a-f0-9])` 3 times using the quantifier

### Bracket Expressions

I've been saying we are searching for `[a-f0-9]`, but what is that?

`[]` characters within these brackets limit our search. 

In our brackets we have `a-f0-9`, what is it searching? `a-f` tell us to search between "a - f" in the alphabet, `0-9` tells us to search numbers between "1 - 9"

With this together, we know we are searching for any letter between a and f, and any number between 1 and 9. Put this together with the quanifier we learned about and we know the following.

* `([a-f0-9]){6}` we're searching for `{6}` characters that can be between `a-f` and/or a number `1-9` 
* `([a-f0-9]{3})` we're searching for `{3}` characters that can be between `a-f` and/or a number `1-9`

### Character Classes

Character classes are usually what is inside of the bracket expression. You can use things like `^` to modified the searhc more if needed.

Something like `[abc123]` will search for a, b, c, 1, 2, or 3.

In our case we have something that searches for a range using `-`. `a-f`, and `1-9`

In another RegEx you might use `a-z` which would search all the letters or `1-5` to only search for 1, 2, 3, 4, or 5.

### The OR Operator

Remember breaking the gruop apart in the grouping constructs? This is how we bring them our bracket expressions together in a single group.

Using `|` we can search for THIS or THAT. `a|b` THIS `a` or THAT `b`. Another example would be `hamburgers|hotdogs`, hamburgers or hotdogs.

So in ours we're searching for the same thing though? Well that is where the quantifier changes it. 

We are searching THIS `([a-f0-9]){6}` or THAT `([a-f0-9]){3}`. So either a 6 char string or a 3 char string, the same character classes, but different size strings.

### Flags

Flags special characters that change how a RegEx searches and are usually put on the end after the `/` delimiter at the end of the expression. Sadly we don't have any...

An example of one would be `/i` which allows you to be case-insensitive. i.e. `A` and `a` would both match in `a/i`. Doesn't matter if it is upper or lower case, the RegEx will find it.

Look into other RegEx to see examples but here is a full list of jscript flags:

* `i`
* `g`
* `m`
* `s`
* `u`
* `y`

### Character Escapes

Character escapes are wild, and again we sadly don't use them here. Something like the email matching RegEx might better help you understand them.

They allow use to search for specific LITERAL characters. 

Example: `([a-z123\-])`

We search `a-z`, `1`, `2`, `3`, then hit the character escape and search `-`. Without the `\` there may be issue searching for the `-`.

## Author

My name is Luc Martin, I am tired. Here is my github for this https://github.com/offbrandcat/regextutorial