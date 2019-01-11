## Markdown Basics for GitHub Projects

### Headings in Markdown
As you see above, Two hash symbols (##) create an H2 heading. The number of hash symbols determines the heading level — for example, ### creates an H3. Always leave a blank line before a heading to ensure proper rendering.
```
# Main Heading (H1) 
## Section Heading (H2)
### Subsection (H3)
#### Smaller Section (H4)
##### Even Smaller (H5)
###### Smallest Heading (H6)
```
and looks like this

# Main Heading (H1) 
## Section Heading (H2)
### Subsection (H3)
#### Smaller Section (H4)
##### Even Smaller (H5)
###### Smallest Heading (H6)

### Code Blocks
You may have noticed 3 backticks, (In windows, it is a key below the esc and left to 1)- helps to create a code block and used above to make it a section of different heading.
```
    message= "Hello world!"
    print(message)
```
### Text Formatting

**Bold text- achieved by placing two asterisks on either end**  
*Italic text - achieved by placing one asterisk on either end*  
~~strikethrough - achieved by placing two tilde on either side~~  
`inline code - achieved by placing single backtick on either end`

*The tilde(~) in strikethrough is the same backtick(`) key below **esc** and left to **1***

### Line Breaks
Standard : Can be achieved by placing two spaces at the end of line  
Explicit : use of `<br>` html tag at the end of the line.

### Lists

```
#### Unordered lists
  - Item 1  
    - Nested item  
  - Item 2

#### Ordered lists
1. First step
2. Second step
   1. Substep A
   2. Substep B
```
and looks like this
#### Unordered lists
  - Item 1  
    - Nested item  
  - Item 2

and 
#### Ordered lists
1. First step
2. Second step
   1. Substep A
   2. Substep B
### Links

```
[Link text](https://github.github.com/gfm/)
```
[Link text](https://github.github.com/gfm/)
### Images

```
![Alt text for image](path/to/image.png)
```

### Blockquotes
Blockquotes are used to highlight or quote a section of text or call out warnings, tips, or ideas.
```
> This is a blockquote 
> You can use multiple lines
>> Nested blockquotes are also possible
```
> This is a blockquote 
> You can use multiple lines
>> Nested blockquotes are also possible
### Horizontal Rule

```
---
```
### Checkboxes

```
- [x] Implement binary search
- [ ] Add unit tests
```
and should like this 
- [x] Implement binary search
- [ ] Add unit tests
### GitHub-Specific Markdown

### [README.md](README.md)

### Collapsible - click to reveal more
Syntax (How to write a collapsible section in Markdown)

```<details>
<summary>TLDR; Click for quick Markdown tips & note</summary>

- **Use blank lines before headings** to ensure proper rendering  
- **Inline code**: Enclose code in backticks `` `code` ``  
- **Code blocks**: Use triple backticks. You can specify language like ` ```python `  
- **Line breaks**: Add two spaces at the end of a line, or use `<br>`  
- **List nesting**: Indent sub-items with 2+ spaces  
- **Escaping characters**: Use `\` before symbols like `\*`, `\_`, or `\|`  
- **Table alignment**:
  ```markdown
  | Left | Center | Right |
  |:-----|:------:|------:|
GitHub-only features: Checkboxes, collapsible sections, syntax highlighting, etc. may not work on all Markdown renderers.
</details>
```
Output (What it looks like when rendered)
<details>
<summary>TLDR; Click for quick Markdown tips & note</summary>

- **Use blank lines before headings** to ensure proper rendering  
- **Inline code**: Enclose code in backticks `` `code` ``  
- **Code blocks**: Use triple backticks. You can specify language like ` ```python `  
- **Line breaks**: Add two spaces at the end of a line, or use `<br>`  
- **List nesting**: Indent sub-items with 2+ spaces  
- **Escaping characters**: Use `\` before symbols like `\*`, `\_`, or `\|`  
- **Table alignment**:
  ```markdown
  | Left | Center | Right |
  |:-----|:------:|------:|
GitHub-only features: Checkboxes, collapsible sections, syntax highlighting, etc. may not work on all Markdown renderers.
</details>

### Tables
A table in Markdown uses pipes (|) and dashes (-) to define columns and headers.
Like this-  
```
| Feature           | Syntax                            | Example Output                     |
|-------------------|-----------------------------------|------------------------------------|
| Heading           | `# Heading 1`, `## Heading 2`     | # Heading 1                        |
| Bold              | `**bold**` or `__bold__`          | **bold**                           |
| Italic            | `*italic*` or `_italic_`          | *italic*                           |
| Bold + Italic     | `***bold italic***`               | ***bold italic***                  |
| Strikethrough     | `~~strikethrough~~`               | ~~strikethrough~~                  |
| Inline Code       | `` `code` ``                      | `code`                             |
| Code Block        | \`\`\`python ... \`\`\`           | Code block with syntax highlighting|
| Blockquote        | `> text`                          | > text                             |
| Ordered List      | `1. Item`                         | 1. Item                            |
| Unordered List    | `- Item` or `* Item`              | - Item                             |
| Task List (GitHub)| `- [ ] item`, `- [x] item`        | - [ ] unchecked, - [x] checked     |
| Link              | `[text](url)`                     | [Google](https://google.com)       |
| Image             | `![alt](img.png)`                 | ![alt](img.png)                    |
| Horizontal Line   | `---` or `***`                    | ---                                |
| Line Break        | 2 spaces at end of line or `<br>` | Line 1␣␣<br>Line 2                  |
| Table             |  use pipe and dash character      | Tables like this one               |

```
and the above table should like this, ( just let's focus on the pipe(|) a dash(-) characters forming table)
| Feature           | Syntax                            | Example Output                     |
|-------------------|-----------------------------------|------------------------------------|
| Heading           | `# Heading 1`, `## Heading 2`     | # Heading 1                        |
| Bold              | `**bold**` or `__bold__`          | **bold**                           |
| Italic            | `*italic*` or `_italic_`          | *italic*                           |
| Bold + Italic     | `***bold italic***`               | ***bold italic***                  |
| Strikethrough     | `~~strikethrough~~`               | ~~strikethrough~~                  |
| Inline Code       | `` `code` ``                      | `code`                             |
| Code Block        | \`\`\`python ... \`\`\`           | Code block with syntax highlighting|
| Blockquote        | `> text`                          | > text                             |
| Ordered List      | `1. Item`                         | 1. Item                            |
| Unordered List    | `- Item` or `* Item`              | - Item                             |
| Task List (GitHub)| `- [ ] item`, `- [x] item`        | - [ ] unchecked, - [x] checked     |
| Link              | `[text](url)`                     | [Google](https://google.com)       |
| Image             | `![alt](img.png)`                 | ![alt](img.png)                    |
| Horizontal Line   | `---` or `***`                    | ---                                |
| Line Break        | 2 spaces at end of line or `<br>` | Line 1␣␣<br>Line 2                  |
| Table             |  use pipe and dash character      | Tables like this one         

Referenced from https://www.markdownguide.org/basic-syntax/