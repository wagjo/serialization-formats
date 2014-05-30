# Data serialization formats

Comparison of selected data serialization formats

## Null

 | JSON | EDN | CLJ
-----|-----|-----|----
null literal | `null` | `nil` | `nil`

## Booleans

 | JSON | EDN | CLJ
-----|-----|-----|----
true literal | `true` | `true` | `true`
false literal | `false` | `false` | `false`

## Characters

 | JSON | EDN | CLJ
-----|-----|-----|----
syntax | NONE :x: | `\X` | `\X`
special characters | NO :x: | `\newline` `\tab` `\return` `\space` | `\newline` `\tab` `\return` `\space` `\backspace` `\formfeed` 
unicode escapes | NO :x: | `\uNNNN` | `\uNNNN`
octal escapes | NO :x: | NO :x: | `\o0` to `\o377`

## Strings

 | JSON | EDN | CLJ
-----|-----|-----|----
syntax | wrapped in `"` | wrapped in `"` | wrapped in `"` 
may span multiple lines | NO :x: | YES | YES
characters which must be escaped | `"` `\` and control characters (U+0000 to U+001F) | `"` `\` | `"` `\`
escape characters | `\"` `\\` `\/` `\b` `\f` `\n` `\r` `\t` | `\"` `\\` `\n` `\r` `\t` | `\"` `\\` `\'` `\b` `\f` `\n` `\r` `\t` 
unicode escapes | `\uNNNN` | NO, not mentioned in specs :x: | `\uNNNN`
octal escapes | NO :x: | NO :x: | `\0` to `\377`
