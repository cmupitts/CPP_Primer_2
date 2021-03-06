# Answers To Non-programming Exercises

## Contents
- [Exercise 13.1](#exercise-131)
- [Exercise 13.2](#exercise-132)
- [Exercise 13.3](#exercise-133)
- [Exercise 13.4](#exercise-134)
- [Exercise 13.5](#exercise-135)
- [Exercise 13.6](#exercise-136)
- [Exercise 13.7](#exercise-137)
- [Exercise 13.8](#exercise-138)
- [Exercise 13.9](#exercise-139)
- [Exercise 13.10](#exercise-1310)
- [Exercise 13.11](#exercise-1311)
- [Exercise 13.12](#exercise-1312)
- [Exercise 13.13](#exercise-1313)
- [Exercise 13.14](#exercise-1314)
- [Exercise 13.15](#exercise-1315)
- [Exercise 13.16](#exercise-1316)
- [Exercise 13.17](#exercise-1317)
- [Exercise 13.18](#exercise-1318)
- [Exercise 13.19](#exercise-1319)
- [Exercise 13.20](#exercise-1320)
- [Exercise 13.21](#exercise-1321)
- [Exercise 13.22](#exercise-1322)
- [Exercise 13.23](#exercise-1323)
- [Exercise 13.24](#exercise-1324)
- [Exercise 13.25](#exercise-1325)
- [Exercise 13.26](#exercise-1326)
- [Exercise 13.27](#exercise-1327)
- [Exercise 13.28](#exercise-1328)
- [Exercise 13.29](#exercise-1329)
- [Exercise 13.30](#exercise-1330)
- [Exercise 13.31](#exercise-1331)
- [Exercise 13.32](#exercise-1332)
- [Exercise 13.33](#exercise-1333)
- [Exercise 13.34](#exercise-1334)
- [Exercise 13.35](#exercise-1335)
- [Exercise 13.36](#exercise-1336)
- [Exercise 13.37](#exercise-1337)
- [Exercise 13.38](#exercise-1338)
- [Exercise 13.39](#exercise-1339)
- [Exercise 13.40](#exercise-1340)
- [Exercise 13.41](#exercise-1341)
- [Exercise 13.42](#exercise-1342)
- [Exercise 13.43](#exercise-1343)
- [Exercise 13.44](#exercise-1344)
- [Exercise 13.45](#exercise-1345)
- [Exercise 13.46](#exercise-1346)
- [Exercise 13.47](#exercise-1347)
- [Exercise 13.48](#exercise-1348)
- [Exercise 13.49](#exercise-1349)
- [Exercise 13.50](#exercise-1350)
- [Exercise 13.51](#exercise-1351)
- [Exercise 13.52](#exercise-1352)
- [Exercise 13.53](#exercise-1353)
- [Exercise 13.54](#exercise-1354)
- [Exercise 13.49](#exercise-1349)
- [Exercise 13.50](#exercise-1350)
- [Exercise 13.51](#exercise-1351)
- [Exercise 13.52](#exercise-1352)
- [Exercise 13.53](#exercise-1353)
- [Exercise 13.54](#exercise-1354)
- [Exercise 13.55](#exercise-1355)
- [Exercise 13.56](#exercise-1356)
- [Exercise 13.57](#exercise-1357)
- [Exercise 13.58](#exercise-1358)

## Exercise 13.1

> What is a copy constructor? When is it used?

## Exercise 13.2

> Explain why the following declaration is illegal:
```cpp
Sales_data::Sales_data(Sales_data rhs);
```

## Exercise 13.3

> What happens when we copy a StrBlob? What about
StrBlobPtrs?

## Exercise 13.4

> Assuming Point is a class type with a public copy
constructor, identify each use of the copy constructor in this program
fragment:
```cpp
Point global;
Point foo_bar(Point arg)
{
    Point local = arg, *heap = new Point(global);
    *heap = local;
    Point pa[ 4 ] = { local, *heap };
    return *heap;
}
```

## Exercise 13.5

> Given the following sketch of a class, write a copy
constructor that copies all the members. Your constructor should dynamically
allocate a new string (§ 12.1.2, p. 458) and copy the object to which ps
points, rather than copying ps itself.
```cpp
class HasPtr {
public:
    HasPtr(const std::string &s = std::string()):
    ps(new std::string(s)), i(0) { }
private:
    std::string *ps;
    int i;
};
```

[Exer13_05.cpp](Exer13_05.cpp) 

## Exercise 13.6

> What is a copy-assignment operator? When is this operator
used? What does the synthesized copy-assignment operator do? When is it
synthesized?

## Exercise 13.7

> What happens when we assign one StrBlob to another?
What about StrBlobPtrs?

## Exercise 13.8

> Write the assignment operator for the HasPtr class from
exercise 13.5 in § 13.1.1 (p. 499). As with the copy constructor, your
assignment operator should copy the object to which ps points.

[Exer13_08.cpp](Exer13_08.cpp) 

## Exercise 13.9

> What is a destructor? What does the synthesized destructor
do? When is a destructor synthesized?

## Exercise 13.10

> What happens when a StrBlob object is destroyed? What
about a StrBlobPtr?

## Exercise 13.11

> Add a destructor to your HasPtr class from the previous
exercises.

## Exercise 13.12

> How many destructor calls occur in the following code
fragment?
```cpp
bool fcn(const Sales_data *trans, Sales_data accum)
{
    Sales_data item1(*trans), item2(accum);
    return item1.isbn() != item2.isbn();
}
```

## Exercise 13.13

> A good way to understand copy-control members and
constructors is to define a simple class with these members in which each
member prints its name:
```cpp
struct X {
    X() {std::cout << "X()" << std::endl;}
    X(const X&) {std::cout << "X(const X&)" <<
    std::endl;}
};
```
Add the copy-assignment operator and destructor to X and write a program using
X objects in various ways: Pass them as nonreference and reference parameters;
dynamically allocate them; put them in containers; and so forth. Study the output
until you are certain you understand when and why each copy-control member is
used. As you read the output, remember that the compiler can omit calls to the
copy constructor.

[Exer13_13.cpp](Exer13_13.cpp) | [Exer13_13.h](Exer13_13.h) 

## Exercise 13.14

> Assume that numbered is a class with a default constructor
that generates a unique serial number for each object, which is stored in a
data member named mysn. Assuming numbered uses the synthesized copycontrol
members and given the following function:
```cpp
void f (numbered s) { cout << s.mysn << endl; }
```
what output does the following code produce?
```cpp
numbered a, b = a, c = b;
f(a); f(b); f(c);
```

[Exer13_14.cpp](Exer13_14.cpp) | [Exer13_14.h](Exer13_14.h) 

## Exercise 13.15

> Assume numbered has a copy constructor that generates a
new serial number. Does that change the output of the calls in the previous
exercise? If so, why? What output gets generated?

[Exer13_15.cpp](Exer13_15.cpp) | [Exer13_15.h](Exer13_15.h) 

## Exercise 13.16

> What if the parameter in f were const numbered&?
Does that change the output? If so, why? What output gets generated?

[Exer13_16.cpp](Exer13_16.cpp) | [Exer13_16.h](Exer13_16.h) 

## Exercise 13.17

> Write versions of numbered and f corresponding to the
previous three exercises and check whether you correctly predicted the
output.

## Exercise 13.18

> Define an Employee class that contains an employee name
and a unique employee identifier. Give the class a default constructor and a
constructor that takes a string representing the employee’s name. Each
constructor should generate a unique ID by incrementing a static data
member.

[Exer13_18.h](Exer13_18.h) 

## Exercise 13.19

> Does your Employee class need to define its own versions
of the copy-control members? If so, why? If not, why not? Implement
whatever copy-control members you think Employee needs.

## Exercise 13.20

> Explain what happens when we copy, assign, or destroy
objects of our TextQuery and QueryResult classes from § 12.3 (p. 484).

## Exercise 13.21

> Do you think the TextQuery and QueryResult classes
need to define their own versions of the copy-control members? If so, why?
If not, why not? Implement whichever copy-control operations you think
these classes require.

## Exercise 13.22

> Assume that we want HasPtr to behave like a value. That
is, each object should have its own copy of the string to which the objects
point. We’ll show the definitions of the copy-control members in the next
section. However, you already know everything you need to know to
implement these members. Write the HasPtr copy constructor and copyassignment
operator before reading on.

[Exer13_22_HasPtr.h](Exer13_22_HasPtr.h) 

## Exercise 13.23

> Compare the copy-control members that you wrote for the
solutions to the previous section’s exercises to the code presented here. Be
sure you understand the differences, if any, between your code and ours.

## Exercise 13.24

> What would happen if the version of HasPtr in this section
didn’t define a destructor? What if HasPtr didn’t define the copy
constructor?

## Exercise 13.25

> Assume we want to define a version of StrBlob that acts
like a value. Also assume that we want to continue to use a shared_ptr so
that our StrBlobPtr class can still use a weak_ptr to the vector. Your
revised class will need a copy constructor and copy-assignment operator but
will not need a destructor. Explain what the copy constructor and copyassignment
operators must do. Explain why the class does not need a
destructor.

## Exercise 13.26

> Write your own version of the StrBlob class described in
the previous exercise.

[Exer13_26.cpp](Exer13_26.cpp) | [Exer13_26_StrBlob.h](Exer13_26_StrBlob.h) 

## Exercise 13.27

> Define your own reference-counted version of HasPtr.

[Exer13_27_HasPtr.h](Exer13_27_HasPtr.h) 

## Exercise 13.28

> Given the following classes, implement a default constructor
and the necessary copy-control members.
```cpp
(a)
class TreeNode {
private:
    std::string value;
    int count;
    TreeNode *left;
    TreeNode *right;
};
(b)
class BinStrTree {
private:
    TreeNode *root;
};
```

[Exer13_28_BinStrTree_point.h](Exer13_28_BinStrTree_point.h) | [Exer13_28_BinStrTree_value.h](Exer13_28_BinStrTree_value.h) | [Exer13_28_pointer.cpp](Exer13_28_pointer.cpp) | [Exer13_28_TreeNode_point.h](Exer13_28_TreeNode_point.h) | [Exer13_28_TreeNode_value.h](Exer13_28_TreeNode_value.h) | [Exer13_28_value.cpp](Exer13_28_value.cpp) 

## Exercise 13.29

> Explain why the calls to swap inside swap(HasPtr&,
HasPtr&) do not cause a recursion loop.

## Exercise 13.30

> Write and test a swap function for your valuelike version of
HasPtr. Give your swap a print statement that notes when it is executed.

[Exer13_30.cpp](Exer13_30.cpp) 

## Exercise 13.31

> Give your class a < operator and define a vector of
HasPtrs. Give that vector some elements and then sort the vector.
Note when swap is called.

[Exer13_31.cpp](Exer13_31.cpp) 

## Exercise 13.32

> Would the pointerlike version of HasPtr benefit from
defining a swap function? If so, what is the benefit? If not, why not?

## Exercise 13.33

> Why is the parameter to the save and remove members
of Message a Folder&? Why didn’t we define that parameter as Folder?
Or const Folder&?

## Exercise 13.34

> Write the Message class as described in this section.

[Exer13_34_36_37.cpp](Exer13_34_36_37.cpp) | [Exer13_34_36_37_Folder.h](Exer13_34_36_37_Folder.h) 

## Exercise 13.35

> What would happen if Message used the synthesized
versions of the copy-control members?

## Exercise 13.36

> Design and implement the corresponding Folder class.
That class should hold a set that points to the Messages in that Folder.

[Exer13_34_36_37.cpp](Exer13_34_36_37.cpp) | [Exer13_34_36_37_Folder.h](Exer13_34_36_37_Folder.h) 

## Exercise 13.37

> Add members to the Message class to insert or remove a
given Folder* into folders. These members are analogous to Folder’s
addMsg and remMsg operations.

[Exer13_34_36_37.cpp](Exer13_34_36_37.cpp) | [Exer13_34_36_37_Folder.h](Exer13_34_36_37_Folder.h) 

## Exercise 13.38

> We did not use copy and swap to define the Message
assignment operator. Why do you suppose this is so?

## Exercise 13.39

> Write your own version of StrVec, including versions of
reserve, capacity (§ 9.4, p. 356), and resize (§ 9.3.5, p. 352).

## Exercise 13.40

> Add a constructor that takes an
initializer_list<string> to your StrVec class.

[Exer13_40_43_StrVec.h](Exer13_40_43_StrVec.h) 

## Exercise 13.41

> Why did we use postfix increment in the call to
construct inside push_back? What would happen if it used the prefix
increment?

## Exercise 13.42

> Test your StrVec class by using it in place of the
vector<string> in your TextQuery and QueryResult classes (§ 12.3,
p. 484).

[Exer13_42.cpp](Exer13_42.cpp) | [Exer13_42_TextQuery.h](Exer13_42_TextQuery.h) 

## Exercise 13.43

> Rewrite the free member to use for_each and a lambda
(§ 10.3.2, p. 388) in place of the for loop to destroy the elements. Which
implementation do you prefer, and why?

[Exer13_40_43_StrVec.h](Exer13_40_43_StrVec.h) | [Exer13_43.cpp](Exer13_43.cpp) 

## Exercise 13.44

> Write a class named String that is a simplified version of
the library string class. Your class should have at least a default
constructor and a constructor that takes a pointer to a C-style string. Use an
allocator to allocate memory that your String class uses.

[Exer13_44.cpp](Exer13_44.cpp) | [Exer13_44_47_49_String.h](Exer13_44_47_49_String.h) 

## Exercise 13.45

> Distinguish between an rvalue reference and an lvalue
reference.

## Exercise 13.46

> Which kind of reference can be bound to the following
initializers?
```cpp
int f();
vector<int> vi(100);
int? r1 = f();
int? r2 = vi[0];
int? r3 = r1;
int? r4 = vi[0] * f();
```

## Exercise 13.47

> Give the copy constructor and copy-assignment operator in
your String class from exercise 13.44 in § 13.5 (p. 531) a statement that
prints a message each time the function is executed.

[Exer13_44_47_49_String.h](Exer13_44_47_49_String.h) 

## Exercise 13.48

> Define a vector<String> and call push_back several
times on that vector. Run your program and see how often Strings are
copied.

[Exer13_48.cpp](Exer13_48.cpp) 

## Exercise 13.49

> Add a move constructor and move-assignment operator to
your StrVec, String, and Message classes.

[Exer13_44_47_49_String.h](Exer13_44_47_49_String.h) | [Exer13_49_String.h](Exer13_49_String.h) 

## Exercise 13.50

> Put print statements in the move operations in your
String class and rerun the program from exercise 13.48 in § 13.6.1 (p.
534) that used a vector<String> to see when the copies are avoided.

[Exer13_50.cpp](Exer13_50.cpp) 

## Exercise 13.51

> Although unique_ptrs cannot be copied, in § 12.1.5 (p.
471) we wrote a clone function that returned a unique_ptr by value.
Explain why that function is legal and how it works.

## Exercise 13.52

> Explain in detail what happens in the assignments of the
HasPtr objects on page 541. In particular, describe step by step what
happens to values of hp, hp2, and of the rhs parameter in the HasPtr
assignment operator.

## Exercise 13.53

> As a matter of low-level efficiency, the HasPtr assignment
operator is not ideal. Explain why. Implement a copy-assignment and moveassignment
operator for HasPtr and compare the operations executed in
your new move-assignment operator versus the copy-and-swap version.

[Exer13_53_1.cpp](Exer13_53_1.cpp) | [Exer13_53_2.cpp](Exer13_53_2.cpp) | [Exer13_53_HasPtr.h](Exer13_53_HasPtr.h) | [Exer13_53_HasPtr_copy_swap.h](Exer13_53_HasPtr_copy_swap.h) | [Exer13_53_overload.cpp](Exer13_53_overload.cpp) 

## Exercise 13.54

> What would happen if we defined a HasPtr moveassignment
operator but did not change the copy-and-swap operator? Write
code to test your answer.

[Exer13_54.cpp](Exer13_54.cpp) | [Exer13_54_HasPtr.h](Exer13_54_HasPtr.h) 

## Exercise 13.49

> Add a move constructor and move-assignment operator to
your StrVec, String, and Message classes.

[Exer13_55_StrBlob.h](Exer13_55_StrBlob.h) | [Exer13_55_String.h](Exer13_55_String.h) | [Exer13_55_StrVec.h](Exer13_55_StrVec.h) 

## Exercise 13.50

> Put print statements in the move operations in your
String class and rerun the program from exercise 13.48 in § 13.6.1 (p.
534) that used a vector<String> to see when the copies are avoided.

[Exer13_56.cpp](Exer13_56.cpp) 

## Exercise 13.51

> Although unique_ptrs cannot be copied, in § 12.1.5 (p.
471) we wrote a clone function that returned a unique_ptr by value.
Explain why that function is legal and how it works.

[Exer13_57.cpp](Exer13_57.cpp) 

## Exercise 13.52

> Explain in detail what happens in the assignments of the
HasPtr objects on page 541. In particular, describe step by step what
happens to values of hp, hp2, and of the rhs parameter in the HasPtr
assignment operator.

## Exercise 13.53

> As a matter of low-level efficiency, the HasPtr assignment
operator is not ideal. Explain why. Implement a copy-assignment and moveassignment
operator for HasPtr and compare the operations executed in
your new move-assignment operator versus the copy-and-swap version.

## Exercise 13.54

> What would happen if we defined a HasPtr moveassignment
operator but did not change the copy-and-swap operator? Write
code to test your answer.

## Exercise 13.55

> Add an rvalue reference version of push_back to your
StrBlob.

## Exercise 13.56

> What would happen if we defined sorted as:
```cpp
Foo Foo::sorted() const & {
    Foo ret(*this);
    return ret.sorted();
}
```

## Exercise 13.57

> What if we defined sorted as:
```cpp
Foo Foo::sorted() const & { return Foo(*this).sorted(); }
```

## Exercise 13.58

> Write versions of class Foo with print statements in their
sorted functions to test your answers to the previous two exercises.
