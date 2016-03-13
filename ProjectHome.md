## The Relational Algebra project: ##

<ul>
<li>includes an <b>interactive interpreter</b> that can perform relational algebra operations.</li>
<li>self contained and standalone, does not require a connection to a database</li>
<li>implements a <b>re-usable Java class</b> that models relations and relational operators.</li>
<li>provides static methods that can parse relational algebra expressions and evaluate them against relations.</li>
</ul>

About the author: http://uk.linkedin.com/pub/nick-everitt/24/296/67/

The idea behind the Relational Algebra project is that it is easier to understand relational algebra if you can experiment with the different operators.  I looked at some of my solutions and thought 'if only I could just run this with some test data to see if it works'.

The interpreter handles select, project, join, divide, rename, union, difference, intersection, alias and times.

**Update 27th September 2012:** Version 0.3 now allows commands and results to be echoed to a log file.  Logged commands, followed by their output, are numbered sequentially to assist with commentary.

**Update 20th April 2011:** Version 0.2 includes a built-in editor.  This allows relations to be created and edited from within the interpreter itself.  To start the editor evaluate **edit** <i>relation</i>.  For example, 'edit myrelation'.  This will begin an editing session and will also create the relation if it does not already exist.  The editor will also load and save to CSV files using file dialogs. There are more details on using the editor in the instructions documentation.

**Update:** Infinite command history is here.  Use Ctrl-up arrow and Ctrl-down arrow to browse command history.

The ability to load relations in from a CSV file  has been retained (first row attribute names, second row domain names, subsequent rows values - see example in instructions).  But then you can create new relations from it using relational algebra.

For example,

rela **:= load** "/home/nick/my-rela.csv"

Then:

**select** rela **where** a > 2

**project** rela **over** a, b, c

**project** (**select** rela **where** a > 2 **or** b <= 5) **over** a, b

It also handles assignment, so:

relb **:= project** rela **over** a, b, c

Which creates a new relation called relb.

Loads more examples in the documentation along with some example CSV files and how to make your own.

<u>Hint:</u> in the interpreter use enter to get a newline (for long expressions) and use ctrl-enter to evaluate.

The project is written in Java and has a re-usable class called Relation that does all the work.  It's free for anyone that wants to use it.

The interpreter itself is a JAR file called "raeval.jar" and is available under the downloads tab.  To run it you need the Java Runtime Environment that is also available free.  I have had it up and running on Windows, Mac and Ubuntu Linux.

There are some (really) basic instructions in the Downloads too together with a screenshot.

Note: this is beta software.  The functionality has been tested but there probably are some bugs left.  Contact me if you spot them.  But please be gentle, because this has been an obsession...


## Relational operators supported: ##

**select** <i>relation</i> **where** <i>condition</i>

**project** <i>relation</i> **over** <i>attribute</i> {, <i>attribute</i>, ... }

<i>relation</i> **join** <i>relation</i>

<i>relation</i> **rename** (<i>attribute</i> **as** <i>newname</i> ...)

**divide** <i>relation</i> **by** <i>relation</i>

<i>relation</i> **union** <i>relation</i>

<i>relation</i> **difference** <i>relation</i>

<i>relation</i> **times** <i>relation</i>

<i>relation</i> **alias** <i>relation</i>

## Non-relational operators supported: ##

+ - `*` / and or not < > = <= >= <>

<i>relation</i> := <i>relation</i>      (assignment)

**show** <i>relation</i>

**load** <i>filename</i>

## Additionally in the interpreter: ##

**help**

**help** <i>keyword</i>

**edit** <i>relation</i>

**log** <i>filename</i>     (also starts logging)

**log start**

**log stop**

**quit**