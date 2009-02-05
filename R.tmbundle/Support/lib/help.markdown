# Introduction

R is a language and environment for statistical computing and graphics. It is a [GNU project](http://www.gnu.org/) which is similar to the S language and environment which was developed at Bell Laboratories (formerly AT&T, now Lucent Technologies) by John Chambers and colleagues. R can be considered as a different implementation of S. There are some important differences, but much code written for S runs unaltered under R.

R provides a wide variety of statistical (linear and non-linear modeling, classical statistical tests, time-series analysis, classification, clustering, ...) and graphical techniques, and is highly extensible. The S language is often the vehicle of choice for research in statistical methodology, and R provides an Open Source route to participation in that activity.

(Text taken from [What is R?](http://www.r-project.org/about.html))

More information about R can be found at [r-project.org](http://www.r-project.org/).
       
# Commands

## Run Selection/Document In R
<button>&nbsp;&#x2318;R&nbsp;</button>
It executes the current document or selection in a self-sufficient environment of the command-line version of R and it displays the output in an HTML window. By default new plots use the "pdf" device and are placed in a temporary folder and displayed at the end of the HTML window.

## Execute Selection/Document In R (Tooltip/Insert)
<button>&nbsp;^&#x2318;R&nbsp;</button>
It executes the current document or selection in a self-sufficient environment of the command-line version of R. The output will be displayed as Tooltip or will be inserted.

## Send Selection/Document to Rdaemon
<button>&nbsp;&#x21E7;&#x2318;R&nbsp;</button>
It sends the current document or selection line by line to the Rdaemon. If Rdaemon is not yet running it will start it, it opens the Rsession project, and the file `~/Rdaemon/console.Rcon` will contain the output.

***Hint*** To use that command you have to install the Rdaemon Bundle in beforehand.

## Send Selection/Document to R.app
<button>&nbsp;&#x2325;&#x21E7;&#x2318;R&nbsp;</button>
It executes the current document or selection in R.app and switches to R.app's Console.

***Hint*** To use that command you have to install R.app in beforehand.

## Completion…
<button>&nbsp;^.&nbsp;</button>
Based on all installed packages and local function declarations it shows an inline menu with completion suggestions for the current word or selection as <code style="background-color:lightgrey;color:black">&nbsp;command&nbsp;{library}&nbsp;</code>. The library `local` refers to functions defined within the current document.

As default it also displays an inline menu if there is only one suggestion found in order to give you an hint for the required library. You can force TextMate to complete it without displaying that menu by setting the shell variable `R_AUTOCOMPLETE` to `1`.

***Hint*** This command works case-sensitively. E.g. if you type `math` (without selection and there is no command beginning with `math`) and invoke this command it lists all case-insensitive matched commands like `Math.fraction`, etc. as a tooltip caused by the chosen "Insert as Snippet" mechanism.

## Show R Help for actual Word/Selection
<button>&nbsp;^H&nbsp;</button>
It shows an HTML document with the found R help for the current word or of that command in which the caret is located. If no help file is found it opens an HTML window with all found keywords beginning with the current word. Furthermore this help window offers a `Search for` field. It allows to search for a term within

* all `keywords` meaning all commands, aliases, and descriptions of a command
* all man help pages as `full text`

***Hint*** Both search functions make usage of `egrep -i`, and the search term will be interpreted as regular expression. This also means that the search is line-oriented and case-insensitive.
    
## Show Function Usage
<button>&nbsp;&#x2325;&#x21E7;H&nbsp;</button>
Based on all installed packages and local function declarations it shows a tooltip with the function signature for the current word &mdash; or that command in which the caret is located in respect of nested parentheses &mdash; or of the selection.

## Show Function Usage + Insert “(”
<button>&nbsp;(&nbsp;</button>
Based on all installed packages and local function declarations it shows a tooltip with the function signature for the current word and it inserts “()” or “(”.

***Hint*** This functionality can be switched off by deactivating the bound key equivalent within in the Bundle Editor.

## Create Command Help Index

It creates the index files `$TM_BUNDLE_SUPPORT/help.index` and `$TM_BUNDLE_SUPPORT/help.pkgs` based on **all installed packages** which are needed by the following commands:

* Show R Help for actual Word/Selection
* Show Function Usage
* Insert Function Parameter…
* Function Completion…

***Hint*** These index files will be built automatically if one of the above mentioned commands will be executed for the first time or if you removed or installed packages. There won't be a rebuilt if one updates a package.

## Function Parameter…
<button>&nbsp;^,&nbsp;</button>
It shows an inline menu with all available parameters and inserts a snippet with the chosen one(s). This command also tries to figure out whether it is necessary to insert a comma “, ”. If the inserted comma “, ” is set falsely one can press <button>&#x21E5;</button> twice to highlight it.

***Hint*** It is possible the write its own parameter list for a given function. This list has to be saved in `$TM_BUNDLE_SUPPORT/lib/command_args` and its name represents the function name.

See here an example for <a onclick="document.getElementById('plot').style.display=(document.getElementById('plot').style.display=='')?'none':''" href="#">`$TM_BUNDLE_SUPPORT/lib/command_args/plot`</a>:

<pre id="plot" style="display:none">
	asp="y/x aspect ratio"
	log="x|y|xy|yx"
	main="title"
	sub="subtitle"
	type="p|l|b|c|o|h|s|S|n"
	xlab="x-title"
	xlog=TRUE
	ylab="y-title"
	ylog=TRUE
</pre>

## “par()” Parameters…
<button>&nbsp;^;&nbsp;</button>
It shows an inline menu with all parameters defined in `$TM_BUNDLE_SUPPORT/lib/command_args/par` and inserts a snippet with the chosen one(s). This command also tries to figure out whether it is necessary to insert a comma “, ”. If the inserted comma “, ” is set falsely one can press <button>&#x21E5;</button> twice to highlight it.

## “require(xxx)” for current Function
<button>&nbsp;^&#x21E7;L&nbsp;</button>
It looks for that package in which the current keyword &mdash; "()" will be recognized &mdash; is defined, and it inserts the R code to load that package `require(PACKAGE)` above the current line.

## Package Name…
<button>&nbsp;&#x2325;&#x21E7;&#x2318;L&nbsp;</button>
It shows all installed packages as an inline menu.

## Option List as Pull Down… / BoolToggler
<button>&nbsp;^F12&nbsp;</button>
This is an auxiliary tool command with these two different tasks based on a selection:

* It negates the logical value if the selection is "FALSE" or "TRUE".
* It shows an inline menu of all values which are selected and delimited by "|" and replaces the selection by the chosen one.

  For instance this is useful after inserting the parameter `method` of the R function `dist`.<br>The selected value is:<br>
&nbsp;&nbsp;&nbsp;`euclidean|maximum|manhattan|canberra|binary|minkowski`

  or if the selected value (like for `par`, parameter `font.lab`) is:<br>
&nbsp;&nbsp;&nbsp;`1-plain|2-bold|3-italics|4-bolditalics`

  it only inserts the according digits.

## Create Vector from Selection
<button>&nbsp;^&#x2325;C&nbsp;</button>
It inserts a vector in the form of `x <- c(x1, x2, ...)` as snippet taken from a selected string or the current content of the clipboard. Delimiters are " ", "&#x21A9;", or "&#x21E5;". If an element doesn't consist of digits the element will be enclosed by double-quotes.

## Next/Previous List Element/Parameter Value
<button>&nbsp;^&#x2325;&#x2192;&nbsp;</button><button>&nbsp;^&#x2325;&#x2190;&nbsp;</button>
It tries to highlight the next/previous element (if quoted only the content) of a list/vector or the value of function parameters.

## Tidy
<button>&nbsp;^&#x21E7;H&nbsp;</button>
It tidies the selection or the entire document by deparsing them on-the-fly using the command-line version of R. General syntax errors will be displayed as tooltip and the caret will be moved to the first error.

***Attention*** All comments will be deleted!

***Hint*** This command can also be used as a kind of `Syntax Checker`. It only checks the R code for general syntax error like missing brackets, or commas, etc. It does **not** check for semantic errors like if a variable was assigned correctly or not.

## Function Call
<button>&nbsp;^&#x21E7;W&nbsp;</button>
It inserts: &nbsp;&nbsp;&nbsp;<code><span style="background-color:lightblue;color:black">sum</span>(SELECTION/WORD)</code> as snippet.

## Function Definition
<button>&nbsp;^&#x21E7;&#x2318;W&nbsp;</button>
It inserts:<br><pre>	x <- function(var) {
		SELECTION/WORD
	}
</pre> as snippet.

## Drag&amp;Drop Facilities
-   __load (*.Rdata)__

	If a `*.Rdata` file is drag&amp;dropped to a R/R console document it inserts:
	
	`load(FILE)`.
	
	By pressing SHIFT while dragging it inserts the absolute file path.

-   __source (*.R)__

	If a `*.R` file is drag&amp;dropped to a R/R console document it inserts:
	
	<code>source(FILE, chdir = <span style="background-color:lightblue;color:black">TRUE</span>)</code>.
	
	By pressing SHIFT while dragging it inserts the absolute file path.

-   __read.csv (*.csv)__

	If a `*.csv` file is drag&amp;dropped to a R/R console document it inserts:
	
	<code>read.csv(file = FILE, header = <span style="background-color:lightblue;color:black">TRUE</span>, stringsAsFactors = <span style="background-color:lightblue;color:black">FALSE</span>)</code>.
	
	By pressing SHIFT while dragging it inserts the absolute file path.

-   __read.table (*.tab)__

	If a `*.tab` file is drag&amp;dropped to a R/R console document it inserts:
	
	<code>read.table(file = FILE, sep = <span style="background-color:lightblue;color:black">\t</span>, header = <span style="background-color:lightblue;color:black">TRUE</span>, stringsAsFactors = <span style="background-color:lightblue;color:black">FALSE</span>)</code>.
	
	By pressing SHIFT while dragging it inserts the absolute file path.

# Shell Variables

## R&#95;AUTOCOMPLETE

As default TextMate displays an inline menu if there is only one suggestion found in order to give you an hint for the required library. You can force TextMate to complete it without displaying that menu by setting the shell variable `R_AUTOCOMPLETE` to `1`. See also [Completion…](#sect_2.5).

# Troubleshooting &amp; FAQ

-   __`'re-encoding is not available on this system'` or `'object ".PSenv" not found'`__

    If you see one of these messages then you are most likely using an older version of R. In this case you should upgrade to the latest (currently, version 2.6.1) by downloading the pre-built universal R.app installer from <a href="http://www.r-project.org">r-project.org</a>.

-   __`115:116: syntax error: Expected end of line, etc. but found “. (-2741)`__

    If you see such an error (or similar) while sending something to "R.app" it is very likely that you are also running the "Rdaemon" with loaded "CarbonEL". Unfortunately "CarbonEL" uses the same application name "R", thus the AppleScript will send the R code to it, not to "R.app". In such a case you have to quit the Rdaemon.
    
-   __After updating a R package new commands are not found by "Completion…", "Show Command Usage", etc.__

    The help index files will only be rebuilt if these don't exist or if one removed/installed R packages. An update of a package won't be recognized. Run "Create Command Help Index" manually.

# The bundle "R Console (Rdaemon)"

In addition there is the bundle "R Console (Rdaemon)" available. This bundle allows to run the command-line version of R ***inside*** TextMate. A normal document window, which is set to the language "R Console (Rdaemon)", serves as R console. More details within this bundle.  

# The bundle "R Console (R.app)"

In addition there is the bundle "R Console (R.app)" available. This bundle allows to remote the Mac OSX GUI "R.app". More details within this bundle.  

# Main Bundle Maintainer

***Date: Mar 06 2008***

<pre>
-  Charilaos Skiadas&nbsp;<a href="mailto:cskiadas@gmail.com">cskiadas@gmail.com</a>
-  Hans-Jörg Bibiko&nbsp;&nbsp;<a href="mailto:bibiko@eva.mpg.de">bibiko@eva.mpg.de</a>
</pre>

