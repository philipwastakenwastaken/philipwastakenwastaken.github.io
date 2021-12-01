---
layout: default
---

DET HER ER INFORMATIONS MARKDOWN-FILEN. DETTE ER IKKE HJEMMESIDE-MARKDOWN'EN. 
FOR AT ÆNDRE/TILFØJE TIL HJEMMESIDEN, SÅ BENYT ```index.md```! :)
INDSÆT BILLEDER I ```images``` FOLDEREN

# Markdown commands

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).

If you want to link to somewhere on the same page like to 'Header 1' ([Link to header](#header-1)),
then write the header as lower-case with '-' inbetween: 
```
[Link to header](#header-1).
```


There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Code is written this way
function foo() {
  return 1+1;
}
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Centered Image 
```
{% include image.html url="/images/<image_here>" description="<description here>" width="<size>" height="<size>" %}
```

### Image on one of the sides
```
{% include image_side.html url="/images/<image_here>" description="<description here>" align="<left or right>" width="<percentage>%" height="<percentage>%" fill="<percentage>%" %}
```


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
