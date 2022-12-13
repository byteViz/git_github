## Sections

- [Live Preview VS Code](#live-preview-vscode)
- [Headers](#headers)
- [Quotes](#quotes)
- [Emphasis](#emphasis)
- [Horizontal Rule](#horizontal-rule)
- [Lists](#lists)
- [Links](#links)
- [Images](#images)
- [Code](#code)
- [Tables](#tables)
- [Custom HTML](#custom-html)
- [Custom CSS](#custom-css)
- [Additional Resources](#additional-resources)

---

## VS Codelive preview

To turn on side by side live preview of the .md file, perform the key combination:

> ctrl+K V

Hold control and press K then with K pressed drop ctrl and press V.

## Headers

Headers are defined by the '#'symbol. One '#' for H1, two for H2, etc.

# Header1

## Header2

### Header3

#### Header4

##### Header 5

###### Header 6

---

## Quotes

Quotes are defined by the '>' symbol

> sample quote

You can combine a header with a quote.

> ## This is a H2 quote

---

## Emphasis

Add emphasis with asterisks '\*' and underscores '\_'
Two before and after (no spaces) a section of texts makes it bold

<!--
    Example

    **Bold Text with asterisks**
    __Bold Text with underscores__
-->

One before and after (no spaces) a section of texts makes it Italicized

<!--
    Example

    *Italicized Text with asterisks*
    _Italicized Text with underscores_
-->

You can also put Bold and Italicized text inline by surrounding a group of words.

<!--
    Example

    This text is **bold** and this text is *italicized*
-->

**this is a bold sentence**

_this is an italicized sentence_

this is a sentence with **bold** and _italicized_ text inline

## Horizontal Rule

A horizontal rule gives a visible line break. You can create one by putting three or more hypens, asterisks, or underscores (-, \*, \_).

<!--
    Example

    ---
    ***
    ___
-->

---

## Lists

Create unordered lists using '-', '\*', '+,

<!--
    Example with each

    - item
    * item
    + item
    - sdfsd
-->

You can create sublists by indenting

<!--
    Example

    - item
      - subitem
-->

Create ordered lists using a number prefix

<!--
    Example

    1. item 1
    2. item 2
    3. item 3
-->

- this is an unordered list:
  - item1
  - item2
  - item3

1. this is an ordered list:
   1. one
   2. two
   3. three

---

## Links

Create a link by surrounding it with angle bracket

<!--
    Example

    <http://www.aboutarun.com>
-->

Create a link with text by surrounding text with brackets, [], and link immediately following with parenthesis ()

<!--
    Example

    [Arunakchutha](http://www.aboutarun.com)
-->

<https://www.aboutarun.com>

[My Portfolio](https://www.aboutarun.com)

What if you needed to reuse a link several times? Well, you could copy and paste that link each time. That means, if you need to update the link, you will have to do it each time its used. There's a better way!

Create reference style links by defining your link with the a 'key' inside of brackets, colon, space, and the link

<!--
    Example

    [1]: http://aboutarun.com/
-->

Then use the reference style link by using your text inside of brackets followed by the link 'key' inside of bracket.

<!--
    Example

    [My Website][1]
-->

[aboutme]: https://www.aboutarun.com

[My Website][aboutme]

[About me][aboutme]

[My Portfolio][aboutme]

You can also link to other locations on your markdown page. Remember, your MarkDown will get converted to HTML, so you can, in theory, use a anchor tag to link to an element with a specific ID. You can find an example of this in the list of sections at the top of this document.

When we create a header tag for example, it implicitly creates an id property.

Ex '# Header' becomes `<h1 id="header">Header</h1>`

Names will be converted to ids by replacing spaces with hyphens and uppercase letters with lowercase letters (think css naming convention).

Ex 'Header Info' becomes header-info

[Goto Top of the Page](<a href="#Top">)

---

## Images

Defining an image is similar to defining a link, except you prefix it with '!'

<!--
    Example

    ![world](https://upload.wikimedia.org/wikipedia/commons/c/cf/A_large_blank_world_map_with_oceans_marked_in_blue.PNG)
-->

Just like links, you can define images by reference in the same format.

Define the reference

<!--
    Example

    [world]:https://upload.wikimedia.org/wikipedia/commons/c/cf/A_large_blank_world_map_with_oceans_marked_in_blue.PNG
-->

Use the reference

<!--
    Example

    ![Map of the world][world]
-->

[world]: https://upload.wikimedia.org/wikipedia/commons/c/cf/A_large_blank_world_map_with_oceans_marked_in_blue.PNG

![Map of the world][world]

---

## Code

You can do inline code with `backticks` (``)

The `git status` command is very commonly used ...

You can do blocks of code by surroung it with 3 backticks (` `)

<!--
    Example

    ```
    var num = 0;
    var num2 = 0;
```
-->

```
git switch main
git merge features
```

The above does not give language specific highlighting. You can specify the programming language immediately following the opening 3 backticks. You Should see a difference in highliting!

<!--
    Example Javascript

    ```javascript
    var num = 0;
    var num2 = 0;
    ```
-->

<!--
    Example HTML

    ```html
    <div>
        <p>This is an html example</p>
    </div>
    ```
-->

```html
<div>
  <p>This is an html example</p>
</div>
```

---

## Tables

Tables are useful for displaying rows and columns of data. Column headers can be defined in between pipes (|). Headers are separated from table content with a row of dashes (-) (still separated by pipes), and there must be at least 3 dashes between each header. The row data follows beneath (still separated by pipes).

<!--
    Example

    | Header 1    | Header 2    | Header 3    |
    | ----------- | ----------- | ----------- |
    | Row 1 Col 1 | Row 1 Col 2 | Row 1 Col 3 |
-->

The column definitions and row definitions do not have to have the exact same width sizes, but it would be much more readable. Notice the output of the following two tables are the same, but the second (the raw markdown) is much more readable.

<!--
    Example

    | Header 1 | Header 2 |
    | ----| ---|
    |Loooooooooooooong item 1 | looooooooooong item 2 |
-->

<!--
    Example

    | Header 1                | Header 2              |
    | ----------------------- | --------------------- |
    |Loooooooooooooong item 1 | looooooooooong item 2 | -->

| Header 1    | Header 2    | Header 3    |
| ----------- | ----------- | ----------- |
| Row 1 Col 1 | Row 1 Col 2 | Row 1 Col 3 |

You can also align (Center, left, right) the text in a column by using colons (:) in the line breaks between headers and rows. No colon means the default **left alignment**. Colons on each side signifies **center alignment**. And a trailing colon means **right alignment**.

| Header 1    |  Header 2   |    Header 3 |
| ----------- | :---------: | ----------: |
| Row 1 Col 1 | Row 1 Col 2 | Row 1 Col 3 |

<!--
    Example

    | Header | Header 1 | Header 2  |
    | ------ | :------: | --------: |
    | Aligned Left | Aligned Center | Aligned Right |
-->

---

## Custom HTML

Since MarkDown gets automatically converted to HTML, you can add raw HTML directly to your MarkDown.

```html
<p>Sample HTML Div</p>
```

---

## Custom CSS

You can also add custom CSS to your MarkDown to add additional styling to your document. You can also include CSS by including a style tag.

```html
<style>
  body {
    color: red;
  }
</style>
```

---
