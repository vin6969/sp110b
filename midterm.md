## mid term

### Ruby Compiler

####Summary
ruby compiler is a programming language created in 1990 by yukihiro in japan. Ruby programming languages can be installed by downloading the software on their website
```
https://www.ruby-lang.org/en/downloads/
```

```
 apt-get install ruby
```
for linux

Ruby programming languages uses a simple and easy to learn, because of its similar syntax to already widely used languages.
Programs can be written in Ruby in any of the widely used text editors like Notepad++, gedit etc After writing the programs save the file with the extension .rb


### Basic code
puts is used to print something on the console in Ruby.For eg. A string
```
puts "Hello World"
puts "Hello Again"
```

### Comments
'#' is called the pound character in ruby and it is used to add comments to your code.
=begin, =end are used for multi-line comments

```
# this is a comment and wont be executed
= begin
this is 
a multi line
comment in ruby
= end
```

### Maths
Simple mathematical functions can be carried out within the puts statements.
Just as we use ‘%d’ or ‘%f’ and ‘&’ in C,we will use ‘#{ } in Ruby to get our work done.
```
puts "Alok has #{25+30/6} Rupees in his pocket"
```
#### Output:
```
Alok has 30 Rupees in his pocket
```

### Variables and Names
Variables in ruby are the same as that of any other dynamic programming language.
You just don’t need to mention its type and ruby will know its type automatically.
```
cars = 100
drivers = 30
puts "There are #{cars} cars and #{drivers} drivers."
```
#### Output:
```
There are 100 cars and 30 drivers.
```

#### Getting Input
‘gets.chomp’ is used to take input from user.
‘print’ can be used instead for ‘puts’to print without a new line.
```
print "How old are you ? "
age = gets.chomp
print "How tall are you ?"
height = gets.chomp
puts " You are #{age} year old and your height is #{height} cms"
```

#### prompting people for numbers
gets.chomp.to_i is used to get integer input from user.
gets.chomp.to_f is used to get float(decimal) input from user.

```
print "Give a number"
number = gets.chomp.to_i
puts "You just entered #{number}"
```
#### Source
https://www.geeksforgeeks.org/ruby-for-beginners/?ref=lbp


### About Ruby

#### Ruby's Visual Appearance
While Ruby often uses very limited punctuation and usually prefers English keywords, some punctuation is used to decorate Ruby. Ruby needs no variable declarations. It uses simple naming conventions to denote the scope of variables.

- var could be a local variable.
- @var is an instance variable.
- $var is a global variable.

These sigils enhance readability by allowing the programmer to easily identify the roles of each variable. It also becomes unnecessary to use a tiresome self.
prepended to every instance member.

#### What is Ruby used for?
Ruby developers really love the language and have found many uses for it over the years. 
This programming languages is highly portable general-purpose language that serves many purposes.
Ruby is great for building desktop applications, static websites, data processing services, and even automation tools. It’s used for web servers, DevOps, and web scraping and crawling.

#### Data processing
Ruby is also a great language for data processing, cleaning, and filtering. Ruby's built-in map, reduce, and select functions are powerful tools used to solve many data processing problems.


#### What makes Ruby different?
Ruby is often called a "language of careful balance." It was released in 1995 by Yukihiro Matsumoto. Matsumoto had in-depth knowledge of multiple programming languages, including Perl, Smalltalk, Eiffel, Ada, and Lisp. He created Ruby to combine what he thought were the best features of these programming languages.

Ruby is a very flexible programming language that allows developers to alter how the language itself works. You can add functionality to core language features or even remove them if you need. Ruby is also a highly portable, cross-platform language. Code you write on one operating system will run on Linux, Mac OSX, and Windows. It will even run in UNIX, DOS, BeOS, OS/2, and more.

##### source
https://www.ruby-lang.org/en/about/


### Ruby vs Phyton
One of the languages Ruby gets compared to most often is Python. Ruby and Python have a lot in common and can be used for many of the same purposes, which can make it hard for developers who are deciding which language to learn or which to use for a specific project. Both Ruby and Python are high-level server-side scripting languages with clear and easy-to-read syntax, but there are some important technical differences.

### Differences between Ruby vs Python
Some of the differences between Ruby vs Python include:

- Python supports multiple IDEs, whereas Ruby supports only EclipseIDE.
- With Python you’re limited to the Django framework; with Ruby, you’re limited to Rails.
- Ruby uses a powerful blocks feature, but Python offers more libraries.
- Ruby is a true object-oriented language, but Python has more traction among data scientists. And on it goes, tit for tat.

Some developers find Ruby more difficult to debug but more flexible in general.
Some find Python easier to learn initially but more stifling in the long run.
In many ways, it boils down to a basic philosophical difference between the two: In Ruby, there are many ways of doing things, many solutions to one problem. In Python, there’s a best way of doing things, and that’s the way you should do it.



|               | Ruby                             | Python                   |
| ------------- |:-------------------------------: | ------------------------:|
| Framework     | Rails                            | Django                   |
| Philosophy    | “Many ways of doing things”      | “One best way of doing things”|
| Developers    | 1.8M                             |  8.2M                    |
| Values        | Flexibility, creativity          |    Simplicity, stability |


### Why should I learn Ruby?
Developers like using Ruby because it’s high level and has a simple syntax. You have less code to write and can focus on finding a solution to your problem.

Because of the high level and abstracted nature of Ruby, this adds up to a language that is easy to learn and put into practice. While many low-level languages require lines and lines of code for the smallest thing, with Ruby, you can write your first cloud application in just a few hours.
It’s also an excellent choice for building applications quickly and definitely has the edge over Python when it comes to web development.

##### Source
https://acloudguru.com/blog/engineering/what-is-the-ruby-programming-language
