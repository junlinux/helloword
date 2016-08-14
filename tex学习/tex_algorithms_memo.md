### Introduction
- two environments:algorithmic,algorithm

### The algorithmic environment
- simple statement
	> \STATE <text>
- if-then-else statement
	> \IF{...} <text> \ELSE <text1> \ENDIF
- for loop
	> \FOR{...} <text> \ENDFOR
	> \FORALL{...} <text> \ENDFOR
- to connective 
	> \TO
- while loop
	> \WHILE{...} <text> \ENDWHILE
- repeat-until loop
	> \REPEAT <text> \UNTIL{...}
- infinite loop
	> \LOOP <text> \ENDLOOP
- logical connective
	> \AND  \OR  \XOR  \NOT
- precondition
	> \REQUIRE <text>
- postcondition
	> \ENSURE <text>
- return value
	> \RETURN <text>
- true,false value
	> \TRUE  \FALSE
- printing messages
	> \PRINT <text>
- comments
	> \COMMENT{<text>}

### options and customization
- changing indentation
	> \algsetup{indent=length}
- changing line numbering size
	> algsetup{linenosize=size}
	> algsetup{linenodelimiter=delimiter}
- customization
	> \renewcommand{\algorithmicrequire}{\textbf{Input:}}
	> \renewcommand{\algorithmicensure}{\textbf{Output:}}
	> \renewcommand{\algorithmiccomment}[1]{// #1}

### the algorithm environment

### options


### labels and references in algorithms 

### hints for typesetting algorithms
- don't overcomment your pseudo-code.
- similarly,don't regard pseudo-code as a low-level programming language
- always document what the algorithm receives as an input and what it returen as a solution
- if you feel your pseudo-code is getting too big ,just break it into subalgorithms
