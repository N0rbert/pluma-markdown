First level (style Setext)
================================

## Second level header

### Third level header ###

It is possible to use *italic* and **bold**. The monospaced inline code is also supported - `code in line`. But you can escape it too: \`not code in a line\`.

HTML tags are also supported - <strong>code HTML in bold</strong> inside Markdown document.

Below is the list with three items:

- Unnumbered list item labeled with `-`
+ Unnumbered list item labeled with `+`
* Unnumbered list item labeled with `*`

The numbered list is below:

1. First

2. Second

		<em>Code HTML</em> in html
		<strong>strong</strong>.

3. List item with text paragraph

	The paragraph.

Citation block:

> First level with **bold**.
>> Second level with *italic*.

Horizontal lines:

----------
** ** ** ** **
__  __  __  __  __

The links also have their syntax:

- Automatic link: <https://github.com/N0rbert/pluma-markdown>

- Embedded link to the text: The software [pluma-markdown](https://github.com/N0rbert/pluma-markdown "optional title attribute") allows you to add Markdown language support in the pluma text editor.

- Link by reference: the [pluma-markdown][1] software makes it possible, among other things, to use the syntax highlighting of Markdown in pluma.

- Other link by reference: the software [pluma-markdown] allows among other things to use the Markdown syntax highlighting in pluma.

We should not forget the images:

- Image embedded in the text: the logo of Wikipedia is ![Wikipedia](http://upload.wikimedia.org/wikipedia/commons/5/5a/Wikipedia-logo-v2-fr.png)

- Image by reference: the logo of Wikipedia is ![Wikipedia][logo wikipedia]

The links by reference created a little higher can be defined anywhere in the text, for example here:

[1]: https://github.com/N0rbert/pluma-markdown
[pluma-markdown]: https://github.com/N0rbert/pluma-markdown

Same thing as regards the image by reference:

[logo wikipedia]: http://upload.wikimedia.org/wikipedia/commons/5/5a/Wikipedia-logo-v2-fr.png "Optional title attribute"
