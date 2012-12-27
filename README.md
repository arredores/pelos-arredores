Using Markdown in WriteMonkey 
=============================

-----
[Original](http://wm.jcby.com/md.html) by Jim Brown
-----

[_Markdown_] [3] is a system of markup for a plain text document designed 
to produce valid HTML content for the web directly from that readable text 
document. It is implemented within WriteMonkey such that a source text document 
written in WriteMonkey with _Markdown_ markup can be exported directly into 
a complete web page. I had already begun to write content for my web site 
using plain text when I found WriteMonkey. One way to learn about anything 
is to write a tutorial about it. By writing a _Markdown_ tutorial in _Markdown_ 
itself, I could quickly learn all the features of the markup. Using a tool 
fixes it more securely in your mind than just [reading about it][1]&mdash;at 
least it does in mine.

Table of Contents
-----------------

*  [Purpose of Markdown](#pur)
*  [Markdown in WriteMonkey](#mdwm)
*  [Document Structure](#docstru)
*  [Text Formatting](#emp)
*  [Lists](#list)
*  [Links](#lnk)
*  [Images](#img)
*  [Preformatted Blocks and Spans](#pre)
*  [Literal Characters](#lit)
*  [Other Features](#oth)
*  [Exceptions to _Markdown_ in WriteMonkey ](#exc)


<h2 id="pur"> Purpose of Markdown </h2>

_Markdown_ is designed to produce readable source text for the web. All of 
the markup consists of punctuation marks, many from the days when e-mail 
messages were plain text without the benefit of HTML or CSS formatting to 
show bold, italics, etc. So users took to writing `*bold*` and `_italics_` 
to show their intent. But the key is readable source text. You should be 
able to display or print a _Markdown_ document and read it without having 
to navigate a maze of angle brackets, tags, and attributes. To see what I 
mean, you can view the [source text of this document] [2]. You can manage 
your content much better when it is readable plain text documents.


<h2 id="mdwm"> Markdown in WriteMonkey </h2>

_Markdown_ is a limited set of markup that translates to the HTML tags you 
use in writing content for the web (as opposed to use in laying out a web 
page). There are a lot of elements for which there is no _Markdown_ markup, 
e.g., tables. This is, however, not a serious problem as _Markdown_ will 
accept HTML code within the document and simply pass it through when the 
markup is converted to HTML. The original _Markdown_ is a Perl script available 
from the author John Gruber's [Daring Fireball site] [3]. The script processes 
the markup to produce a snippet of HTML suitable for inserting into the code 
for a web page. The implementation of _Markdown_ within WriteMonkey is supplemented 
to produce a complete web page and apply a style sheet when the marked-up 
document is converted (exported in WriteMonkey's terminology) to HTML. Note 
that you can produce a snippet of HTML from WriteMonkey by copying the markup 
of the entire file or a selection of markup within the text to a file using 
Ctrl+Shift+H. 


<h2 id="docstru"> Document Structure </h2>

The basic unit of structure in _Markdown_ is the *paragraph*. No particular 
markup is required for a paragraph. You simply separate blocks of text with 
a blank line (by pressing Enter twice at the end of the paragraph) to create 
a paragraph. As in HTML, the most visible document structure elements are 
headings. With _Markdown_, you can markup *headings* in two ways. If you 
want to use only H1 and H2, you can underline the heading text with equal 
signs (H1) or hyphens (H2). Thus, a heading marked like this in the source 
text document:

  Heading H1  
  ==========

is converted to the following HTML when processed through the _Markdown_ 
script or exported from WriteMonkey:

	<h1>Heading H1</h1>

Note that the number of underline characters is irrelevant; even one will 
work. The second way to markup headings is by inserting one to six `#s` before 
the heading text. Thus, this markup:

	#### Heading H4

is converted to:

	<h4>Heading H4</h4>

If it pleases your eye better, you can close the hash marks like this:

	### Heading H3 ###

(the number of closing hashes is irrelevant as the number of opening hashes 
controls the heading level).

*Horizontal rules* are inserted in the source text using three or more `*s` 
or `-s` on a line by themselves. The `*s` or `-s` may be separated by spaces. 
For example, each of the lines of markup below is converted to `<hr />`:

	- - - - - - - - - - - - -  
	--------    
	***

*Manual line breaks* are inserted by ending a line of text with two or more 
spaces, which are converted to `<br />`.

*Blockquotes* are marked up as quoted messages are in e-mail, with a leading 
`>` on the line. This markup:

		> This is the markup for a blockquote paragraph. You
	see that you only have to place a single > at the
	beginning of the paragraph to indent the entire
	paragraph.

is rendered as:

   > This is the markup for a blockquote paragraph. You
see that you only have to place a single > at the beginning of the paragraph 
to indent the entire paragraph. 

Using the single >, however, does not display well in the source text. For 
the source text, it is better to use a hard return at the end of each line 
and place a > before each one, like this:

	> This is the markup for a blockquote paragraph. If
	> you use a > at the beginning of each line and
	> place a hard return at the end, it is much more
	> obvious in your source text that this is a
	> blockquote.

which renders the same way in the browser as using the single >:

   > This is the markup for a blockquote paragraph. If
   > you use a &gt; at the beginning of each line and
   > place a hard return at the end, it is much more
   > obvious in your source text that this is a
   > blockquote.

Blockquotes may be nested and have multiple paragraphs, as illustrated by 
this markup:

	> Lorem ipsum dolor sit amet, consectetur adipiscing
	> elit. Maecenas nec purus vitae leo posuere blandit a
	> a sem. Morbi a sapien et leo posuere placerat.
	>
	> Cras ultricies, sapien tincidunt semper accumsan,
	> ante odio ultricies diam, ac molestie orci sapien
	> sed nunc.
	>
		>> Nulla vitae leo id purus vestibulum gravida
		>> sit amet eu arcu. Aenean nec turpis eget nisi
		>> bibendum condimentum at nec libero. Cras
		>> viverra molestie vestibulum.
	>
	> Morbi ante mi, lobortis quis eleifend vel, commodo
	> eget ipsum. Sed hendrerit orci id erat dignissim ac 
	> dapibus massa condimentum. 

which renders as:

   > Lorem ipsum dolor sit amet, consectetur adipiscing
   > elit. Maecenas nec purus vitae leo posuere blandit a
   > a sem. Morbi a sapien et leo posuere placerat.
   >
   > Cras ultricies, sapien tincidunt semper accumsan,
   > ante odio ultricies diam, ac molestie orci sapien
   > sed nunc.
   >
	>> Nulla vitae leo id purus vestibulum gravida
	>> sit amet eu arcu. Aenean nec turpis eget nisi
	>> bibendum condimentum at nec libero. Cras
	>> viverra molestie vestibulum.
   >
   > Morbi ante mi, lobortis quis eleifend vel, commodo
   > eget ipsum. Sed hendrerit orci id erat dignissim ac 
   > dapibus massa condimentum. 


<h2 id="emp"> Text Formatting </h2>

The only text formatting markup is for italic and bold. Standard _Markdown_ 
markup calls for a string of text to be wrapped in single symbols, either 
`_` or `*`, to produce italic or double symbols to produce bold. Thus, either:

	_italic_ or *italic*

is converted to:

	<em>italic</em>

and:

	__bold__ or **bold**

is converted to:

	<strong>bold</strong>

Note that WriteMonkey's use of _Markdown_ has an [exception](#exc) to this 
in that single underscores are used for italic and asterisks for bold. Double 
underscores in WriteMonkey produce underlined text. 


<h2 id="list"> Lists </h2>

_Markdown_ allows you to insert either an ordered (numbered) list or an unordered 
(bullet) list. Ordered lists are marked up by inserting a number followed 
by a period at the beginning of a line. Unordered lists are marked up by 
inserting a `-`, `*`, or `+` at the beginning of a list item. The number 
or symbol may be indented up to 3 spaces (at the 4th space, _Markdown_ thinks 
you want to insert a preformatted line) and must be followed by at least 
one space or a tab. Lists may be nested and other block or span markup may 
be included within a list item. If a list item includes a second paragraph 
or other block element, it must be indented by at least 4 spaces or a tab. 
Preformatted blocks must be preceded by two tabs, one to signal a block element 
within a list item and one to signal preformatted text. For example, the 
following markup for an unordered list:

	*  First list item in unordered list
	*  Second list item in unordered list
		-  First list item in nested unordered list

		   Second paragraph of the first list item in the 
		   nested list.

		-  Second list item in next unordered list
	*  Third list item in unordered list

is converted to:

	<ul>
	<li>First list item in unordered list</li>
	<li><p>Second list item in unordered list</p>

		<ul>
		<li><p>First list item in nested unordered list</p>
		<p>Second paragraph of the first list item in the 
		nested list.</p></li>
		<li><p>Second list item in next unordered list</p></li>
		</ul></li>

	<li>Third list item in unordered list</li>
	</ul>

and renders as:

*  First list item in unordered list
*  Second list item in unordered list
   -  First list item in nested unordered list

	 Second paragraph of the first list item in the 
	 nested list.

   -  Second list item in next unordered list
*  Third list item in unordered list

In the HTML code above for the unordered list, notice how list items with 
a second paragraph or a blank line above or below the item are wrapped in 
paragraph `<p>` tags.

Ordered lists are marked up by including a number followed by a period as 
the first characters on a line. Again, the 3-space max indent holds. The 
order of the numbers in source text does not matter, although the author 
of _Markdown_ suggests beginning with 1., just in case _Markdown_ ever allows 
numbering beginning with other than 1. For example, this markup:

	1.  First item of ordered list
	2.  Second item of ordered list
		6.  First item of nested ordered list
		2.  Second item of nested ordered list 
	2.  Third item of ordered list

is converted to:

	<ol>
	<li>First item of ordered list</li>
	<li>Second item of ordered list
	<ol>
		<li>First item of nested ordered list</li>
		<li>Second item of nested ordered list </li>
	</ol></li>
	<li>Third item of ordered list</li>
	</ol>

and renders as:

1.  First item of ordered list
2.  Second item of ordered list
   6.  First item of nested ordered list
   2.  Second item of nested ordered list 
2.  Third item of ordered list


<h2 id="lnk"> Links </h2>

There are several ways to markup links in _Markdown_. The basic inline markup 
is:

	[Link text](URL "Optional title")

The URL can be an internal named anchor or an element ID preceded by a hash 
mark (`#`).

Links can also use a reference style markup to keep from cluttering up the 
source text with lengthy and complicated URLs:

	[Link text] [reference_id]

or

	[Link text] []

The URL is specified anywhere in the document after the link markup and may 
be relative or absolute. For the markup using a reference text (e.g., reference\_id 
above), the URL is associated with the reference_id like this:

	[reference_id]: URL "Optional title"

For markup using an "empty" reference text set of brackets, the "Link text" 
serves as the reference text for the URL:

	[Link text]: URL "Optional title"

I like to list the link references at the end of the document, like endnotes. 
I think it keeps the source text cleaner, i.e., more readable. You can see 
the link references for this document by scrolling to the end of the [source 
text] [2].


<h2 id="img"> Images </h2>

Images are inserted into the _Markdown_ markup in a manner similar to links, 
but using an exclamation point at the beginning of the line. It works well 
for a simple, inline image. 

	![Image text](URL "Optional title")

Images can also use the same style as reference links:

	![Image text] [reference_id]

with the URL linked to the reference_id thusly:

	[reference_id]: URL "Optional title"

If you need to have more control over image positioning or size, it is best 
just to use the HTML `<img>` tag and styling.


<h2 id="pre"> Preformatted Blocks and Spans </h2>

_Markdown_ makes it easy to write about HTML and other code. To wrap a block 
text in `<pre><code>` tags, simply indent each line by at least 4 spaces 
or 1 tab.  Thus:

	Normal indent paragraph

		Preformatted block of text
		that displays code such as
		<h1>Heading</h1> with the angle
		brackets converted to entities.

	Back to normal paragraph

is converted to:

	<p>Normal indent paragraph</p>

	<pre><code>Preformatted block of text
	that displays code such as
	&lt;h1&gt;Heading&lt;/h1&gt; with the angle
	brackets converted to entities.</code></pre>

	<p>Back to normal paragraph</p>

and renders as:

Normal indent paragraph

	Preformatted block of text
	that displays code such as
	<h1>Heading</h1> with the angle
	brackets converted to entities.

Back to normal paragraph

Code spans are inserted in source text by enclosing the text string in backticks. 
For example:

	To include a literal backtick in an `<h1>Heading</h1>`
	string, you must use 5 backticks, which looks like `` ` ``

is converted to:

	<p>To include a literal backtick in an 
	<code>&lt;h1&gt;Heading&lt;/h1&gt;</code> string,
	you must use 5 backticks, which looks like <code> ` </code></p>

and renders as:

To include a literal backtick in an `<h1>Heading</h1>` string,
you must use 5 backticks, which looks like `` ` ``


<h2 id="lit"> Literal Characters </h2>

The _Markdown_ markup characters can be inserted literally in the rendered 
page by escaping with a backslash before the markup symbol. Thus to insert 
a literal underscore character:

	Insert a backslash before the underscore character
	to insert a literal underscore like this \_

renders as:

Insert a backslash before the underscore character to insert a literal underscore 
like this \_


<h2 id="oth"> Other Features </h2>

_Markdown_ includes a neat feature for clickable e-mail addresses. Enclose 
the address in the source text with angle brackets and some encoding will 
result, which serves as a low-level spam barrier. Some spam bots will probably 
break the code, but it is better than nothing. For example:

	<name@domain.com>

is converted to:

	<p><a href="&#x6d;&#x61;&#x69;&#x6c;&#x74;&#x6f;:&#x6e;&#x61;
	&#x6d;&#x65;&#x40;&#x64;&#x6f;&#x6d;&#x61;&#x69;&#x6e;&#x2e;
	&#x63;&#x6f;&#x6d;">&#x6e;&#x61;&#x6d;&#x65;&#x40;&#x64;&#x6f;
	&#x6d;&#x61;&#x69;&#x6e;&#x2e;&#x63;&#x6f;&#x6d;</a></p>

and renders as clickable e-mail address:

<name@domain.com>

Similarly, if you enclose a web address in angle brackets:

	<http://domain.com/index.html>

it converts to:

	<p><a href="http://domain.com/index.html">
	http://domain.com/index.html</a></p>

and renders as a clickable web address:

<http://domain.com/index.html>


<h2 id="exc"> Exceptions to _Markdown_ in WriteMonkey </h2>

WriteMonkey's implementation of _Markdown_ includes a few exceptions in markup 
to the original Markdown script. These are listed below.

   * Single asterisks (`*phrase*`) produce *bold* in
     WriteMonkey, _italic_ in Markdown.
   * Double underscores (`__phrase__`) produce
     __underline__ in WriteMonkey, *bold* in Markdown.
   * In addition to _Markdown's_ standard markup for a
     horizontal rule, three or more plus signs (`++  +`)
     in WriteMonkey produce a `<hr />`. 



[1]: http://daringfireball.net/projects/markdown/syntax/

[2]: ./mda.txt

[3]: http://daringfireball.net/projects/markdown/
