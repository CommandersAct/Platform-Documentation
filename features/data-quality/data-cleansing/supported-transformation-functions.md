# Supported transformation functions





| FUNCTION NAME                            | WHAT IT DOES                                                                                                                                                    |
| ---------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| EXTRACT(text, delimiter, position)       | Extracts from the given text the substring at the given position, after splitting by the given delimiter. (_Example_: EXTRACT('a\_b\_c', '\_', 1) returns 'b'.) |
| SUBSTITUTE(text, old\_text, new\_text)   | Substitutes newText for oldText in a text string. Use SUBSTITUTE when you want to replace specific text in a text string.                                       |
| REPLACE(sourceStr, pattern)              | Replaces every match of pattern (a regex expression) in sourceStr. (_Example_: REPLACE('The-Clone-Wars', '-') would return 'The Clone Wars'.)                   |
| SHA256(stringToHash)                     | Returns an SHA256 hash of the given string                                                                                                                      |
| MD5(stringToHash)                        | Returns an MD5 hash of the given string                                                                                                                         |
| COALESCE(value1, value2, ...)            | Returns the first value from the list that isn’t empty                                                                                                          |
| TRIM(text)                               | Removes all spaces from the text except for single spaces between words                                                                                         |
| SELECT(sourceStr, pattern)               | Selects the first match of the pattern(a regex expression) in the sourceStr. (_Example_: SELECT('From A to Z alphabet', 'A(.\*?)Z') would return 'A to Z')      |
| LOWER(text)                              | Converts all uppercase letters in a text string to lowercase                                                                                                    |
| UPPER(text)                              | Converts all lowercase letters in a text string to uppercase                                                                                                    |
| NUMBER(value1)                           | Converts string to number                                                                                                                                       |
| ENCODE\_BASE64(value1)                   | Encode a string to base64                                                                                                                                       |
| DECODE\_BASE64(value1)                   | Decode a string from base64                                                                                                                                     |
| TODAY()                                  | Returns the current system date                                                                                                                                 |
| TIMESTAMP()                              | Returns the current timestamp date                                                                                                                              |
| LEFT()                                   | Returns the requested number of characters from the left                                                                                                        |
| RIGHT()                                  | Returns the requested number of characters from the right                                                                                                       |
| CHAR()                                   | Returns the character specified by a number                                                                                                                     |
| IF(condition,resultIfTrue,resultIfFalse) | Returns the second argument if the first argument is true, and third argument if otherwise                                                                      |
| ISEMPTY(value)                           | Returns whether the value is empty or not                                                                                                                       |
| AND(condition1, condition2)              | Logical AND, checks to see that both conditions are true                                                                                                        |
| OR(condition1, condition2)               | Logical OR, Checks to see if either one of the conditions is true                                                                                               |
| NOT(condition)                           | Logical NOT, reverses the logic of its argument, true becomes false and vice versa                                                                              |
