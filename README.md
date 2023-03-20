# Regex Tutorial (Regex Tutorial)

In this tutorial, we will be taking a brief look into what Regex (regular expressions) are and how they work. While regular expressions may seem to be overwhelming at first glance,
just like with any language, they can be broken down into its most simple parts and easily understood.

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
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
In regular expressions, an anchor is a character that defines a specific position within the search string. Anchors allow you to match patterns that occur at the beginning or end of a line, word, or string, or at a specific position within the string. 

Examples of Anchors:

    ^ - Matches the beginning of a line or string.
    $ - Matches the end of a line or string.
    \b - Matches a word boundary.
    \B - Matches a position that is not a word boundary.
    \A - Matches the beginning of a string, but not the beginning of a line.
    \Z - Matches the end of a string, or the end of a line if there is one.
    \z - Matches the end of a string.


* Examples:
```
To match a string that starts with "hello": ^hello
To match a string that ends with "world": world$
To match a word that starts with "cat": \bcat
To match a string that contains "dog" but not at the beginning of a word: \Bdog
To match a string that starts with "hello" but not at the beginning of a line: \Ahello
To match a string that ends with "world" or the end of a line: world\Z
To match a string that ends with "world" but not followed by any characters: world\z
```

### Quantifiers
In regular expressions, quantifiers are characters or symbols that specify how many times a particular character, group, or character class should be repeated. Here are some common quantifiers in regex:



Examples of Quanitifers are as follows:

* Matches zero or more occurrences of the preceding character or group.
* Matches one or more occurrences of the preceding character or group.
* ? - Matches zero or one occurrence of the preceding character or group.
* {n} - Matches exactly n occurrences of the preceding character or group.
* {n,} - Matches n or more occurrences of the preceding character or group.
* {n,m} - Matches at least n and at most m occurrences of the preceding character or group.

* Examples:
```
    To match any number of characters that start with "a": a*
    To match one or more digits: \d+
    To match a string that may or may not contain the word "apple": apple?
    To match exactly three occurrences of the letter "b": b{3}
    To match two or more occurrences of the string "abc": abc{2,}
    To match between 2 and 5 occurrences of the letter "x": x{2,5}
```

### OR Operator
In regular expressions, the OR operator is represented by the pipe character | and allows you to match one of several possible patterns.

Examples of OR Operators are as follows:

    To match either "cat" or "dog": cat|dog
    To match either "apple", "banana", or "orange": apple|banana|orange
    To match either "hello world" or "hi there": hello world|hi there
    To match either "Mr." or "Ms." followed by a name: (Mr\.|Ms\.)\s[A-Z][a-z]+

    In the last example, the backslash is used to escape the period character, which has a special meaning in regex as it matches any single character. By *  * escaping the period with a backslash, we are indicating that we want to match the literal period character.


* Examples: 
```
x(y|z)  matches a string that has x followed by y or z (and captures y or z)
x[yz]   matches a string that has x, but without capturing b or c
```




### Character Classes
In the context of regular expressions, a character class is a set of characters enclosed within square brackets. It specifies the characters that will successfully match a single character from a given input string.



Examples of Character Classes are as follows:

[abc] 	a, b, or c (simple class)
[^abc] 	Any character except a, b, or c (negation)
[a-zA-Z] 	a through z, or A through Z, inclusive (range)
[a-d[m-p]] 	a through d, or m through p: [a-dm-p] (union)
[a-z&&[def]] 	d, e, or f (intersection)
[a-z&&[^bc]] 	a through z, except for b and c: [ad-z] (subtraction)
[a-z&&[^m-p]] 	a through z, and not m through p: [a-lq-z] (subtraction


* Examples:
```
\d    Matches any digit (Arabic numeral). Equivalent to [0-9]. For example, /\d/ or /[0-9]/ matches "2" in "B2 is the suite number". 
\w     Matches any alphanumeric character from the basic Latin alphabet, including the underscore. Equivalent to [A-Za-z0-9_]. For example, /\w/ matches "a" in "apple", "5" in "$5.28", "3" in "3D" and "m" in "Émanuel". 
\s    matches ` `
.     matches any character
\D    Matches any character that is not a digit (Arabic numeral). Equivalent to [^0-9]. For example, /\D/ or /[^0-9]/ matches "B" in "B2 is the suite number". 
\W    Matches any alphanumeric character from the basic Latin alphabet, including the underscore. Equivalent to [A-Za-z0-9_]. For example, /\w/ matches "a" in "apple", "5" in "$5.28", "3" in "3D" and "m" in "Émanuel". 

\S   Matches a single character other than white space. Equivalent to [^\f\n\r\t\v\u0020\u00a0\u1680\u2000-\u200a\u2028\u2029\u202f\u205f\u3000\ufeff]. For example, /\S\w*/ matches "foo" in "foo bar". 
```



### Flags
A regular expression consists of a pattern and optional flags: g , i , m , u , s , y . Without flags and special symbols (that we'll study later), the search by a regexp is the same as a substring search. The method str. match(regexp) looks for matches: all of them if there's g flag, otherwise, only the first one.

Examples of Flags are as follows:

* i
    With this flag the search is case-insensitive: no difference between A and a (see the example below).
* g
    With this flag the search looks for all matches, without it – only the first match is returned.
* m
    Multiline mode (covered in the chapter Multiline mode of anchors ^ $, flag "m").
* s
    Enables “dotall” mode, that allows a dot . to match newline character \n (covered in the chapter Character classes).
* u
    Enables full Unicode support. The flag enables correct processing of surrogate pairs. More about that in the chapter Unicode: flag "u" and class \p{...}.
* y
    “Sticky” mode: searching at the exact position in the text (covered in the chapter Sticky flag "y", searching at position) 

* Examples:
```
/Hello/g   matches all `Hello` in the test
/Hello/m   matches the beginning and ending of each line with `Hello`, rather than the whole string `Hello` itself
/Hello/i   matches all `hello` despite case (Hello, hEllo, heLlo, hellO, hello, HELLO all match)
```

### Character Escapes 

An escape character may not have its own meaning, so all escape sequences are of two or more characters.

Escape characters are part of the syntax for many programming languages, data formats, and communication protocols. For a given alphabet an escape character's purpose is to start character sequences (so named escape sequences), which have to be interpreted differently from the same characters occurring without the prefixed escape character. 

```
JavaScript uses the \ (backslash) as an escape character for:[1][2]

    \' single quote
    \" double quote
    \\ backslash
    \n new line
    \r carriage return
    \t tab
    \b backspace
    \f form feed
    \v vertical tab (Internet Explorer 9 and older treats '\v as 'v instead of a vertical tab ('\x0B). If cross-browser compatibility is a concern, use \x0B instead of \v.)
    \0 null character (U+0000 NULL) (only if the next character is not a decimal digit; else it is an octal escape sequence)
    \xFF character represented by the hexadecimal byte "FF"

Note that the \v and \0 escapes are not allowed in JSON strings. 
```

### AUTHOR 
https://github.com/AustinMcClarren
