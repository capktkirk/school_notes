Expressions Exploration :

Inheritance Hierarchy :

Why are we doing this style:
  Less "Decision" making, less branching.

Different Subject regarding Expressions :

int main()
{
  char array[6];
  float flarray[6];
  array[0] = 'G';
  array[1] = 'r';
  array[2] = 'a';
  array[3] = 'p';
  array[4] = 'e';
  array[5] = '\0';

  cout << array[2] << endl;

  unsigned longaddr = reinterpret_cast<unsigned long>(array); 
  cout << addr << endl;
  unsigned long larger = addr+2;
  char* char_offset = reinterpret_cast<char*>(larger);
  cout << *char_offset << endl;


}


In GPL the [   ] comprose an operator.
Binary operator. 

What we could do :

Constant* Subscript::evaluate() //evaluate lhs[rhs]
{
  Gpl_type lht = lhs->type();
  Gpl_type rht = rhs->type();
  Constant* lhs_constant = lhs->evaluate();
  Constant* lhs_constant = lhs->evaluate();
  Integer_constant( *(lhs_constant->as_int() + rhs_constant->as_int());
}


cout << *(array + 2) << endl;
cout << *(2 + array) << endl;
cout << 2[array] << endl;
cout << 2["Grape"] << endl;

All will print out a.


char*a = "This is a "
         "set of strings "
         "appended together.";

This creates one string.



Project 4 : 
  The addition of the game objects (3 Shapes, Pixmap, Textbox)
  We will be working with game objects.
  Interacting with objects will be done with attribute_type, write_attribute, read_attribute
  Symbol will grow a fair amount with this project for the five new objects.
  Variable will need to have support for the five game objects.
  Derive a class from Variable named member_variable depending on the item.


