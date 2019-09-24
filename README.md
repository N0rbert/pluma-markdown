This repository was forked from [gedit-markdown](https://github.com/jpfleury/gedit-markdown) to adapt it for Pluma editor. 
This repository was renamed to `pluma-markdown` to indicate compatibility with Pluma.

## Aknowlegement

Author of this repository would like to thank @jpfleury for original development.

## Overview

pluma-markdown adds support for [Markdown][] (or [Markdown Extra][]) in pluma, the default MATE DE text editor.

Specifically, it adds:

- Markdown syntax highlighting and snippets;

- plugin *Markdown Preview* for pluma, displayed in the side panel or the bottom panel and previewing in HTML the current document or selection (this plugin can also be used as a Web browser; see section *Usage*);

- an external tool exporting to HTML the current document or selection;

- a color scheme, optional, highlighting Markdown files in a manner more similar to HTML rendering.

[Markdown]: http://daringfireball.net/projects/markdown/
[Markdown Extra]: http://michelf.com/projects/php-markdown/extra/

<img src="https://github.com/N0rbert/pluma-markdown/raw/master/doc/example1.png" width="100%" alt="Default Markdown syntax highlighting in pluma." />

## Requirements

- pluma-markdown supports pluma 1.20.1 (as in Ubuntu 18.04 LTS). It's shipped with an installer for GNU/Linux.

- The plugin *Markdown Preview* depends on the package `python-markdown`.

- For users of Ubuntu (and maybe other distributions) 18.04 LTS, the packages `gir1.2-webkit-3.0 python-configparser` must be installed to use the plugin *Markdown Preview*. 

Simply install all needed stuff with `sudo apt-get install python-markdown gir1.2-webkit-3.0 python-configparser`.

## Installation (or update)

- [Download the archive of pluma-markdown](https://github.com/N0rbert/pluma-markdown/archive/master.zip)

- Extract the archive.

- Open a terminal in the extracted folder.

- Run the installer in the terminal:

		./pluma-markdown.sh install

Or programmatically:

```
cd ~/Downloads
wget https://github.com/N0rbert/pluma-markdown/archive/master.zip
unzip master.zip
cd pluma-markdown-master
./pluma-markdown.sh install
```

Markdown support will be added for the current user (so no need root privileges). The folder created by the extraction can be deleted after installation.

## Uninstallation

- Open a terminal in the extracted folder.

- Run the uninstaller in the terminal:

		./pluma-markdown.sh uninstall

## Usage

First of all, restart pluma if it's already running.

### Syntax highlighting

Syntax highlighting should automatically be activated for files recognized as Markdown files (extensions `.markdown`, `.md` or `.mkd`), otherwise choose it manually by going to *View > Highlight Mode > Markup* and selecting *Markdown*.

### Plugin *Markdown Preview*

To enable this plugin, go to *Edit > Preferences > Plugins* and check *Markdown Preview*.

Two items are added in the pluma menu *Tools*:

- *Update Markdown Preview*: displays in the side panel or in the bottom panel a preview in HTML of the current document or selection.

	Note: there are two other ways to update preview:
	
	  - with the keyboard shortcut *Ctrl+Alt+m* (can be changed in the configuration file);
	
	  - by right clicking on the preview area (side or bottom panel) and selecting the item *Update Preview*.

- *Toggle Markdown Preview visibility*: allows to display or hide the Markdown Preview panel tab.

	Note: the keyboard shortcut *Ctrl+Alt+v* (can be changed in the configuration file) can be used to do the same.

When right clicking on the preview area, a context menu appears and lists several options. Besides the default ones (previous page, next page, copy, etc.), we have:

- *Copy the current URL*: copy in the clipboard the URL of the document or the page being displayed in the preview tab. If it's a document that has not yet been saved to disk, this menu item is disabled.

- *Go to another URL*: allows to manually enter a local or distant URL of a document or page to visit in the preview tab.

- One of the following two options, depending on the value of the property `externalBrowser` in the configuration file:

	- *Open in an external browser*: allows to open the link in an external browser.

	- *Open in the embedded browser*: allows to open the link in the panel.

- *Update Preview*: reloads in the side panel or in the bottom panel the preview in HTML of the current document or selection.

- *Clear Preview*: clear content of the preview tab.

### Snippets

To use Markdown snippets, activate the plugin *Snippets* in *Edit > Preferences > Plugins*. Then, go to *Tools > Manage Snippets...* to see the possibilities.

### External tool *Export to HTML*

To use the external tool, activate the plugin *External Tools* in *Edit > Preferences > Plugins*. Then, go to *Tools > External Tools > Export to HTML* to access the tool. The keyboard shortcut *Ctrl+Alt+h* does the same. The code of the currently opened Markdown file or the selection will be converted in HTML, and the result will be put in a new document.

To edit the tool, go to *Tools > Manage External Tools...*.

### Optional color scheme

An optional color scheme is installed by pluma-markdown. To use it, go to *Edit > Preferences > Font & Colors > Color Scheme* in pluma and select *Classic Markdown*. This color scheme is more similar to an HTML rendering, for example strong emphases and headers are in bold and black font, links are blue and underlined, etc.

### Configuration file

The configuration file of pluma-markdown is the following:

	$XDG_CONFIG_HOME/pluma/pluma-markdown.ini

Most of the time, it will correspond to:

	$HOME/.config/pluma/pluma-markdown.ini

The section `markdown-preview` contains several properties:

- `externalBrowser`: open links in an external browser by default. Possible values: `0` (don't open links in an external browser by default; default value) or `1` (open links in an external browser by default).

	If `externalBrowser` has a value of `0`, the context menu displayed when right clicking on a link will contain an option to open the link in an external browser. If `externalBrowser` equals `1`, the context menu will contain an option to open the link in the embedded browser.

- `panel`: emplacement of the preview. Possibles values: `bottom` (default value) or `side`.

- `shortcut`: shortcut to refresh the preview. The default value is `<Control><Alt>m`.

- `version`: the Markdown version to use for the HTML preview and to export to HTML. Possible values: `extra` (default value) or `standard`.

- `visibility`: visibility of the Markdown Preview panel tab when pluma starts. Possible values: `0` (hidden) or `1` (displayed; default value).

- `visibilityShortcut`: shortcut to toggle Markdown Preview visibility. The default value is `<Control><Alt>v`.

## Details and limitations

- Syntax highlighting and snippets for standard Markdown were officially added in GtkSourceView and gedit > 3.1.1. The installer of pluma-markdown will ensure that no already existing files are copied (no check is done for Markdown Extra because this is not the default version shipped with GtkSourceView and gedit > 3.1.1).

- Since HTML code can be directly used in a text written in Markdown, HTML syntax highlighting was added to Markdown syntax highlighting. However, keep in mind that, even if they're highlighted, Markdown syntax within HTML blocks (e.g. `<div>`) and Markdown Extra syntax within HTML blocks without `markdown` attribute set to 1 (e.g., `<div markdown="1">`) are not processed.

- Within a paragraph, text wrapped with backticks indicates a code span. Markdown allows to use one or more backticks to wrap text, provided that the number is identical on both sides, and the same number of consecutive backticks is not present within the text. Examples:

		`lorem lorem lorem lorem`
		
		`lorem lorem `` lorem lorem`
		
		`lorem lorem ````` lorem lorem`
		
		``lorem lorem lorem lorem``
		
		``lorem lorem ` lorem lorem``
		
		``lorem lorem ````` lorem lorem``

	Syntax highlighting in pluma supports code span highlighting with up to 2 backticks surrounding text.

- Blockquote can contain block-level and inline Markdown elements, but pluma-markdown only highlights inline ones (emphasis, link, etc.).

- A full context analysis can't be done (because line break can't be used in regex). Here are some consequences:

	- According to the Markdown syntax, to write several paragraphs in a list item, we have to indent each paragraph. Example:

			- Item A (paragraph 1).

				Item A (paragraph 2).

				Item A (paragraph 3).

			- Item B.

		So there is a conflict in terms of syntax highlighting between an indented paragraph inside a list item (4 spaces or 1 tab) and an indented line of code outside a list (also 4 spaces or 1 tab). The choice was made ​​​​to highlight code block only from 2 levels of indentation.

	- Only the underline of a Setext-style header is matched and highlighted, so there's no guarantee that it's indeed a title underline.

	- With Markdown Extra, some elements are matched and highlighted with no guarantee that they're in the right context: Setext-style header id attribute, colon used as separator in a definition list and separator line of a table.


## Localization

The plugin *Markdown Preview* is localizable. The file containing strings is `plugins/markdown-preview/locale/markdown-preview.pot`.

