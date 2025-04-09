# L2.1 - Information representation in a machine

* Computers work only with "bits" (0s and 1s)
* Numbers
	* Place value: binary numbers => 6->0110
	* 2s complement => -6->1010

## Information interchange
* communication through machines (machine-machine or machine-human) only done in bits
* Standard encoding
	* some sequence of bits interpreted as a character
### Representing text
* ASCII
	* American standard code for information interchange
	* 7 bits - 128 different entities
	* later extended to 8 bits by europeans as european languages had accents, extending the limit to 256 characters
* Unicode
	* Allows codes for more scripts, characters
	* Universal Character Set - UCS
		* UCS2, 2 bytes per character -> max 65536 characters
		* UCS4. 4 bytes per character -> max 4billion
* UTF-8
	* Use 8 bits for most common characters - ASCII subset
		* All ASCII Documets are automatically UTF-8 compatible
	* All other characters can be encoded based on prefix string
	* More difficult for text processor
		* First check prefix
		* linked list through chain of prefixed possible
		* still more efficient for majority documents
	* Most common encoding in use today

# L2.2 - Efficiency of encoding
* Using UCS-4 - 5000 characters - 160,000 bit
* Using 8 bit ASCII - 40,000 bit
* Using 7 bitt ascii - 35,000 bit
* only encoding 'a' - 'z' and special characters, 6 bits - 30,000 bits
* Optimal coding based on frequency of occurence
	* Huffman or similar encoding - 10-20,000 bits

# L2.3 - Markup
## What is markup?
it is a way of using cues of codes in the regular flow of text to indicate how text should be displayed. Markup is very useful to make the display of text clear and easy to understand.
Eg: LaTeX

What we see in markup is known as semantics - content vs presentation
*Semantics* - meaning of text vs structure of logic of the document
### Types of markup
* Presentational
	* WYSIWYG: directly format output and display
	* Embed codes not part of regular text, specific to editor
* Procedural
	* details on how to display
		* change font, large, bold
		* skip 2 lines, indent 4 columns
* Descriptive
	* HTML like tags

# L2.4 - HTML
First used at CERN
Considered an application of SGML (Standard General Markup Language)
* very strict
HTML meant for browser interpretation
* very forgiving, loose validity checks

# L2.5 - Intro to Styling

-

# L2.6 - Types of CSS and Response Websites

## Inline CSS
* Directly add style to the tag
```
<h1 style='color:blue;text-align:center;'>	
```

## External CSS
* Extract common content for reuse
* Multiple CSS files can be included

## Responsive Design
* Adapt to scren - respond

## Bootstrap
* Commonly used framework
	* Originated from twitter
	* widely used
* Standard styles for various components
	* Buttons
	* Forms
	* Icons
* Mobile first: highly responsive layout

## Javascript
* Interpreted language brought into the browser
* Formally ECMAScript - Not really related to java
* Need cuz HTML, CSS aren't programming language
* programmability important

## CSS
```
<link red='stylesheer" href="">

# HTML form items
<input>
types: text, button, radio etc.

# id in CSS
#id {

}

# class in css
.class {

}

#child of a certain element
form > input {
# input child of every form
}

:hover 

nth-cild(#!)
can be odd even or any specific number 

```