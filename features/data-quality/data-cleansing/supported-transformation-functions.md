# Supported transformation functions

In the formula input, you can can write basic or complex expression to transform the data.\
\
Expressions are composed of either a value, a function, an operation, or another expression in parenthesis. See below for the description of each one of them.

{% hint style="info" %}
Functions can be nested, ex: `SHA256(LOWER(user.email))`
{% endhint %}

## Available functions

| FUNCTION NAME                            | WHAT IT DOES                                                                                                                                                                                                                                      |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| EXTRACT(text, delimiter, position)       | Extracts from the given text the substring at the given position, after splitting by the given delimiter. (_Example_: EXTRACT('a\_b\_c', '\_', 1) returns 'b'.)                                                                                   |
| SUBSTITUTE(text, old\_text, new\_text)   | Substitutes newText for oldText in a text string. Use SUBSTITUTE when you want to replace specific text in a text string.                                                                                                                         |
| REPLACE(sourceStr, pattern, replaceStr)  | Replaces every match of pattern (a regex expression) in sourceStr. (_Example_: REPLACE('The-Clone-Wars', '-', ' ') would return 'The Clone Wars'.)                                                                                                |
| SHA256(stringToHash)                     | Returns an SHA256 hash of the given string                                                                                                                                                                                                        |
| MD5(stringToHash)                        | Returns an MD5 hash of the given string                                                                                                                                                                                                           |
| COALESCE(value1, value2, ...)            | Returns the first value from the list that isn’t empty                                                                                                                                                                                            |
| TRIM(text)                               | Removes all spaces from the text except for single spaces between words                                                                                                                                                                           |
| SELECT(sourceStr, pattern, \<position>)  | <p>Selects the first match of the pattern(a regex expression) in the sourceStr. (<em>Example</em>: SELECT('From A to Z alphabet', 'A(.*?)Z') would return 'A to Z')<br>If the third parameter is set, it will return the corresponding match </p> |
| LOWER(text)                              | Converts all uppercase letters in a text string to lowercase                                                                                                                                                                                      |
| UPPER(text)                              | Converts all lowercase letters in a text string to uppercase                                                                                                                                                                                      |
| NUMBER(value1)                           | Converts string to number                                                                                                                                                                                                                         |
| ENCODE\_BASE64(value1)                   | Encode a string to base64                                                                                                                                                                                                                         |
| DECODE\_BASE64(value1)                   | Decode a string from base64                                                                                                                                                                                                                       |
| ~~TODAY()~~                              | Returns the current system date                                                                                                                                                                                                                   |
| TIMESTAMP()                              | Returns the current timestamp date                                                                                                                                                                                                                |
| LEFT()                                   | Returns the requested number of characters from the left                                                                                                                                                                                          |
| RIGHT()                                  | Returns the requested number of characters from the right                                                                                                                                                                                         |
| CHAR()                                   | Returns the character specified by a number                                                                                                                                                                                                       |
| IF(condition,resultIfTrue,resultIfFalse) | Returns the second argument if the first argument is true, and third argument if otherwise                                                                                                                                                        |
| ISEMPTY(value)                           | Returns whether the value is empty or not                                                                                                                                                                                                         |
| NOT(condition)                           | Logical NOT, reverses the logic of its argument, true becomes false and vice versa                                                                                                                                                                |

## Operators

| **Operator**                            | **Description**                                                                                                                                                                                                     |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AND or &&                               | Do a boolean AND between the two parts                                                                                                                                                                              |
| OR or \|\|                              | Do a boolean OR between the two parts                                                                                                                                                                               |
| NOT()                                   | Do a boolean NOT on the expression                                                                                                                                                                                  |
| =, ==, or IN                            | <p>Return true if the left part is equal to the right part<br>If one of the part is an array, check if some values are in equal between the two parts</p>                                                           |
| !=, <>, or !IN                          | Inverse of the above                                                                                                                                                                                                |
| <, >, <=, or >=                         | <p>Compare two values<br>If one of the values is an array, check that at least one of the value match.</p>                                                                                                          |
| BETWEEN()                               | Check if the left value is between the two values passed as arguments.If the left value is an array, check that at least one of the value match.                                                                    |
| \~ or !\~                               | <p>Check if the left value match the regex in the right value (or doesn’t match if !~). The regex language is the javascript one.<br>If the left value is an array, check that at least one of the value match.</p> |
| STARTSWITH(), ENDSWITH(), or CONTAINS() | <p>Check if the left value starts with, ends with, or contains the right value.<br>If the left value is an array, check that at least one of the value match.</p>                                                   |
| \* or /                                 | Multiplication or division                                                                                                                                                                                          |
| + or -                                  | Addition / concatenation or substraction                                                                                                                                                                            |

## Examples

Scenario 1: Create a Flag that shows if Consumers’ Primary Address is in California\
`IF(EXTRACT(city_state, '-', 1) == " CA", "TRUE", "FALSE")`

``
