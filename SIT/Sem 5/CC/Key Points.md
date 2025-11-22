
Compiler is divided into 2 parts: 
- [Analysis](e-book.pdf#page=27&selection=62,0,63,39|e-book, page 27)
- [Synthesis](e-book.pdf#page=27&selection=70,0,71,60|e-book, page 27)



## Lexical Analysis

- converts input stream into lexemes, which are then converted into tokens
- updates values in the symbol table
## Syntax Analysis

- reads the input from the lexical analysis and creates a parse tree
- represents the grammatical structure of a language
- typical representation is a syntax tree in which each interior node represents an operation and the children of the node represent the arguments of the operation

> [!Note] Example : 
> - Define Precedence
> - `For/While` loop structures

## Semantic Analysis

- Takes syntax tree and symbol table to check for semantic consistency according to language definitions
- outputs an annotated parse tree 

Type Checking:
- integer array index
- arithmetic between numbers

## Intermediate Code Generation

- process of translating a source program into target code may construct one or more intermediate representations, for example : Syntax trees
- syntax trees generate low level, machine like, explicit language

Properties it should have:
- easy to produce
- easily convertible in target language


# TO DO: 
- [ ] Context Free grammar: 
	- Left factoring
	- Ambiguity checking
	- Elimination of left recursion


### Left Recursion:



$$
\begin{aligned}
S \to A\alpha | B \\
\\

\text{then:}
\\
\\

A \to BA'
\\
A' \to \alpha A' | \in
\end{aligned}
$$

