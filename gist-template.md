# # RejexSummary

A brief look into what Regex (regular expressions) are and how they work. 

## Summary

Regex (short for regular expression) is a string of text that allows you to create search patterns that match, manage, and locate text. An example code snippet of regex shows as following:
```
/[\w._%+-]+@[\w.-]+\.[a-zA-z]{2,4}/
```
* A regular expression used to match an e-mail address

Regular expressions can also be used from the command line and within text-editors to find text within a file. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

Anchors are characters within the regular expression that allow the user to match strings that begin with or ends with (or both) certain characters. 

Examples of Anchors are as follows:

* `^` - matches any string that start with the anterior word
* `$` - matches a string that end with preceeding word before the character
* Examples:
```
^Oliver          matches any string starting with `Oliver`
Car$          matches any string ending with `Car`
^New Car$   matches exact string
usedcar         matches any string that has the exact text `usedcar` in it
```

### Quantifiers

Qunatifiers are characters within the regular expression that specify how many instances a character, group, or character class must be represented in the input to be matched.

Examples of Quanitifers are as follows:

* `*` - matches a string that has the anterior followed by zero or more of the last character
* `+` - matches a string that has the anterior followed by one or more of the last character
* `?` - matches a string that has the atnerior follwoed by zero or one of the last character
* `{}` -  matches a string that has the anterior followed by how ever many the number in the brackets of the last character in the string
* `()*` - matches a string that has any anterior characters followed by zero or more copies of the string within the brackets
* Examples:
```
abc*        matches a string that has ab followed by zero or more c
abc+        matches a string that has ab followed by one or more c
abc?        matches a string that has ab followed by zero or one c
abc{4}      matches a string that has ab followed by 4 c
abc{4,}     matches a string that has ab followed by 4 or more c
abc{4,8}    matches a string that has ab followed by 4 up to 8 c
a(bc)*      matches a string that has a followed by zero or more copies of the sequence bc
a(bc){4,8}  matches a string that has a followed by 4 up to 8 copies of the sequence bc
```
### Grouping Constructs

Grouping unifies a pattern or string so that it is matched in a complete block

Examples of Grouping are as follows:
* `()` - parentheses creates a capture group
* `(?:)` - using `?:` disables the capturing group
* `(?<>)` - using `?<>` puts a name to the group
* Examples:
```
x(yz)           parentheses create a capturing group with value yz
x(?:yz)*        using ?: we disable the capturing group
x(?<bar>yz)     using ?<bar> we put a name to the group
```

### Bracket Expressions

Bracket Expressions are characters enclosed by a bracket `[]` matching any single character within the brackets. 
*note: if the first character within the brackets is a `^` then it signifies any chracter **not** in the list, and is unspecified whether it matches an encoding error. 

Examples of Bracket Expressions are as follows: 
* `[]` - matching any single character within the brackets
* `[]%` - matching the string inside the brackets before the `%`
* `[^]` - matching any string that has not a letter from within the brackets (negation of expression)
* Examples:
```
[xyz]         matches a string that etiher has x or x y or x z (same as x|y|z)
[x-y]         similar to case above
[u-zU-Z0-9]   a string that represents a single hexadecimal digit, case insensitively
[0-9]%        a string that has a character from 0-9 before a %
[^a-zA-Z]     a string that has not a letter from a to z or from A to Z
```

### Character Classes

Character Classes (Character Set) tells the regex engine to match only one out serveral specific characters, such as digits, words, or whitespace

Examples of Character Classes are as follows:

* `\d` - matches a single character that is a digit
* `\w` - matches a word character (any alphanumeric character plus underscore)
* `\s` - matches a whitespace character (including tabs and line brakes)
* `.` - matches any character
* the capital case for any aformentioned characters will inverse the match
* Examples:
```
\d    matches a single any digit 0-9
\w    matches a single any character that is a-z
\s    matches ` `
.     matches any character
\D    matches a single non-digit character
\W    matches a single any non-character that is a-z
\S    matches a single non-` `
```

### The OR Operator

OR Operators (Alternation Operator) matches on of a choice of regular expressions: if you put the character(s) representing the alternation operator between any two characters in the regular expression, the result matches the union of the strings that those two characters match.

Examples of OR Operators are as follows:

* `(|)` - matches a string that has any anterior characters followed by the characters on the left or right of the vertical bar
* `[]` - matches a string that has any anterior characters without any characters within the brackets
* Examples: 
```
a(b|c)  matches a string that has a followed by b or c (and captures b or c)
a[bc]   matches a string that has a, but without capturing b or c
```
### Flags

Flags are optional parameters that we can add to a plain expression to make it search in a different way. Each flag is denoted by a single alphabetic character, and serves different purposes in modifying the expression's searching behavior.

Examples of Flags are as follows:
* `g` - Global, does not return after the first match, which restarted any subsequest searches from the end of the previous match (Makes the expression search for all occurences)
* `m` - Multi-line, when enabled the Anchors (^ $) will match the start and end of a line, rather than the whole string
* `i` - Insensitive, makes the entire expression case-insensitive
* Examples:
```
/Hello/g   matches all `Hello` in the test
/Hello/m   matches the beginning and ending of each line with `Hello`, rather than the whole string `Hello` itself
/Hello/i   matches all `hello` despite case (Hello, hEllo, heLlo, hellO, hello, HELLO all match)
```

### Character Escapes

The backslash (\)  in a regular expression precedes a literal character. You also escape certain letters that represent common character classes, such as \w for a word character or \s for a space. The following example matches word characters (alphanumeric and underscores) and spaces.

```
Char 	         Description 	                                          Meaning
"\" 	          Backslash 	                               Used to escape a special character
"^" 	            Caret 	                                     Beginning of a string
"$" 	         Dollar sign 	                                    End of a string
"." 	        Period or dot 	                            Matches any single character
"|"     	Vertical bar or pipe symbol 	              Matches previous OR next character/group
"?"            Question mark 	                            Match zero or one of the previous
"*" 	        Asterisk or star 	                        Match zero, one or more of the previous
"+"	            Plus sign                             	Match one or more of the previous
"( )" 	Opening and closing parenthesis 	                      Group characters
"[ ]" 	Opening and closing square bracket 	                Matches a range of characters
"{ }" 	Opening and closing curly brace 	      Matches a specified number of occurrences of the previous

```
## Author

Alan is a Junior Developer towards the end of his coding bootcamp at UCI

Feel free to check out his GitHub repo for all of his previous projects

[GitHub Profile](https://github.com/alntruong)

[GitHub Gist Link](https://gist.github.com/alntruong/23c59874e9be5ead3a2c3077b350f956)
