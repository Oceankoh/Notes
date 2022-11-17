## Cheat Sheet

[https://www.rexegg.com/regex-quickstart.html](https://www.rexegg.com/regex-quickstart.html)

## Additional Notes for Clarification

|Expression| Explanation|
| ----------- | ---|
| `A(?=B)`|Find expression A where expression B follows|
|`A(?!B)`|Find expression A where expression B does not follow|
|`(?<=B)A`|Find expression A where B precedes|
|`(?<!B)A`|Find expression A where B does not precede|
|`\A`|Matches start of string. `^` is similar but matches start of line as well. Line is after `\n`|
|`(?:)`|Non capture group. Still matches whatever is in the colon, but is ot included in the resultant string. Match cannot be referenced as a capture group|
|`(?<name?)`|Name a capture group|
|`(?<protocol>http:\/\/\|ftp:\|https:\/\/).+` | Capture group named "protocol" matches "http://" or "ftp://" or "https://" and one or more characters that follow|
|`(?:(?<=http:\/\/)\|(?<=ftp:)\|(?<=https:\/\/)).+`| Matches everything after the protocol|




