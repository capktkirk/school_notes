Follow-up notes:

switch statement : default case required with gpl_type

default case shuts the compiler up, but it also introduces potential debugging headaches. 

General debugging proposition

#include <iostream>
#include <cassert>


using namespace std;
int main() {
  int var=3;
  switch(var)
  {
    case 1:
    {
      cout << "one\n";
      break;
    }
    case 2:
    {
      cout << "two\n";
      break;
    }
    default:
    {
      assert(false);
      break;
    }
  }
  return 0;
}



const member functions :

operator[] doesn't have a const version


