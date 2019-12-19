
Notes:

##C++ Classes and features we will now be using regularly.
  * Constructors
  * Initialization LIsts
  * Passing complex types by reference/const reference
  * Constructors with unions
  * suppressing compiler-generated member functions (of classes)
  * singletons
  * smart pointers(i.e., std::shared_ptr and std::makeshared)
  * Memory handling in general.


This is all C++, nothing to do with compilers, we're going to be preparing to work with this in a compiler.

Twenty minute video on constructors and initialization lists on class website. Video bits on Blackboard.

One thing that is easy to lose sight of, the gpl executable.

In the gpl file for every test in the directory will expand on what the test is doing.

*Will run it a singular test :*
./gpl tests/t###.gpl 

Not create an extra file, instead :


printf 'int x; \ndouble y;\n' 

we want to pipe it in.

gpl expects a file name, so to fool it we must :

printf 'int x; \ndouble y;\n' | ./gpl /dev/stdin

/dev/stdin is a file that takes input on stdin and takes the input

valgrind is what we will be using 

In a vagrant box if you're going to valgrind, cd into the home directory of the machine.

Project 2 Goal : Begin making our parser handle buggy input.


int       x       =       5   ;
T_INT     T_ID                T_SEMIC

global variable array;

variable_declaration:
  simple_type T_ID optional_initializer
  {
    //Obtain our singleton Table_handler th
    if(th.have_you_already_been_declared($2)){
      Error::error(Error::alreadydeclared);
    }
  }


table handler - singleton 

  Symbol Table
  _______________
    symbol for example : int x = 99;
    type    (e.g., string, int, double, etc)
    value   (e.g. 99)
    name    (eg. x)
    length  (e.g. size, or amount of things)

    class called Symbol Table, and a class called Symbol


