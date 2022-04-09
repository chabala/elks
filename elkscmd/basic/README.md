ELKS Sinclair Basic
======================
From Robin Edwards' ArduinoBASIC (https://github.com/robinhedwards/ArduinoBASIC).

A complete BASIC interpreter for your 80's home computer! The BASIC supports almost all the usual features, with float and string variables, multi-dimensional arrays, FOR-NEXT, GOSUB-RETURN, etc.

BASIC Language
--------------
Variables names can be up to 8 alphanumeric characters but start with a letter e.g. a, bob32
String variable names must end in $ e.g. a$, bob32$
Case is ignored (for all identifiers). BOB32 is the same as Bob32. print is the same as PRINT

Array variables are independent from normal variables. So you can use both:
```
LET a = 5
DIM a(10)
```
There is no ambiguity, since a on its own refers to the simple variable 'a', and a(n) referes to an element of the 'a' array.

```
Arithmetic operators: + - * / MOD
Comparisons: <> (not equals) > >= < <=
Logical: AND, OR, NOT
```

Expressions can be numerical e.g. 5*(3+2), or string "Hello "+"world".
Only the addition operator is supported on strings (plus the functions below).

Commands
```
PRINT <expr>;<expr>... e.g. PRINT "A=";a
LET variable = <expr> e.g. LET A$="Hello"
variable = <expr> e.g. A=5
GOTO lineNumber
REM <comment> e.g. REM ** My Program ***
STOP
CONT (continue from a STOP)
INPUT variable e.g. INPUT a$ or INPUT a(5,3)
IF <expr> THEN cmd e.g. IF a>10 THEN a = 0: GOTO 20
FOR variable = start TO end STEP step
NEXT variable
GOSUB lineNumber
RETURN
DIM variable(n1,n2...)
CLS
PAUSE milliseconds
POSITION x,y sets the cursor
NEW
LIST [start],[end] e.g. LIST or LIST 10,100
RUN [lineNumber]
LOAD "filename" from filesystem
SAVE "filename" to filesystem
SAVE+ "filename" to filesystem, set auto-run on load
DELETE "filename" from filesystem
DIR

Architecture-specific
PIN pinNum, value (0 = low, non-zero = high)
PINMODE pinNum, mode - not implemented

Not yet implemented
POKE offset,segment,value
OUT port,value
RANDOMIZE [nmber]
READ var
DATA
RESTORE [line]
INPUT [prompt,] variable
PRINT <expr>,<expr> (tab separated output)
MODE number (set graphics mode)
COLOR fg[,bg]
PLOT x,y
DRAW x,y[,a]
CIRCLE x,y[,r]
```

"Pseudo-identifiers"
```
INKEY$ - returns (and eats) the last key pressed buffer (non-blocking). e.g. PRINT INKEY$
RND - random number betweeen 0 and 1. e.g. LET a = RND
PI - 3.1415926
```

Functions
```
LEN(string) e.g. PRINT LEN("Hello") -> 5
VAL(string) e.g. PRINT VAL("1+2")
INT(number) e.g. INT(1.5)-> 1
ABS(number) e.g. ABS(-1)-> 1
STR$(number) e.g. STR$(2) -> "2"
LEFT$(string,n)
RIGHT$(string,n)
MID$(string,start,n)
COS(x)
SIN(x)
TAN(x)
ACS(x)
ASN(x)
ATN(x)
EXP(x)
LN(x)
POW(x,y) e.g. POW(2,0.5) -> 1.414 square root of 2

Architecture-specific
PINREAD(pin)
ANALOGRD(pin) - not implemented

Not yet implemented
SGN(number) e.g. SGN(-1) -> -1
CHR$(number) e.g. CHR$(32) -> " "
CODE(string) e.g. CODE(" ") -> 32
PEEK(offset,segment) - not yet i
IN(port)
SCREEN$(line,col)
ATTR(line,col)
POINT(x,y)
```