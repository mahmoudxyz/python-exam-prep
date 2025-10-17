# Markdown to HTML Converter

## The Challenge

Build a command-line tool that converts Markdown syntax to HTML. Design the architecture however you want - OOP, functional, procedural - your choice.

## What to Support

### Required Features:

- Headers (`#`, `##`, `###`, etc.)
- Bold (`**text**`)
- Italic (`*text*`)
- Inline code (`` `code` ``)
- Links (`[text](url)`)
- Unordered lists (`- item`)
- Ordered lists (`1. item`)
- Paragraphs (blank line separated)

### Bonus Features:

- Code blocks (` `)
- Blockquotes (`> quote`)
- Horizontal rules (`---`)
- Nested formatting
- Read from file / Save to file

## Input/Output Examples

### Example 1: Headers and Paragraphs

**Input:**

```markdown
# Welcome

This is a simple paragraph.

## Section 2

Another paragraph here.
```

**Output:**

```html
<h1>Welcome</h1>
<p>This is a simple paragraph.</p>
<h2>Section 2</h2>
<p>Another paragraph here.</p>
```

---

### Example 2: Inline Formatting

**Input:**

```markdown
This is **bold** and this is _italic_ text.

Check out `my_function()` for details.
```

**Output:**

```html
<p>This is <strong>bold</strong> and this is <em>italic</em> text.</p>
<p>Check out <code>my_function()</code> for details.</p>
```

---

### Example 3: Lists

**Input:**

```markdown
## Features

- Easy to use
- Fast conversion
- Clean output

## Steps

1. Write markdown
2. Run converter
3. Get HTML
```

**Output:**

```html
<h2>Features</h2>
<ul>
  <li>Easy to use</li>
  <li>Fast conversion</li>
  <li>Clean output</li>
</ul>
<h2>Steps</h2>
<ol>
  <li>Write markdown</li>
  <li>Run converter</li>
  <li>Get HTML</li>
</ol>
```

---

### Example 4: Links

**Input:**

```markdown
Visit [my website](https://example.com) for more info.

Check out [GitHub](https://github.com) too.
```

**Output:**

```html
<p>Visit <a href="https://example.com">my website</a> for more info.</p>
<p>Check out <a href="https://github.com">GitHub</a> too.</p>
```

---

### Example 5: Code Blocks (Bonus)

**Input:**

````markdown
Here's some Python code:

```
def hello():
    print("Hello, World!")
```

That's it!
````

**Output:**

```html
<p>Here's some Python code:</p>
<pre><code>def hello():
    print("Hello, World!")
</code></pre>
<p>That's it!</p>
```

---

### Example 6: Complex Mix

**Input:**

```markdown
# My Project

This is a **great** project with _lots_ of features.

## Installation

1. Clone the repo
2. Run `pip install -r requirements.txt`
3. Start coding!

## Resources

- [Documentation](https://docs.example.com)
- [GitHub](https://github.com/example)

---

Happy coding!
```

**Output:**

```html
<h1>My Project</h1>
<p>This is a <strong>great</strong> project with <em>lots</em> of features.</p>
<h2>Installation</h2>
<ol>
  <li>Clone the repo</li>
  <li>Run <code>pip install -r requirements.txt</code></li>
  <li>Start coding!</li>
</ol>
<h2>Resources</h2>
<ul>
  <li><a href="https://docs.example.com">Documentation</a></li>
  <li><a href="https://github.com/example">GitHub</a></li>
</ul>
<hr />
<p>Happy coding!</p>
```

---

## Command Line Interface

Your program should work like this:

```bash
$ python markdown_converter.py

Enter markdown (type 'END' on a new line to finish):
# Hello World
This is **bold**.
END

Output:
<h1>Hello World</h1>
<p>This is <strong>bold</strong>.</p>
```

Or read from a file:

```bash
$ python markdown_converter.py input.md
# Converts input.md and prints HTML
```

Or save to a file:

```bash
$ python markdown_converter.py input.md output.html
# Converts input.md and saves to output.html
```

---

## What You'll Practice

- String parsing and manipulation
- Pattern matching
- Data structures (lists, dicts, strings)
- File I/O
- Functions or classes (your choice)
- Algorithm design
- Edge case handling

## Design Approach (Your Choice!)

### Option 1: OOP

- Classes for different element types
- Inheritance hierarchy
- Parser class

### Option 2: Functional

- Pure functions for each conversion
- Function composition
- Immutable data flow

### Option 3: Procedural

- Main parsing loop
- Helper functions
- Direct string manipulation

**Choose what works for you!**

---

## Success Criteria

✅ Converts all required markdown syntax correctly  
✅ Produces valid HTML  
✅ Handles edge cases (empty lines, multiple spaces, etc.)  
✅ Works from command line  
✅ Code is readable and organized

## Time Estimate

2-4 hours depending on features implemented

---

## Tips

- Start with headers and paragraphs
- Add inline formatting (bold, italic) next
- Lists are trickier - handle consecutive items
- Links require careful parsing of `[text](url)` pattern
- Test incrementally with simple examples
- Don't worry about perfect Markdown spec compliance

## Submit Your Solution

Save as `solutions/yourname_markdown_converter.py`

Test with the examples above to verify it works!
