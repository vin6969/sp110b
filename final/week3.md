A high-level language is a programming language designed to simplify computer programming. It is "high-level" since it is several steps removed from the actual code run on a computer's processor.
High-level source code contains easy-to-read syntax that is later converted into a low-level language, which can be recognized and run by a specific CPU.

Most common programming languages are considered high-level languages. Examples include:

* C++
* C#
* Cobol
* Fortran
* Java
* JavaScript
* Objective C
* Pascal
* Perl
* PHP
* Python
* Swift

Each of these languages use different syntax. Some are designed for writing desktop software programs, while others are best-suited for web development.
But they all are considered high-level since they must be processed by a compiler or interpreter before the code is executed.

#### source
https://techterms.com/definition/high-level_language


### BNF
* It stands for Backus-Naur Form
* It is a formal, mathematical way to specify context-free grammars
* It is precise and unambiguous
* Before BNF, people specified programming languages ambiguously

#### example code for BNF

### EBNF
* Stands for “Extended Backus-Naur Form”
* EBNF is a few simple extensions to BNF which make expressing grammars more convenient
* EBNF is no more “powerful” than BNF; that is, anything that can be expressed in EBNF can also be expressed in BNF


### BNF vs EBNF

#### BNF code
```
<expr> ::= '-' <num> | <num>
<num> ::= <digits>
| <digits> '.' <digits>
<digits> ::= <digit>
| <digit> <digits>
<digit> ::= '0' | '1' | '2' | '3' |
'4' | '5' | '6' | '7' | '8' | '9'
```
### EBNF code
```
<expr> := '-'? <digit>+ ('.' <digit>+)?
<digit> := '0' | '1' | '2' | '3' | '4' |
'5' | '6' | '7' | '8' | '9' 
```










