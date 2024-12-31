+++
title = 'Intro to Regex in Python'
date = 2024-12-31
draft = false
tags = ['Python', 'Regex']
categories = ['computer science', 'python']
[cover]
    image = 'Regex.jpg'
    alt = 'This is a post image'
    caption = 'This is the caption'

[editPost]
    URL = "https://github.com/link/content"
    Text = "Suggest changes on this repository!!" 
    appendFilePath = true 

+++

**A Beginner's Guide to Regular Expressions in Python**

### What Are Regular Expressions?

Regular expressions, often abbreviated as **regex** or **regexp**, are patterns used to match sequences of characters in text. They are powerful tools for searching, extracting, and manipulating strings based on specific patterns. In Python, the `re` library is used to work with regular expressions, offering a range of functions to simplify text processing.

### When to Use Regular Expressions

You should consider using regular expressions when:

- Searching for specific patterns in text (e.g., finding all dates in a document).
- Validating input formats (e.g., ensuring an email address is correctly formatted).
- Replacing or reformatting parts of text (e.g., converting snake_case to camelCase).
- Extracting data from unstructured text (e.g., pulling phone numbers from a webpage).

However, regular expressions can be overkill for simple string operations. If basic string methods like `.find()`, `.replace()`, or `.startswith()` suffice, stick with those for better readability and performance.

### Common Regular Expressions Used in Real Life

Here are some commonly used regex patterns:

### 1. Validating an Email Address

```
import re
email_pattern = r'^[\w.%+-]+@[\w.-]+\.[a-zA-Z]{2,}$'
email = "test@example.com"
if re.match(email_pattern, email):
    print("Valid email!")
else:
    print("Invalid email!")
```

Explanation:

- `^` and `$`: Ensure the pattern matches the entire string.
- `[\w.%+-]`: Matches allowed characters in the username.
- `@`: Literal "@" symbol.
- `[\w.-]`: Matches allowed characters in the domain name.
- `\.[a-zA-Z]{2,}`: Matches a dot followed by at least two letters.

### 2. Finding All Phone Numbers

```
text = "Call me at 123-456-7890 or 987.654.3210."
phone_pattern = r'\b\d{3}[-.]\d{3}[-.]\d{4}\b'
print(re.findall(phone_pattern, text))
```

Output: `['123-456-7890', '987.654.3210']`

### 3. Removing Extra Spaces

```
text = "This   is   a   test."
print(re.sub(r'\s+', ' ', text))
```

Output: `"This is a test."`

### Rules for Creating Regular Expressions

1. **Special Characters**: Regex includes special characters like `.`, , `+`, `?`, `^`, `$`, `[ ]`, `( )`, `{ }`, and `|`. To match these literally, escape them with a backslash (`\`).
2. **Character Classes**:
    - `\d`: Matches any digit (0-9).
    - `\w`: Matches any word character (a-z, A-Z, 0-9, _)
    - `\s`: Matches any whitespace (spaces, tabs, newlines).
    - `[abc]`: Matches any one of the characters `a`, `b`, or `c`.
3. **Quantifiers**:
    - : Matches 0 or more occurrences.
    - `+`: Matches 1 or more occurrences.
    - `?`: Matches 0 or 1 occurrence.
    - `{n}`: Matches exactly `n` occurrences.
    - `{n,}`: Matches `n` or more occurrences.
    - `{n,m}`: Matches between `n` and `m` occurrences.
4. **Anchors**:
    - `^`: Matches the beginning of a string.
    - `$`: Matches the end of a string.
    - `\b`: Matches a word boundary.
5. **Groups and Alternation**:
    - `( )`: Groups patterns together.
    - `|`: Acts as an OR operator.

### Sample Problem: Validating and Extracting Dates

### Problem:

Write a Python function that validates a date in the format `YYYY-MM-DD` and extracts the year, month, and day if valid.

### Solution:

```
import re

def validate_and_extract_date(date):
    date_pattern = r'^(\d{4})-(\d{2})-(\d{2})$'
    match = re.match(date_pattern, date)
    if match:
        year, month, day = match.groups()
        print(f"Valid date! Year: {year}, Month: {month}, Day: {day}")
    else:
        print("Invalid date format.")

validate_and_extract_date("2024-12-31")
validate_and_extract_date("31-12-2024")
```

**Output:**

```
Valid date! Year: 2024, Month: 12, Day: 31
Invalid date format.
```

### Conclusion

Regular expressions are a versatile tool for text processing and validation in Python. By mastering the `re` library and understanding regex syntax, you can handle complex string operations efficiently. Just remember to use regex sparingly and not see it as a hammer sees nail scenario —simpler methods are often more readable for straightforward tasks.