+++
title = 'Firstblogpost'
date = 2024-12-09T03:07:07-05:00
draft = false
tags = ['HTML', 'CSS']
categories = ['tech']

[cover]
    image = 'hugoimage.png'
    alt = 'This is a post image'
    caption = 'This is the caption'

[editPost]
    URL = "https://github.com/link/content"
    Text = "Suggest changes on this repository!!" 
    appendFilePath = true 

+++


---

### Basic Regex Characters

| **Pattern** | **Description** | **Example** |  |
| --- | --- | --- | --- |
| `.` | Any character except newline | `a.b` matches `acb`, `aXb` |  |
| `\d` | Any digit (0-9) | `\d\d` matches `42` |  |
| `\D` | Any non-digit | `\D` matches `a`, `X` |  |
| `\w` | Any word character (a-z, A-Z, 0-9, _) | `\w\w\w` matches `abc` |  |
| `\W` | Any non-word character | `\W` matches `@`, `#`, |  |
| `\s` | Any whitespace (spaces, tabs, newlines) | `\s\s` matches 2 spaces |  |
| `\S` | Any non-whitespace | `\S\S` matches `ab` |  |
| `^` | Start of a string | `^a` matches `abc` but not `bac` |  |
| `$` | End of a string | `b$` matches `cab` |  |
| `\b` | Word boundary | `\bword\b` matches `word` but not `swordfish` |  |
| `\B` | Not a word boundary | `\Bfoo` matches `foobar` but not `foo bar` |  |

### Quantifiers

| **Pattern** | **Description** | **Example** |
| --- | --- | --- |
| `*` | 0 or more occurrences | `a*` matches `a`, `aa`, or empty |
| `+` | 1 or more occurrences | `a+` matches `a`, `aa` |
| `?` | 0 or 1 occurrence (optional) | `colou?r` matches `color`, `colour` |
| `{n}` | Exactly n occurrences | `\d{4}` matches `1999` |
| `{n,}` | n or more occurrences | `\d{2,}` matches `42`, `4242` |
| `{n,m}` | Between n and m occurrences | `\d{2,5}` matches `42`, `12345` |

### Character Classes & Ranges

| **Pattern** | **Description** | **Example** |
| --- | --- | --- |
| `[abc]` | Matches any of `a`, `b`, or `c` | `[aeiou]` matches any vowel |
| `[^abc]` | Matches any character except `a`, `b`, or `c` | `[^aeiou]` matches consonants |
| `[a-z]` | Matches any lowercase letter | `[a-z]` matches `a`, `b`, ... `z` |
| `[A-Z]` | Matches any uppercase letter | `[A-Z]` matches `A`, `B`, ... `Z` |
| `[0-9]` | Matches any digit | `[0-9]` matches `1`, `2`, ... `9` |
| `[a-zA-Z0-9]` | Matches alphanumeric characters | Combines letters and digits |

Groups and Alternation

| **Pattern** | **Description** | **Example** |
| --- | --- | --- |
| `(abc)` | Captures group `abc` | `(foo)` matches `foo` |
| `(?:abc)` | Non-capturing group | `(?:foo)` matches `foo` but doesn't store it |
| ` | ` | Alternation (or) |

### Special Characters

| **Pattern** | **Description** | **Example** |
| --- | --- | --- |
| `\` | Escape special character | `\.` matches `.` |
| `\n` | Newline | Matches newline |
| `\t` | Tab | Matches tab |

### Anchors

| **Pattern** | **Description** | **Example** |
| --- | --- | --- |
| `^` | Start of string | `^a` matches `a` at the start of string |
| `$` | End of string | `a$` matches `a` at the end of string |

### Lookahead and Lookbehind

| **Pattern** | **Description** | **Example** |
| --- | --- | --- |
| `(?=...)` | Positive lookahead (asserts what follows) | `\d(?=abc)` matches `1` in `1abc` |
| `(?!...)` | Negative lookahead (asserts what doesn’t follow) | `a(?!b)` matches `a` not followed by `b` |
| `(?<=...)` | Positive lookbehind (asserts what precedes) | `(?<=\$)\d+` matches digits following a `$` |
| `(?<!...)` | Negative lookbehind (asserts what doesn’t precede) | `(?<!\$)\d+` matches digits not preceded by a `$` |

### Example Patterns

- **Email**: `\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b`
- **URL**: `(https?:\/\/(www\.)?)[\w\-]+(\.[\w\-]+)+[/#?]?.*$`
- **Phone Number**: `\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}`
- **Date (MM/DD/YYYY)**: `\b(0[1-9]|1[0-2])/(0[1-9]|[12][0-9]|3[01])/([0-9]{4})\b`