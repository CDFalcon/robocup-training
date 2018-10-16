# Skills, Tactics, Plays {#t20182}


# Python Overview


## Using Python

```shell
$ python3
Python 3.5.3 (default, Jan 19 2017, 14:11:04)
[GCC 6.3.0 20170118] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print("Hello RoboCup!")
Hello RoboCup!
```


## Basic Syntax

```python
# Hello world
print("Hello World!")

# Set a variable
myinteger = 1
mydouble = 1.0
mystr = "one"

print(myinteger)
print(mydouble)
print(mystr)
```

    Hello World!
    1
    1.0
    one


## IF Statements and Conditionals

```python
if True:
    print("RoboCup is great!")
if False:
    print("IGVC is great...")

if True:
    print("RoboCup is the best!")
elif True:
    print("RoboRacing is the best...")
else:
    print("IGVC is the best...")

a = 5
if a > 2:
    print("a is greater than 2!")
if a > 2 and a < 10:
    print("a is > 2 and < 10")
print("a is greater than 3" if a > 3 else "a is less than 3")
print("a is greater than 9" if a > 9 else "a is less than 9")
```

    RoboCup is great!
    RoboCup is the best!
    a is greater than 2!
    a is > 2 and < 10
    a is greater than 3
    a is less than 9


## Loops and range()

```python
a = 10
while a > 0:
    print(a, end=" ")
    a = a - 1
print("")

print(list(range(10)))
for i in range(10):
    print(i * i, end=" ")
print("")
```

    10 9 8 7 6 5 4 3 2 1 
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    0 1 4 9 16 25 36 49 64 81 


## Functions

```python
def func1(a, b):
    return a + b

print(func1(2, 4))

# Lambda Expressions ('advanced' topic)
def secret_func():
    return "RoboCup!"
def welcome(target):
    return "Welcome to " + target()

print(welcome(secret_func))
print(welcome(lambda: "RoboJackets!"))
# Lambda with arguments
# print(welcome(lambda arg1, arg2: "RoboJackets!"))
```

    6
    Welcome to RoboCup!
    Welcome to RoboJackets!


## Object Oriented Python

```python
class BaseClass():
    globalVar = 1
    # Constructor
    def __init__(self):
	print("Initializing a Base")
	self.local_var = 2

class ChildClass(BaseClass):
    def __init__(self):
	super().__init__() # call superclass constructor
	print("Initializing Child")
	print("Our local var is: " + str(self.local_var))

# When defining class methods, pass 'self' as the first arg.
# Self refers to the current class instance.
a = BaseClass()
print("---")
a = ChildClass()
```

    Initializing a Base
    ---
    Initializing a Base
    Initializing Child
    Our local var is: 2


## We can't teach a full year of programming in one hour.

-   Take advantage of resources like [codeacademy](https://www.codecademy.com/) or [lynda](https://www.lynda.com/)(to which you have access using your Georgia Tech information.)
-   Programming is a language, and like every language, it takes time to become familiar with the syntax and vocabulary.


## Additional Python Resources

-   [lightbot](http://lightbot.com/hocflash.html) - A Introduction to Programming Logic
-   [Python Beginner Hub](https://wiki.python.org/moin/BeginnersGuide/NonProgrammers)
-   [Python Syntax Overview](https://learnxinyminutes.com/docs/python/)
-   [A intro to python](http://thepythonguru.com/)


# Plays System


## Plays, Tactics, Skills

-   A Basic Unit in our AI
-   Only one **Play** can run at a time
-   A **play** may utilize multiple **tactics**, which themselves may utilize multiple **skills**.


## Skill

-   Involves only *one* robot
-   Extremely basic building blocks
-   Examples
    -   Move
    -   Kick
    -   Face a direction
    -   Capture the ball
-   Located in `soccer/gameplay/skills/`


## Tactics

-   Involves multiple robots
-   Utilize skills
-   Can contain unique behavior (but usually not)
-   Examples
    -   Pass
    -   Defend
    -   Line Up
-   Located in `soccer/gameplay/tactics/`


## Plays

-   Only one can run
-   Utilize tactics
-   Examples
    -   Basic122 (basic offense)
    -   Two side attack (basic offense)
    -   Stopped Play
    -   Line Up
    -   Corner Kick
-   Located in `soccer/gameplay/plays/*/`


### Notes

-   Only plays are actually runnable in our model
    -   If you want to run a tactic, make a dummy play that runs that tactic on startup
-   For now, we'll only look at plays to keep things simple (maybe we'll get more complex later)


# Goals

-   Understand how to use skills
-   Understand which points correspond to different locations on the field


## File

-   Use SimpleBehaviors.py in the training folder
-   In Sim, check the SimpleBehaviors play and run
-   Replace skills.Move.move with different skills or change the point.


## Assignments

-   Make a robot move to the following locations
    -   All four corners
    -   The center of the field
-   Make a robot capture a ball
-   Make a robot shoot using a line kick
-   Make a robot shoot using a pivot kick


## Code you can use

-   constants.Field.Length
-   constants.Field.Width
-   skills.Capture.capture


## Tactics / Positions Extension

-   Make robots do a coordinated pass
-   Make a robot become a submissive defender (use tactics.submissivedefender)
-   Make a robot become a goalie


## Plays extension

-   Write Basic122 without state machines
    -   One robot pivot kicks, two robots mark, two robots are submissive defenders, one robot is a goalie


## Tips

-   The field coordinates start at 0, 0; Which is our Goal.
-   Field Size Docs: ([http://bit.ly/2cLsUBL](http://bit.ly/2cLsUBL))
-   Ball Position Docs: ([http://bit.ly/2damxXA](http://bit.ly/2damxXA))
-   If you don't know how to use a skill or tactics, use ctrl + shift + p to see how other people use it.


## Exercise Details

-   Ask on [gitter](https://github.com/RoboJackets/robocup-software/blob/master/soccer/gameplay/plays/skel/which_half.py) for help and answers!


## Answers

-   Add something here