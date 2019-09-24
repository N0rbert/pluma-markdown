Setext style title with an `id` attribute {#idTitle1}
===========================================

## atx style title with `id` attribute ## {#idTitre2}

Underline bars no longer generate an emphasis inside a word:

- The name of the file is "my_text_file.txt".
- The file name is "my__text_text.txt".

For the other contexts, the emphasis is still generated:

- I use _Markdown Extra_.
- I use __Markdown Extra__.

Here is a list of definitions:

Word 1
: definition

Word 2
: definition

Here is a block of marked code:

~~~
<em> HTML code </em> displayed
<strong> without interpretation </strong>.
~~~

Markdown Extra allows you to specify abbreviations, for example:

* [bac]: Bachelor's degree
* [HTML]: Hypertext Markup Language

All occurrences of "bin" and "HTML" found in the text will be marked to allow display of the definition as the cursor moves.

Here is a sentence that contains a link to a footnote [^1].

Tables are also supported:

| Table title 1 | Table title 2 |
| ------------- | ------------- |
| Cell          | Cell          |
| Cell          | Cell          |

The footnote created a little higher can be defined anywhere in the text, for example here:

[^1]: Here is the footnote.

Finally, two new characters can be escaped: the colon (\:) and the vertical bar (\|).
