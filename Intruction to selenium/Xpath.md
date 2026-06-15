# XPath Notes

---

# What is XPath?

XPath (XML Path Language) is used to locate elements in XML and HTML documents.

| Feature | Description |
|-----------|-------------|
| Full Form | XML Path Language |
| Used For | Locating elements in XML and HTML |
| Commonly Used In | Selenium, Web Scraping, XML Processing |
| Supports | Attributes, Text, Axes, Functions |

---

# Types of XPath

| Type | Syntax | Example |
|--------|---------|---------|
| Absolute XPath | Starts from root | `/html/body/div/input` |
| Relative XPath | Starts anywhere | `//input` |

### Comparison

| Absolute XPath | Relative XPath |
|---------------|---------------|
| Starts from root node | Starts from anywhere |
| Long and complex | Short and readable |
| Easily breaks | More stable |
| Not recommended | Highly recommended |

---

# Basic Syntax

| Expression | Meaning |
|------------|---------|
| `//tagname` | Select all elements with that tag |
| `/` | Direct child |
| `//` | Descendant |
| `.` | Current node |
| `..` | Parent node |

### Examples

| XPath | Selects |
|---------|---------|
| `//input` | All input elements |
| `//button` | All buttons |
| `//a` | All anchor tags |

---


# Important XPath Concepts in Selenium

| Concept | Description | Syntax | Example | When to Use |
|-----------|-------------|---------|---------|-------------|
| Attribute | Attributes are properties of HTML elements such as `id`, `name`, `class`, `type`, `placeholder`, etc. XPath uses `@` to access these attributes. | `//tag[@attribute='value']` | `//input[@id='username']` | When an element has a unique attribute. |
| Text | Selects elements based on their exact visible text. | `//tag[text()='value']` | `//button[text()='Login']` | When text is stable and unique. |
| Contains | Matches elements whose attribute or text contains a specific value. | `contains()` | `//input[contains(@id,'user')]` | For dynamic attributes that change partially. |
| Starts-With | Matches elements whose attribute starts with a specific value. | `starts-with()` | `//input[starts-with(@id,'user')]` | When only the beginning of an attribute remains constant. |
| AND Operator | Combines multiple conditions; all conditions must be true. | `and` | `//input[@type='text' and @name='email']` | To make locators more specific. |
| OR Operator | At least one condition should be true. | `or` | `//input[@id='username' or @name='username']` | When multiple attributes are possible. |
| Parent | Moves from a child element to its parent element. | `parent::` | `//input[@id='email']/parent::div` | To locate containers around an element. |
| Child | Selects direct children of an element. | `child::` | `//form/child::input` | When elements are directly inside another element. |
| Ancestor | Moves upward through multiple levels in the DOM. | `ancestor::` | `//input/ancestor::form` | To find higher-level containers. |
| Descendant | Finds elements present inside another element. | `descendant::` | `//form/descendant::input` | To search nested elements. |
| Following Sibling | Finds elements at the same level after the current element. | `following-sibling::` | `//label[text()='Username']/following-sibling::input` | Commonly used with labels and input fields. |
| Preceding Sibling | Finds elements at the same level before the current element. | `preceding-sibling::` | `//button/preceding-sibling::input` | To locate previous neighboring elements. |
| Following | Finds any element appearing after the current element. | `following::` | `//h1/following::button` | When the target element comes later in the DOM. |
| Preceding | Finds any element appearing before the current element. | `preceding::` | `//button/preceding::input` | When the target element appears earlier. |
| Position | Selects elements based on index. | `[n]` | `(//input)[2]` | When multiple similar elements exist. |
| Last | Selects the last element from a collection. | `last()` | `(//button)[last()]` | To locate the last element dynamically. |
| Wildcard | Matches any HTML tag. | `*` | `//*[@id='username']` | When the tag name is unknown. |
| Current Node | Searches within the current element. | `.` | `.//input` | Useful when working with WebElements. |
| Double Slash | Searches anywhere in the DOM. | `//` | `//button` | Most commonly used XPath expression. |
| Normalize Space | Removes extra spaces from text. | `normalize-space()` | `//button[normalize-space()='Submit']` | When text contains leading or trailing spaces. |

# Common HTML Attributes Used in XPath

| Attribute | Example |
|------------|---------|
| id | `<input id="username">` |
| name | `<input name="email">` |
| class | `<button class="login-btn">` |
| type | `<input type="password">` |
| placeholder | `<input placeholder="Enter Email">` |
| value | `<input value="Submit">` |
| href | `<a href="/home">Home</a>` |
| title | `<button title="Save">` |
| src | `<img src="logo.png">` |
| alt | `<img alt="Company Logo">` |

## Most Frequently Used XPath Functions in Real Projects

1. `@attribute`
2. `text()`
3. `contains()`
4. `starts-with()`
5. `and`
6. `or`
7. `following-sibling::`
8. `ancestor::`
9. `descendant::`
10. `last()`

> **Expert Tip:** Prefer stable attributes like `id`, `name`, and `placeholder`. Avoid absolute XPath (`/html/body/...`) because it is fragile and breaks easily after UI changes.

# XPath by Attribute

## Single Attribute

```xpath
//input[@id='username']
```

## Multiple Attributes

```xpath
//input[@id='username' and @type='text']
```

### Table

| XPath | Description |
|---------|------------|
| `//input[@id='email']` | Find by ID |
| `//input[@name='username']` | Find by name |
| `//button[@type='submit']` | Find submit button |
| `//a[@href='/home']` | Find link |

---

# XPath by Text

| XPath | Description |
|---------|------------|
| `//button[text()='Login']` | Exact text match |
| `//a[text()='Register']` | Exact text match |

Example:

```xpath
//button[text()='Login']
```

---

# contains()

### Attribute Contains

```xpath
//input[contains(@class,'form-control')]
```

### Text Contains

```xpath
//button[contains(text(),'Login')]
```

| XPath | Meaning |
|--------|--------|
| `contains(@id,'user')` | Partial ID match |
| `contains(@class,'btn')` | Partial class match |
| `contains(text(),'Login')` | Partial text match |

---

# starts-with()

```xpath
//input[starts-with(@id,'user')]
```

| XPath | Result |
|--------|--------|
| `starts-with(@id,'user')` | ID begins with user |
| `starts-with(@name,'emp')` | Name begins with emp |

---

# Logical Operators

| Operator | Example |
|-----------|--------|
| AND | `//input[@type='text' and @name='username']` |
| OR | `//input[@type='email' or @type='text']` |
| NOT | `//input[not(@disabled)]` |

---

# Indexing

| XPath | Meaning |
|--------|--------|
| `(//input)[1]` | First input |
| `(//input)[2]` | Second input |
| `(//input)[last()]` | Last input |
| `(//li)[position()=3]` | Third list item |

---

# Wildcards

| XPath | Description |
|--------|------------|
| `//*` | Any element |
| `//*[@id='submit']` | Any tag with ID |
| `//input[@*]` | Input with any attribute |

---

# XPath Axes

## Parent Axis

```xpath
//input[@id='email']/parent::div
```

## Child Axis

```xpath
//div/child::input
```

## Following Sibling

```xpath
//label/following-sibling::input
```

## Preceding Sibling

```xpath
//input/preceding-sibling::label
```

## Ancestor

```xpath
//input/ancestor::form
```

## Descendant

```xpath
//form/descendant::input
```

### Axes Summary

| Axis | Purpose |
|--------|--------|
| `parent::` | Parent node |
| `child::` | Child node |
| `ancestor::` | All ancestors |
| `descendant::` | All descendants |
| `following-sibling::` | Next siblings |
| `preceding-sibling::` | Previous siblings |

---

# XPath Functions

| Function | Example | Purpose |
|-----------|---------|---------|
| contains() | `contains(@class,'btn')` | Partial match |
| starts-with() | `starts-with(@id,'emp')` | Starts with value |
| last() | `(//li)[last()]` | Last element |
| position() | `(//li)[position()=3]` | Specific position |
| text() | `//button[text()='Login']` | Match exact text |

---

# Common Selenium Examples

| Element | XPath |
|----------|-------|
| Username Textbox | `//input[@name='username']` |
| Password Textbox | `//input[@type='password']` |
| Login Button | `//button[text()='Login']` |
| Checkbox | `//input[@type='checkbox']` |
| Radio Button | `//input[@type='radio']` |
| Dropdown | `//select[@id='country']` |
| Hyperlink | `//a[text()='Home']` |

---

# Quick Cheat Sheet

| Requirement | XPath |
|-------------|-------|
| By ID | `//*[@id='value']` |
| By Class | `//*[@class='value']` |
| By Name | `//*[@name='value']` |
| By Text | `//*[text()='Text']` |
| Contains Text | `//*[contains(text(),'Text')]` |
| Starts With | `//*[starts-with(@id,'emp')]` |
| Parent | `parent::` |
| Child | `child::` |
| Ancestor | `ancestor::` |
| Descendant | `descendant::` |
| Following Sibling | `following-sibling::` |
| Preceding Sibling | `preceding-sibling::` |

---

# Interview Questions

| Question | Answer |
|-----------|--------|
| What are the types of XPath? | Absolute and Relative XPath |
| Which XPath is preferred? | Relative XPath |
| Which function is used for partial matching? | `contains()` |
| Which axis finds next sibling? | `following-sibling::` |
| Which function returns last element? | `last()` |


# Why Do We Need XPath in Selenium?

XPath is used to locate web elements when attributes like `id`, `name`, or `class` are missing or change dynamically.

## Example

### HTML Today

```html
<input id="user_1234" placeholder="Username">
```

Selenium code using ID:

```python
driver.find_element(By.ID, "user_1234")
```

### HTML After Deployment

```html
<input id="user_5678" placeholder="Username">
```

The above code will fail because the `id` has changed.

## Using XPath

```python
driver.find_element(By.XPATH, "//input[@placeholder='Username']")
```

### Why does this work?

- The `id` may change every time the application is deployed.
- The `placeholder` value remains the same.
- XPath helps us locate elements using stable attributes, text, and relationships.

## Conclusion

XPath makes Selenium scripts more reliable when web elements have dynamic attributes.

## Justification
XPath is needed in Selenium because web applications are dynamic. Attributes such as IDs, names, and classes may change after every deployment. XPath provides flexible ways to locate elements using partial attributes, text, and relationships between elements, making test scripts more reliable and maintainable.
