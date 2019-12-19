_friend function_ --> allows the function to access the private data in the class

_class_ Date {
  public:
    Date(int m, int d, int y);
    ~Date();
    friend std::ostream& operator<<(std::ostream& os, const Date& dt);

    Date& operator=(const Date&) = delete;
    Date(const Date&) = delete;

  private:
    int month;
    int day;
    int year;
}

Date operator+(int days, const Date& abc);
Date operator+(const Date& abc, int days);

Date dt (...)
  dt + 5 <<---------- operator+(dt, 5);
  *(DOES NOT WORK UNLESS FRIEND) 5 + dt <<---------- operator+(5, dt);*



##Notes :

Doesn't matter *where* the friend is stored.
  * It doesn't lock it out if it is private.
  * As long as it is inside the class.

  Private data is fully for us the programmer, not the compiler.



#Dynamic Allocation


int *main*(){
  Date* dp=new Date(7,4,1776);
  cout << dp << endl;
  return 0;
}
We need to dereference it.


int *main*(){
  std::shared_ptr<Date> dp = make_shared<Date>(7,4,1776);
  std::shared_ptr<Date> dp2(dp);
  cout << *dp << endl;
  return 0;
}


shared_ptr releases the memory dynamically.

We can't get away with shared pointers everywhere.

both would convert, one is a constructor, and one is a converter.

class string{
  string(int);
  operator int();
  }


Next Thing:
    Date& operator=(const Date&) = delete;
    Date(const Date&) = delete;

    Class& operator=(const Class&) = delete;
    Class(const Class&) = delete;

    void class_function(const Class& argument){
    }

This makes it so that the compiler doesn't make the copy functions.

In this course, if you write a class be sure to put these two above lines in them.




##Singleton

A class where we need only a single case (Table_Handler, ex)

Sample_singleton& Sample_singleton::instance(){
  //This variables lifetime is the lifetime of the application.
  static Sample_singleton the_instance;
  return the_instance;
}

_How to keep from creating more_

Sample_singleton()
  :string_data("Special"),
   count_data(0)
{}


_This is how we'll do it with the table handler._

Sample_singleton& thingy=Sample_singleton::instance();


###Project 2 Specific Things:

  * 2 Symbols and symbol tables. We stack symbol tables based on scope.
  * union symboltype{} in the Symbol class, and the Symbol Constructor.
  * 
