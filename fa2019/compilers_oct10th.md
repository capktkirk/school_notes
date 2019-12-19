line 211, gpl.y

int x = 33;
33 is a const object

T_ASSIGN expression

primary_expression:
  T_LPAREN expression T_RPAREN
  |variable
  | T_INT_CONST {$$=new Integer_constant($1)}
  | T_TRUE
  | T_FALSE
  | T_DOUBLE_CONSTANT
  | T_STRING_CONSTANT

  in union add :
  Expression* union_expression_ptr;

  add another type

  %type <union_expression_ptr> primary_expression

get what $3 contains to the integer.
member_function in integer_constant class:
  as_int()
  as_double()
  as_string()

Expression member function:
  evaluate()
  
  
  
we have an expression pointer, $3 (in the switch case is an expression pointer
$3->

int vl;
vl=$3->evaluate()->as_int();

Lfeav , owe rysdyierty eftmo.ano tr,l ooahpo orrme fdorr
12345678901234567890123456789012345678901234567890123456

