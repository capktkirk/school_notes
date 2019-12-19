  Scanner focused on RegEx:
  How does this serve as input to the parsing side :
  context free grammars
  All programming languages based on context free grammar
  (contrasted by context sensitive grammar)

  terminal symbols/tokens, terminals
  non-terminal symbols/tokens

  ex:
  for
  while
  int
  "fdsa"

  Production :
    will always have :
    non-terminal symbol ->, ::->, :
    example :
    non-terminal: rule1 | rule2 | rule3
    non-terminal: rule1 { action } | rule2 { action } | rule3 { action }

    Production Example : expr == expression, op == operator 
    //speaking in a textbook sense
    start symbol :
    start_sym : empty | expr
    //another rule you can have
    //start_sym: empty means that a blank line is valid as well Only one start symbol by definition.

    //EXPRESSION EXAMPLE :
    expr: T_INT_CONST
    expr: T_LPARENT expr T_RPAREN
    expr: expr op expr

    //OPERATION EXAMPLE :
    op: T_PLUS
    op: T_MINUS
    op: T_MULTIPLY
    op: T_DIVIDE
    //////// or
    op: T_PLUS | T_MINUS | T_MULTIPLY | T_DIVIDE

    IN BISON we're going to create a grammar. Bison side is where we determine validity

    Polish calculatr AKA postfix calculator :
    3 + 4 * 7 same as 3 4 + 7 *

    yytext is a global variable that contains the text that is matched
    no memory leaks in first few programs.
