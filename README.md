# Data serialization formats

Comparison of selected data serialization formats

## Whitespace

 | JSON | EDN | CLJ
-----|-----|-----|----
whitespace character | U+0009 (tab) U+000A (newline) U+000D (return) and U+0020 (space) | :warning: specs does not specify whitespace chars, explicitly mentions just `,` | :warning: specs does not specify whitespace chars, explicitly mentions just `,`
delimiters | whitespaces | whitespaces and `[` `]` `{` `}` `(` `)` | :warning: no explicit mention in specs

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

## Integers

 | JSON | EDN | CLJ
-----|-----|-----|----
arbitrary precision indicator | NO :x: | `N` suffix | `N` suffix
valid signs | `-` | `-` `+` |  `-` `+`
`-0` is valid | YES | YES | YES
decimal integer | YES | YES | YES
custom radix | NO :x: | NO :x: | `NrNNNNN`
hexa integer | NO :x: | NO :x: | `0xNNNNN`, but undocumented :warning:
octal integer | NO :x: | NO :x: | `0NNN`, but undocumented :warning:

## Non-integral numbers

 | JSON | EDN | CLJ
-----|-----|-----|----
ratios | NO :x: | NO :x: | `NN/NN`
decimals | NO :x: | `M` suffix | `M` suffix 
floating points | YES | YES | YES
valid signs | `-` | `-` `+` |  `-` `+`

## Identifiers

 | JSON | EDN | CLJ
-----|-----|-----|----
symbols | NO :x: | YES | YES
symbol start character | *n/a* | alphabetic, `+` `-` `.` followed by non-numeric symbol character, `*` `!` `_` `?` `$` `%` `&` `=` `<` `>` | XXX
symbol character | *n/a* | alphanumeric, `+` `-` `.` `*` `!` `_` `?` `$` `%` `&` `=` `<` `>` `:` `#` `/` | XXX
special symbol character  | *n/a* | `/`, used alone or in following combinations `foo//` `foo/bar`. First character after slash must follow rule for symbol start character | `/`, used alone or in following combinations `foo/bar` `foo//` 
keyword | NO :x: | prefixed with `:` | prefixed with `:`
keyword character | *n/a* | alphanumeric, `+` `-` `.` `*` `!` `_` `?` `$` `%` `&` `=` `<` `>` `:` `#` `/` | XXX
keyword invalid second character | *n/a* | `:` `/`
special keyword character  | *n/a* | `/`, used in following combinations `:foo//` `:foo/bar`. First character after slash must follow rule for symbol start character | `/`, used in following combinations `:foo/bar` `:foo//` 

## Collections

 | JSON | EDN | CLJ
-----|-----|-----|----
list | NO :x: | `(a b c)`| `(a b c)`
vector | `[a, b, c]` | `[a b c]`| `[a b c]`
set | NO :x: | `#{a b c}` items are unique | `#{a b c}` items are unique 
map | `{string1 : val1, string2 : val2]` | `{key1 val1 key2 val2}` keys are unique | `{key1 val1 key2 val2}` keys are unique

## Special
 | JSON | EDN | CLJ
-----|-----|-----|----
comments | NO :x: | `;` till the end of the line | `;` till the end of the line
discard | NO :x: | `#_` discards next read object | `#_` discards next read object
