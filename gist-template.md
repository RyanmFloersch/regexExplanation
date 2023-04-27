# Title (replace with your title)

Introductory paragraph (replace this with your text)


## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.
```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```
This regex is used to see if a string is a valid url. Explanations of the regex components can be found bellow. 



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
    Regex components are all different elements used to define the expression. Each component sets rules, boundaries, ranges and more to specifiy what the expression matches to.

### Anchors

Anchors are denoted with the characters ```^ ``` and ``` $```. 
```^``` is the anchor that signifies a string that begins with the characters that follow it. You can also think of it as signifiying the start of a string.  This can be in two formats: 
An exact string match denoted as such ```^The```. This is a case sensitive comparison where it would match for the string  "The dog" but not "the dog".
The other format is a range of possible matches using ```[]``` or bracket expressions. Anything inside the brackets represent a range of characters that we want to match. 

The ```$``` anchor signifies a string that ends with the characters that precede it. You can also think of it signifying the end of a string. Like ```^``` it can be preceeded by an exact string or a range using a ```[]``` expression. 
An example of this would be
```
/^[abc]/
```



### Quantifiers
Quantifiers are used to set the limits of string that the regex matches. It includes a minimum and maximum number of characters that the regex s looking for. Quanitfiers are considered ```greedy``` meany they will try to match as many occurences of a pattern as possible. 
Quntifiers include the following:
```*```- matches the pattern zero or more times
```+```- matches the pattern one or more times
```?```- matches the pattern zero or one time
```{}```- Curly brackets provide three different ways to set limits for a match: 
    - ```{n}``` -- matches the pattern exactly n number of times
    -```{n,}``` -- matches the pattern at least n number of times
    -```{n,x}```-- matches the pattern from a minimum of n number of times to a amaximum of x times. 

Some examples of quantifiers would look something like this:
```
/f{3}/ - Matches to any group of 3 f characters
/ba*ba/ - Matches to any string that starts with the b character has consequtives a characters that end with ba.     
```
### OR Operator

The OR operator provides the OR logic operator to tbe used within your regex expression by using the ```|``` character. Bracket expressions use OR operators behind the scenes but you can use the OR operator character to use it in other areas of the regex expression. The OR operator, ```|```, makes use of 2 arguments, one on both sides of the character. The expression will match if a string matches either argument. You can also make sue of the OR operator within group constructs as well.
</br>
An example of OR Operator:
```
(cat)|(hat)
```

### Character Classes
Within Regex you can deine a set of characters where if any occur within an input string it will match. Character classes are dennoted with the forward slash ```\``` followed by specific characters or a period (```.```) . For example ```\d``` matches to any numeric character. Capitalized letters after the slash typically represent the opposite like ```\D``` where it means any non numeric character. 
Some common ones are: 
```.``` - matches any character except the newline character
```\d ``` - matches any digit character
```\D``` - matches any non digit
```\w ``` - matches any alphanumeric character
```\ ``` - convert metacharcterts to literal characers.
</br>
An example of Character Classes:
```
\d 
And
. 
```

### Flags

Flags are conmponents that are placed at the end of a regex. They define an additional function or limite that the regex will follow. There are six different flags that can be used together or seperattly in any order. These flags are: 
```
/g - global search where the regex will be tested against all possible matchs of a string
/m - multiline search where an input string with multiple lines will be treated like it has multiple lines. ^ and $ anchors now match the beginning and end of each line respectivily instead of either the start or end of the whole string. 
/i - case sensitive search makes it so that case is ignored when matching. 
/x - ignore white space search makes it so it ignores white spaces and allow for comments in the regex also called verbose. Comments are indicated by a starting # character.
/s - single line search makes it so that the dot (.) character also is able to match newlines. The input string is also treated as a single line input. 
/u - unicode search makes it so pattern strings will be treated as UTF-16 which means unicode characters are included in bracket expression [a-z] ranges and in escape sequnces like \w.
```
```
/^a.*\D{4}$/m - a regex that starts with a and ends with 4 non digit characters.
```

### Grouping and Capturing
You can check specific parts of a string by using grouping. You can group by using ```()``` and the characters within the string are reffered to a subexpressions. You can have multiple subexpressions and have characters between them. Both groups need to match for the whole string to match. The characters between the groups also must be valid matches. ```()``` are also referred to as grouping constructs. Grouping constructs have to primary categories being capturing and non-capturing. Capturing construct captures a matched character sequences for use later use and non-capturing does not. 
</br>
Example of grouping:
```
(cat) in a (hat)
```


### Bracket Expressions

Bracket expressions are denoted using ```[]```. Bracket expressions represent a range of characters that we want to match to. 
An example of this is ```[abc]``` where it will look for a strign that has an ```a```, ```b```, or ```c``` character. So strings such as "bbb", "back", "bob", "cat", and "cba" would all match.  
With bracket expressions you can also make use of hyphens (```-```) between alhanumeric characters to denot a range of possible characters betweenthe two characters left and right of the hyphen. 
</br>
Example:
```
[4-6]
```

### Greedy and Lazy Match
A greedy match is the default way regex searches. The algorithm for greedy matching is For evrey position in the string, try to match the pattern at that positon, if there is no match go the next position. Greedy match can cause issues because they will try to match everything. Lazy match in comparissn is the oposit e of greedty where it means reapeat the minimum number of times. Lazy will try to match to the first match. 




### Boundaries

Word boundaries is denoted by ```\b``` and is an anchor like ^ and $. It matches a t a position that is called a word boundary.  word Boundaries can be used in 3 different positions:
-Before the first character in the string, if the first character is a word character.
</br>
-After the last character in the string, if the last character is a word character.
</br>
-Between two characters in the string, where one is a word charcter and the other is not a word character. 


There is also a non-word boundry denoted by ```\B```. 
</br>
Example of word boundaries: 
```
/a\b/
```

### Back-references
Back references match the same text as previously match by a capturing group. This allows you to store a part of a string to be used later in the expression. You can represent a captured group by doing  forward slash followed by a number like so ```\1```.

An exmample of backreferences: 
```
(a-z)x\1
```


### Look-ahead and Look-behind

Lookahead and Lookbehind assertion are zero-length assertions like start and end of line and start and end of word anchors. They are different from the others though as the lookaround actually matches charactres but then gives up thje match returning only if it matched or not. That is why they are called assertions. There is positive and negative lookahead. Negative look ahead is used if you want to match something not followed by something else. 

```
q(?!u) - Negative lookahead looks to match q not followed by u.
q(?=u) - Positive lookahead that looks to match a q that is followed by a u but not matching qu just q.
```




## Author
Ryan Floersch
</br>
Github: https://github.com/RyanmFloersch

