# Tutorial: Regex matching Hex value

WHat are regular expressiona you may ask? They are patterns that are used to match character combinations in strings. In a regular expression the metacharacter ^ means "not". The "a" means "match lowercase a", "^a" means "do not match lowercase a".

## Summary
 I will be covering and breaking down the components of a regular expression used to match Hex Values. Hexadecimal code is a system by which by any specific color can be described to a computer, ensuring consistency and accuracy in an electronic display. A hexadecimal color value is a six-digit code preceded by a # sign; it can defines a color that is used in a computer program.
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

## Table of Contents

- [Anchors](#Anchors)
- [Quantifiers](#Quantifiers)
- [OR Operator](#Or-operator)
- [Character Classes](#Character-classes)
- [Bracket Expressions](#Bracket-expressions)
- [Greedy and Lazy Match](#Greedy-and-lazy-match)

## Regex Components

### Anchors

/`^`#?([a-f0-9]{6}|[a-f0-9]{3})`$`/  
Anchors are so much different. They do not match any characters. They match a position either before or after or either inbetween characters. They can be used to anchor the regex match at a certain position. The caret `^` matches the position before the first character in the string. Applying `^a` to `abc` matches `a`. `^b` does not match `abc` at all, because the `b` cannot be matched right after the start of the string, matched by `^`. See below for the inside view of the regex engine.
Similarly, `$` matches right after the last character in the string. `c$` matches `c` in `abc`, while `a$` does not match at all.

### Quantifiers

/^#`?`([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/   
Quantifiers are used to communicate the amount of characters that are expected. Quantifiers specify how many instances of a character, group, or character class must be thier in the input for a match to be found. By default, quantifiers are greedy, and will match as many characters as possible. If the "`,+,?,{}`" characters are found within regular expressions, they are considered quantifiers. The `?` indicates the expression to match `0` or `1`time. As I mentioned in the summary above  their are 2 formats I will use the or operator to distinguish which format I am using. In our Hex Value regular expression we have `{6}` (Hex Triplet Format) and `{3}` (Shorthand Hex Format), this indicates that the length of the component preceding these quantifiers should be `6` for `{6}` and `3` for `{3}`.

### OR Operator

/^#?([a-f0-9]{6}`|`[a-f0-9]{3})$/  
The "or" operator within a regular expression is defined using the `|` element. The or operator indicates that it could either of the components that we are separating with the `|`. For our hex value regular expression we have `([a-f0-9]{6}``|``[a-f0-9]{3})`. Note the or operator separating these 2 components. This means that our hex value could either be 6 characters `[a-f0-9]{6}` or 3 characters `[a-f0-9]{3}`.

### Character Classes

/^#?(`[a-f0-9]`{6}|`[a-f0-9]{3}`)$/  
Character classes are the components within our regular expression that tells us what type of characters to know in the future. For an example our character classes are confined within brackets `[]`. An example that we have are 2 character classes: `[a-f0-9]` and `[a-f0-9]` which seems to have the same values. I will be breaking down what the characters are searching within these character classes. `a-f` searches for letters `a-f` and `0-9` searches for digits `0-9`.

### Bracket Expressions

/^#?`([a-f0-9]{6}|[a-f0-9]{3})`$/  
Matches any character in the square brackets. For example 	`[nN]` `[oO]` matches `no`, `nO`, `No`, and `NO`.
`gr[ae]y` matches both spellings of the word `'grey'`; that is, `gray` and `grey`.

### Greedy and Lazy Match

/^#`?`([a-f0-9]{6}|[a-f0-9]{3})$/  
A greedy match tries to match any element as many times as possible. Whereas, a lazy match tries to match an element as few times as possible. In our example we have `?` which signifies lazy quantifier. This is referred to a lazy quantifier because it causes the regular expression engine to match as few occurances as possible. We can simply turn this lazy match into a greedy one by adding a `?`.

## Author

Hi I'm Jacob Levine, I'm a full-stack developer student looking to be sucessfull!  
GitHub: [Jake-Levine](https://github.com/jjakelevine3500)
