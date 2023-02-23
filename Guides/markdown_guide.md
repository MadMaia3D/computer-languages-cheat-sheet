# Markdown

## Headers
Use the number sign to create a header:
```markdown
# Level 1 Header
## Level 2 Header
### Level 3 Header
#### Level 4 Header
##### Level 5 Header
###### Level 6 Header
```
Result:
# Level 1 Header  
## Level 2 Header  
### Level 3 Header  
#### Level 4 Header  
##### Level 5 Header  
###### Level 6 Header

---
## Normal Text:
To separate paragraphs, leave a blank line between them.
To break lines on text, end the line with two space.

---
## Styled Text

## Italics:
Wrap the text with * or _:
```markdown
Here is a *piece of text* in italics.  
Here is another _piece of text_ in italics
```
Result:  
Here is a *piece of text* in italics.  
Here is another _piece of text_ in italics

## Bold:
Wrap the text with ** or __:
```markdown
This is a **piece of text** in bold.  
This is another __piece of text__ in bold.
```
Result:  
This is a **piece of text** in bold.  
This is another __piece of text__ in bold.

## Bold and italics:
Wrap the text with ** or __:
```markdown
This is a ***piece of text*** in bold.  
This is another ___piece of text___ in bold.
```
Result:  
This is a ***piece of text*** in bold.  
This is another ___piece of text___ in bold.

## Strikethroughs:
Wrap the text with ~~.
```markdown
This is a ~~piece of text~~ with a strikethrough.  
```
Result:  
This is a ~~piece of text~~ with a strikethrough.  

## Blockquotes:
Start you line with a >.
```markdown
> This is a blockquote.
```
Result:
> This is a block quote.

---
## Code

For inline code, surround your code with the backtick character ( \` ):

```markdown
Put you code `here`.
```

Result:  
Put you code `here`.

For a block of code, surround your code with triple backticks:

````markdown
```language_name(optional)
Put the block of code here.
```
````

Or indent every line by at least 4 spaces or 1 tab:

````markdown
    Put the block of code here.
````

---
## Links & Images

### Links:
```markdown
[Google](https://www.google.com)
```

Result:  
[Take Me To Google](https://www.google.com)

You can link to other files too:
```markdown
[Another page](another_file.md)
```

### Images:
Insert a exclamation mark before the link:
```markdown
![Image Alternative Text](image_file.png)
```
Result:  
![Image Alternative Text](./resources/images/ferrari-250-gto.jpg)

Result with missing image or invalid path:  
![Image Alternative Text](image_file.png)

---
## Lists

### Unordered:
Precede each item in the list with a dash/hyphen:
```markdown
- Item A
- Item B
- Item C
```
Result:  
- Item A
- Item B  
- Item C  

Or use a asterisk instead:
```markdown
* Item A
* Item B
* Item C
```
Result:
* Item A  
* Item B  
* Item C  

### Ordered:
Just precede an list items with a number and a dot. It doesn't need to be in order, you can just repeat the same number:

```markdown
1. Item 1
1. Item 2
1. Item 3
```
Result:  
1. Item 1
1. Item 2
1. Item 3

---
## Tables

```markdown
Col 1 | Col 2 | Col 3
--- | --- | ---
*Item 1* | *Item 2* | *Item 3*
*Item 4* | *Item 5* | *Item 6*
```

Result:
Col 1 | Col 2 | Col 3
--- | --- | ---
*Item 1* | *Item 2* | *Item 3*
*Item 4* | *Item 5* | *Item 6*

---
## Task list
Unfortunately task lists doesn't work everywhere:
```markdown
- [ ] This isn't done
- [x] This is done
```
- [ ] This isn't done
- [x] This is done

---
## Emoji
Unfortunately emojis doesn't work everywhere: 
```markdown
:smile:  
:wave:
```
:smile:  
:wave:

---
## Raw HTML:
```markdown
<h3>This is a HTML header element</h3>
```
Result:
<h3>This is a HTML header element</h3>