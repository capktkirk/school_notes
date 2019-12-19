lx - lexical analysis "lexer" or "Scanner
yacc - "yet another compiler compiler"

flex - modern equivalent of above
bison - modern equivalent of above

.l (lowercase "ell") extension used by flex
.y extension used by bison

scanner side only today : 

#include<iostream>

using namespace std;

int main()
{
  cout << "Hello!\n";
  return 0;
}

//AFTER LEXER
/*
"tokens"
INT_TYPE ...ER(using) T_IDENTIFIER(namespace) T_IDENTIFIER(std)
*/

regex :
regexr.com
//gm in the parser sometimes is used like in sed, expression goes inbetween slashes
search for two different things with | 
in square braces any of these characters [characters]
the negation character is ^
range == [A-Z] (all upper case)
range == [A-Za-z] (all letters)
modifiers : 
[^fdsa] negation only if first character
a* (0 or more a's)
a*p (0 or more a's followed by a p)
^is outside of the braces is at the beginning of the line.
is$ at the end of a line
a+p means one or more a before p
\ is escape character

IN CLASS WORK :
/apple/gm
/apple|banana/gm
/\d*/gm
/-?\d+/gm
/[^3Xj-p]/gm
/the$/gm
/^the/gm
######/([a-zA-Z0-9])\1/gm
######/(\+|-)?\.?[0-9]+\.?[0-9]*/gm
/[-+]?\d+\.\d*|?\d*\.\d+/gm


