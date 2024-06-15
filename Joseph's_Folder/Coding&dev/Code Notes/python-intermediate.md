# Python Intermediate.   
Getting more proficient in python.   
This is where I’m gonna be journaling my return to python.   
### LISTS   
They are ordered, mutable and allow duplicate elements.   
These are declared with square brackets.
mylist = ["banana", "cherry","apple"];
print(mylist)   
They can hold different data types
mylist = [5, True, "banana", 3,1];   
They always begin at index 0 :
[1, 4, 6, 8];
0 1 2 3 <=== indexes   
They can be kept in variables ;
item = mylist;   
This is also usable to get specific indexes;
item = mylist[0] *accesses what is a the 0th index*.   
A for in loop can be used to iterate through to print each element individually.
for i in mylist:
print(i);   
you can also search for a specific element in the list like this :
if "banana" in mylist:
print("yes, it is in");
else:
print(no, it isn't );   
In order to find the length of the list, you can use the len function;
print(len(mylist));   
the ".append(*userinput*)" method can be used to add an element to the end of the list.
mylist.append("lemon");   
if we wanted to be more specific about where the element was added, we would use "insert".
mylist.insert(1, "grapefruit");
index^ object^   
if we wanted to remove items, we would use the pop method.
mylist = [1,2,3,4];
num = mylist.pop();
print(num);
output : 4
This is used to remove numbers and output them, if a number is not specified, it removes the last element. In order to specify the item, you'd have to use the ".remove()" method.   
In order to empty the list, you cwan use the ".clear()" method.   
To reverse a list, you can use ".reverse()".   
To sort, use ".sort()". however it would change the list thus it is safer to create a sorted list then store it into a new variable.   
You can specify the number of new elements that you want in your list.
mylist[0] X 5;   
you can join lists using the + operator.
new\_list = mylist1 + mylist2;
print(new\_list);   
you can join lists using the + operator.
new\_list = mylist1 + mylist2;
print(new\_list);   
Slicing is often used to get segments of a lists
mylist = [1, 2, 3, 4, 5, 6, 7, 8 ,9];
slice\_of\_list = mylist[1:5];
print(slice\_of\_list);
the first number is an index where it will start however, the last number is excluded. [1:5] would give you indexes 1, 2, 3, 4. if no start index is inputed, it would begin all the way from the beginning. the same applies for stop index. you can also add a second colon "(start:stop:step)" to make a step index which is entirely optional. it is used to iterate through the list at intervals. it can also be used in a very cool way to reverse your list by using a negative number. [1:5:-1] would return the 1, 2, 3, 4 indexes but in reverse order. remember that all indexes start with 0.   
copying a list can be done using ".copy()"" method. why can't we just assign it as a variable ? because they would refer to the same space in memory making the copy change when the original is changed. you can also use the "list(input list)" function. lastly, you can use slicing by just not specifying   
List comprehension : fast way to make new list from existing one in one line.
mylist = [1, 2, 3, 4, 5, 6];
squared\_list = [ii for i in mylist];
output will be:
[1, 4, 9, 16, 25, 36];
all the output would be squared.
the syntax is like:
[expression. for-in loop iterating another list];   
Hmm, I’ve been following some youtube videos trying to work on some projects. and i’ve completed a few. I finished a “mad-lib” game and also a number guessing game. I made both a user and computer end where you could get tested by the computer. I am now working on some rock paper scissors code. I could follow the video but i wan’t to try and attempt on my own because I feel like I could do it since it should be quite similar to the number guesser. i will put my first attempt here.   
PYTHON PROJECTS   
```python
import random
# importing random.
# it will be the key feature to the computer choosing its hand.

def Computer_choice():
    choicelist = ["Rock", "Paper", "Scissors"]; # Lists of possible options
    choice = random.choice(choicelist); # the computer chooses between it's options
    return choice; # returns computer's choice.


def User_choice():
    choice = input('\\nEnter "Rock" to play Rock.\\n'
                   'Enter "Paper" to play Paper\\n' # the way the user inputs their choice
                   'Enter "Scissors" to play Scissors\\n'
                   '\\tChoice : ');
    choice = choice.title();
    return choice; # returns user's choice.


def Determine_Winner(user, comp):
    winner = "None" # initialising and setting winner to 0
    print("\\n");

    # this is how the game decides the winner.
    if user=="Rock" and comp=="Paper":
        winner = "Computer";
        print(f"User played {user} and Computer played {comp}\\n"
              f"{winner} Wins.");
    elif user=="Paper" and comp=="Rock":
        winner = "User";
        print(f"User played {user} and Computer played {comp}\\n"
              f"{winner} Wins.");

    elif user=="Paper" and comp=="Scissors":
        winner = "Computer";
        print(f"User played {user} and Computer played {comp}\\n"
              f"{winner} Wins!");
    elif user=="Scissors" and comp=="Paper":
        winner = "User";
        print(f"User played {user} and Computer played {comp}\\n"
              f"{winner} Wins.");

    elif user=="Scissors" and comp=="Rock":
        winner = "Computer";
        print(f"User played {user} and Computer played {comp}\\n"
              f"{winner} Wins.");
    elif user=="Rock" and comp=="Scissors":
        winner = "User";
        print(f"User played {user} and Computer played {comp}\\n"
              f"{winner} Wins.");
    elif user == comp:
        print(f"User played {user} and Computer played {comp}\\n"
              f"It's a tie.");
    else :
        print(f"Sorry User, That's not an option!");


def RockPaperScissors():
    # Runs through the functions in the correct order.
    play = True;
    while play == True:
        player_choice = input(' \\nWould you like to play "RockPaperScissors" with me, User ? (Yes/No)\\n : ');
        player_choice = player_choice.title();
        if player_choice == "Yes":
            ComputerChoice = Computer_choice();
            UserChoice = User_choice();
            Determine_Winner(UserChoice, ComputerChoice);
            print(f"Thanks for playing.\\n\\n");
        else:
            print("Oh, come play some other time, Okay ?");
            break;

# Start game.
RockPaperScissors()


```
## **TicTacToe - Python**   
I'd really like to make TicTacToe In python and this is going to be my progress log until I finally finish it and post it here.   
Im going to be sourcing realpython.com for my material.
[https://realpython.com/python3-object-oriented-programming/](https://realpython.com/python3-object-oriented-programming/) 
by David Amos.   
   
General Structure : 
   
TicTacToe  -Library   
  > Game Engine    

  1. State Validator   
  2. Move Simulatoe   
  3. Score Evaluator.   
   
        
  > Computer Player   

  1. Random (easy mode mostly)   
  2. minimax (basically unbeatable)

   
then there is also the front end (What we see and interact with) :   
Console Front End.   
  1. Command the Int.   
  2. Console Renderer   
  3. Human Player   

I have now understood the structure of the Code, but I will admit, I do not understand a single thing. Thus, I will make sure I complete the pre-requisites that are recommended before Trying to code the game. After-all, my goal is to gain more mastery and fulfil a promise.   
Pre-requisites :   
  - [x] Python-Object-Oriented-Programming (POOP). ✅ 2023-10-28
  - [x] Inheritance & Composition. ✅ 2023-10-28
  - [x] Abstract Classes. ✅ 2023-10-28
  - [x] Data Classes. ✅ 2023-10-28
  - [x] Type Hints. ✅ 2023-10-28
  - [x] Regular Expressions. ✅ 2023-10-28
  - [x] Caching. *i think this one will be hard* ✅ 2023-10-28
  - [x] Recursion. * this one too… * ✅ 2023-10-28
I'll keep coming back and doing my pre-requisites to see my progress.   
### Python's Object Oriented Programming.   
   
> What is a program ?    

- Programs are a set of instructions for manipulating data in a meaningful way.    
- INPUT DATA ==>  MANIPULATE DATA==>  OUTPUT DATA.   
- This applies to any program you'd like to make. If you wanted to make a program to tell you your age in days, you'd have to input how old you are in years. After that, the program will manipulate the data (probably by dividing it by some sort of dividend) and it will out put so called data.   
   
> OOP ?    

- Is a very common programming paradigm(way of designing software).   
- Makes developing large software a lot more manageable and Intuitive.    
- Allows us to think of complex software in terms of real world objects and their relationships to one another.   
   
> Objects ?   

- An object is an entity in your program (usually a noun).   
- A "person" could be an object in your program.   
- They would have properties to define them and behaviours to define what the object does.   
   
Person (object) :   
  > Properties   

  - Name   
  - Age   
  - Address   
  - Height   
  - Gender   
   
  > Behaviours   

  - Walk();   
  - Talk();   
  - Breathe();   
  - Read();   
   
```python

class Car:
    def __init__(self, make, model, miles):
        self.make = make.title();
        self.model = model.title();
        self.miles = int(miles);

    def describe(self):
        return (f"\nThis is a {self.make} {self.model}.\n" 
              f"It has {self.miles} miles.\n");


Honda_S2K = Car("Honda", "S2000", 20000);
Toyota_Supra = Car("Toyota", "Supra Mk4", 4000);
Dodge_Viper = Car("Dodge", "Viper Gen 2", 3000);
Nissan_R34 = Car("Nissan", "R34 Nismo", 3000)

Garage = [Honda_S2K, Toyota_Supra, Dodge_Viper, Nissan_R34];
for car in Garage:
    car = car.describe();
    print(car);



```

Here is a class representing a Car. It takes in a make, model, and how many miles it's driven. it also has a method responsible for making a description of the car.    
```python
class student:
    def __init__(self, name, age, grade="none"):
        self.name = name.title()
        self.age = int(age)
        self.grade = grade

    def describe_student(self):
        student_grade = self.grade
        if student_grade.isdigit():
            num_grades = int(self.grade)
            if num_grades < 0:
                report = f"they haven't begun elementary school yet"
            elif num_grades < 8:
                report = f"they are still in middle school "
            else:
                report = f"they are still a high schooler"
        else:
            graduated = "graduated"
            college = "college"
            no_education = "none"
            word_grade = str(self.grade)
            if word_grade == college.lower():
                report = f"they are still in college"
            if word_grade == graduated.lower():
                report = f"they have finished school"
            if word_grade == no_education.lower():
                report = f"they have no education background"

        full_report = f"{self.name} is {self.age} years old and {report}"
        return full_report


angel = student("angel", "16", "10")
crantson = student("Cranston", "50", "graduated")
jonathan = student("Jonathan", "17", "10")
adebayo = student("Adebayo", "20", )
print(adebayo.describe_student())

```
Self ?    
  Self is a parameter that enters all the methods of the Class. 
It returns the "instance" of the object through the method(function) So that the instance(object) can access its attributes.    
   
INHERITANCE & COMPOSITION   
Inheritance refers to the ability to make a class and it takes features (Inherits) from another class. The one that inherits is the child class and the source is the parent class. Both Inheritance and composition are important concepts in Object-oriented programming in order to model certain relationships between objects. They both determine the way a program works and how it would expand in the future due to updates.   
**Inheritance**   
  - Inheritance models a relationship by allowing a class to derive features from another. The provider becomes the (BaseClass/SuperClass) class and the (derived/subclass/subtypes) class becomes the receiver.    
**Composition**   
  - Represents a "has a" relationship. This means that a Composite Class can contain an object of another class component.   
  - A "Composite" has a "component"   
  - A class "Horse" could be a "composite" of the class "Tail".
This allows you to have a horse with a "Tail".   
Inheritance in Python is very obvious when you look for it. Everything in Python is an object. Everything is derived from the "Base Class": object().
In the Exception handling of Python, you can use "raise" to kind of raise an error. you can input what to raise as an error but all errors must derive from the BaseClass "BaseException". If you wanted to make custom errors, you need to derive your error class from "Exception".   
```python
class MyError(Exception):
    pass;

raise MyError();

```
   
Inheritance Hierarchies: Inheritance is often used to make hierarchies in Python amongst related classes. The base class will be a base for the derived classes that will then just specialize in the features of the base class.    
```python
# IN PAYROLL_SYSTEMHR.PY
# Parent & Child classes.
# I should write more documentation to prepare for when i do c++
class PayrollSysytem:
#Print all employee salaries plus total.
      def calculate_company_payroll(employees):
      │   print("\n\nCalculating payroll . . . ");
      │   print("==========================");
      │   comp_total = 0;
      │   for employee in employees:
      │   │   comp_total = comp_total + employee.calculate_payroll();
      │   │   print(f"Payroll for: {employee.id_num} <> {employee.name}");
      │   │   print(f"Pay-check amount : ${employee.calculate_payroll()}\n");
      │   print(f"Your company's weekly Total payroll is: ${comp_total}");
      │   return comp_total;

      def calculate_monthly_payroll(weeks, company_total):
      │   monthly_total_payroll = weeks * company_total;
      │   print(f"Your company's monthly total payroll is : ${monthly_total_payroll}\n");
      │

  class Employee:
  #Very base class from which the other employee classes will be defined.
      def __init__(self, name, id_num):
      │   self.name = name;
      │   self.id_num = id_num;

  class SalaryEmployee(Employee):
   #Has a definite salary at the end of the week. (Fixed value);
      def __init__(self, name, id_num, weekly_salary):
      │   super().__init__(name, id_num);
      │   self.weekly_salary = int(weekly_salary);

      def calculate_payroll(self):
      │   return self.weekly_salary;

  class Hourly_Employee(Employee):
   #Determine how much they earn per hour and multiply by the number of hours per week.
      def __init__(self, name, id_num, hours_worked, hourly_pay):
      │   super().__init__(name, id_num);
      │   self.hours_worked = int(hours_worked);
      │   self.hourly_pay = int(hourly_pay);
      │
   def calculate_payroll(self):
		return self.hours_worked * self.hourly_pay;

  class Commission_Employee(SalaryEmployee):
  #A salary man who also gets seperate commisions.
      def __init__(self, name, id_num, weekly_salary, commission):
      │   super().__init__(name, id_num, weekly_salary);
      │   self.commission = int(commission);

      def calculate_payroll(self):
      │   return self.weekly_salary+self.commission;




# IN PROGRAM.PY
import payroll_systemhr as hr
 James = hr.SalaryEmployee("james wick", "001", 700);
 Craig = hr.SalaryEmployee("craig duchee", "002", 1500);
 Alton = hr.Hourly_Employee("alton heinzer", "003", 40, 30);
 Jose = hr.Commission_Employee("jose alvarado", "004", 1000, 2000);

MadlibTech = [James, Craig, Alton, Jose];
MadlibTechTotal = hr.PayrollSysytem.calculate_company_payroll(MadlibTech);
WEEKS_IN_MONTH = 4.3;
hr.PayrollSysytem.calculate_monthly_payroll(WEEKS_IN_MONTH, MadlibTechTotal);
```
I have managed to code a Payroll system in python however it is mostly all in reference of realpython.com. 
This code is seperated into two different files where one holds the interface and all the classes while the other is importing the first file and using the interface to import some data and perform some calculations.    
The Classes That define the different kinds of employees are the "Abstract  base classes" since they abstract from the "Employee" class. The Payroll\_system class is an "interface" which means it bridges the user and the other classes. 
   
NEVERMIND, Abstracted base classes are classes that are meant to be inherited but never to be instaniated. For example, the "**Employee**" class is rcommended to not be instantiated especially because it does not have the required ".calculate\_payroll();" method that is needed by the Interface class thus it would most definately return errors.   
I have managed to improve my HR payroll system by also adding another interface to classify some worker classes.    
```python
# This is where the workey classes shall be defined.
# Managers = SalaryEmployee, Fairly high salary.
# Secretery = SalaryEmployee, Medium salary.
# Salesman = CommsionEmployee, Low-medium salary, varying commisions.
# FactoryWorker = HourlyEmployee, low-med hours, med pay.

import payroll_systemhr as hr


class Company:
    def calculate_company_payroll(employees):
        print("\n\nCalculating payroll . . . ")
        print("==========================")
        comp_total = 0
        for employee in employees:
            comp_total = comp_total + employee.calculate_payroll()
            print(f"Payroll for: {employee.id_num} <> {employee.name}")
            print(f"Pay-check amount : ${employee.calculate_payroll()}\n")
        print(f"Your company's weekly Total payroll is: ${comp_total}")
        return comp_total

    def calculate_monthly_payroll(weeks, company_total):
        monthly_total_payroll = weeks * company_total
        print(f"Your company's monthly total payroll is : ${monthly_total_payroll}\n")


class Manager(hr.SalaryEmployee):
    def work(self, hours):
        print(
            f"{self.name} spent {hours} hours overworking his employees\n",
            " they also spent the day yelling at his employees.\n",
        )


class Secretary(hr.SalaryEmployee):
    def work(self, hours):
        print(
            f"{self.name} spent {hours} hours being overworked\n",
            " they also did a lot of paper work.\n",
        )

class Salesman(hr.Commission_Employee):
    def work(self, hours):
        print(
            f"{self.name} spent {hours} hours selling the products\n",
            "they also spent the day lying to customers.\n",
        )


class FactoryWorker(hr.Hourly_Employee):
    def work(self, hours):
        print(
            f"{self.name} spent {hours} hours being overworked\n",
            "they almost chopped off his fingers.\n",
        ) 

```
   
###  [[Tic_Tac_Toe_ai]]