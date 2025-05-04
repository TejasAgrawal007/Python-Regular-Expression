Here are some commonly asked **Python Regular Expression (regex)** questions along with their **answers**. These cover basics to intermediate concepts:

---

### 1. **What is a regular expression in Python?**

**Answer:**
A regular expression (regex) is a sequence of characters used to match patterns in strings. Python provides the `re` module to work with regular expressions.

---

### 2. **How do you import and use regex in Python?**

**Answer:**

```python
import re
pattern = r'\d+'           # matches one or more digits
text = 'My phone number is 12345'
match = re.findall(pattern, text)
print(match)               # Output: ['12345']
```

---

### 3. **What does the `re.match()` function do?**

**Answer:**
It checks for a match **only at the beginning** of the string.

```python
import re
result = re.match(r'Hello', 'Hello world')
print(result.group())       # Output: Hello
```

---

### 4. **Difference between `re.match()` and `re.search()`?**

**Answer:**

* `re.match()` matches from the start of the string.
* `re.search()` scans through the entire string.

```python
re.match(r'world', 'Hello world')  # Returns None
re.search(r'world', 'Hello world') # Returns Match object
```

---

### 5. **How does `re.findall()` work?**

**Answer:**
It returns a list of all matches in the string.

```python
re.findall(r'\d+', '123 and 456')  # Output: ['123', '456']
```

---

### 6. **What does `^` and `$` represent in regex?**

**Answer:**

* `^` matches the start of the string.
* `$` matches the end of the string.

```python
re.findall(r'^Hello', 'Hello world')  # ['Hello']
re.findall(r'world$', 'Hello world')  # ['world']
```

---

### 7. **Write a regex to extract all email addresses from a string.**

**Answer:**

```python
text = "Emails: test@example.com and hello123@domain.co"
emails = re.findall(r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}', text)
print(emails)  # ['test@example.com', 'hello123@domain.co']
```

---

### 8. **How to replace all whitespace with a hyphen using regex?**

**Answer:**

```python
text = "Replace all spaces with dash"
new_text = re.sub(r'\s+', '-', text)
print(new_text)  # Replace-all-spaces-with-dash
```

---

### 9. **What does `\d`, `\w`, and `\s` mean in regex?**

**Answer:**

* `\d`: any digit (0–9)
* `\w`: any word character (a-z, A-Z, 0–9, \_)
* `\s`: any whitespace (space, tab, newline)

---

### 10. **How to validate a phone number (e.g., 10 digits)?**

**Answer:**

```python
number = "9876543210"
is_valid = re.fullmatch(r'\d{10}', number)
print(bool(is_valid))  # True
```

---

Would you like questions with increasing difficulty or ones tailored for interviews?
