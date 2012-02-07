# Ruby Basics

## Introduction

Ruby is a language of careful balance. Its creator, [Yukihiro “matz” Matsumoto](http://www.rubyist.net/~matz/), blended parts of his favorite languages (Perl, Smalltalk, Eiffel, Ada, and Lisp) to form a new language that balanced functional programming with imperative programming.

He has often said that he is “trying to make Ruby natural, not simple,” in a way that mirrors life.

Building on this, he adds:

Ruby is simple in appearance, but is very complex inside, just like our human body.

Initially, Matz looked at other languages to find an ideal syntax. Recalling his search, he said, “I wanted a scripting language that was more powerful than Perl, and more object-oriented than Python3.”

In Ruby, everything is an object. Every bit of information and code can be given their own properties and actions. Object-oriented programming calls properties by the name instance variables and actions are known as methods. Ruby’s pure object-oriented approach is most commonly demonstrated by a bit of code which applies an action to a number.

    5.times { print "We *love* Ruby -- it's outrageous!" }

ruby has 2 main modes:

  - Scripting
  - Program

On the first one, the code is interpreted line by linte, while on the other one, code is loaded on memory and then executed

#### IRB

irb interactive ruby bash is a console to write and test code ruby directly on it.
on irb we can do many test for example, this tool can use to learn what methods or clasess have an object
the sintax tu run and test code ruby is: 

      irb [ options ] [ progrmafile ] [ argument...]

the same way you can define class and  methods  or simple functions as well as the following:

      def sum(n1,n2)
        n1+n2
      end

the result of this piece of code is  a simple arithmetic sum between n1 and n2 example:

      sum(2,3)
      =>5

We need to add more info about this

#### Running a rb file on ruby on bash

the normal way to write ruby is to put them in one file and we can try our code on the console executing it directly load the file whit the console example to load a file an test what is the result
whit vim create a file white the name "sample1.rb" and puts this piece of code:


##  Ruby and it's features

We'll start to talk more about Ruby and it's technical features, and if you wanna taste the Ruby's flavor at the same time that you are reding this, I recommend you to use the irb "Interactive Ruby" command-line environment just by using this command:

    $ irb
    ruby-1.9.2-p290 :001 > 

And now you'll be able to see what's happening on every step on this tutorial.

### Standard types

Ruby supports integer, float, rational, complex, strings, and almost every standard type that you need to use whe you are developing with ruby.

- Arrays:

are idexed collections. this type of variable can be accesible using a key its a very efficient to access array data.
the arrays have many methods and if you whants to know what methods  included his class  you can use :array.public_methods to show the public methods
in ruby the array indices start at zero.

The arrays on ruby can be defined as follows

      [1,2,'ruby on rails']
      %w(number1,number2,number3,etc)

Example:
create a new file called arrays.rb and write the next:

      array = %w( a b c d e f g )
      puts array.collect {|e| puts e }
      puts array.reverse
      puts array.reverse.join(' ')

for test the code just run : 

      ruby arrays.rb
      =>a
      =>b
      =>c
      =>d
      =>e
      =>f
      =>g
      =>g f e d c b a 

the code array.collect throught each position or element in array variable and puts the value on console
the method reverse sort the content of array in order ascendent or descendent. using the last method joins all 
values content in each position in array separate by colons. returns only one string.

      =>a b c d e f g

the first one each element must be separated whit a semicolon and if you write a string should be enclosed
another one  only can contain single phrases or single words if contains words whit blank space you must be defined it whit the first form

      class Array
        def sum
          self.inject :+
        end
      end

the previos code add a method to the class Array this method  in ruby all is an object and exteds the functionality is very simple
and this is a little example. to use the method only needs type the next: the ruby interpreter and the file name

      ruby sample1.rb
        [2,3,2,4].sum
      =>11

- Hashes

Hashes are also indexed collections but is very different from arrays(some times know as assiciative arrays,maps or ditcionaries)
this variables accept or support any object as key. the hashes provide more flexibility than a arrays.
Hoever, althought you index arrays with integers,you can index array with objects of any type: simbols,strings,regular expressions,and so on.
the syntax of a hash is name_variable={'index'=>'value','index2'=>'value2'}. to retrieve a value from hash called h we can do this:

      h['index'] # => "value"
      h['index2'] # =>"value2"

to know how many elements contains  hash h run the command:

      h.length #=>2

- Classeses

in Ruby language a class is used to construct an object. A class is a blueprint for an object for example we might use a button class to make many 
differents buttons, and each button might have its own color,size,etc.. properties in other words an Object is ainstance of a class

let's see  an example of class definition

      class Tangosource

        attr_accesor :writable
        attr_reader :readable

        def initialize
          @writable = Time.now
          @readable = Time.now
        end

        def self.test
          t1 = Tangosource.new
          t2 = Tangosource.new

          puts."t1.writable"
          puts t1.writable

          sleep(2)

          t1.writable = Time.now

          puts "t1.writable"
          puts t1.writable

        end

      end

- Generation of code blocks

In ruby is to easier create new functionalities for example if we needs formater a text input
whit a especific format just needs create a method that return the text input as in the following example

we create a file called blocks.rb inside the file write the following code:

      def super_puts
        puts "*****************************"
        yield(Time.now)
        puts "*****************************"
      end

      super_puts{|x| puts 'value'}
      
      super_puts do |x|
        puts 'value'
        puts x
      end

- Structures of controll

#### If, else

An "if" expresion on Ruby it's pretty similar than any other language:

      1.9.2-p290 :001 > today = "Monday"
      1.9.2-p290 :002 > if today == "Monday"
      1.9.2-p290 :003?>   puts "I hate mondays"
      1.9.2-p290 :004?>   else
      1.9.2-p290 :005 >     puts "What a nice day"
      1.9.2-p290 :006?>   end
      I hate mondays
       => nil    

There is another way to evaluate the if statement, by using "unless" like: 

      1.9.2-p290 :001 > today = "Monday"
      1.9.2-p290 :002 > unless today == "Monday"
      1.9.2-p290 :003?>   puts "what a nice day!"
      1.9.2-p290 :004?>   end
       => nil 
      1.9.2-p290 :005 > today = "Tuesday"
      1.9.2-p290 :006 > unless today == "Monday"
      1.9.2-p290 :007?>   puts "What a nice day"
      1.9.2-p290 :008?>   end
      What a nice day
       => nil     

#### for

      for variable [, variable ...] in expression [do]
         code
      end

#### each

      (0..5).each do |i|
         puts "Value of local variable is #{i}"
      end

#### while

      while conditional [do]
         code
      end

### *RI

To find the documentation for a class, type ri ClassName. 
For example, the following is the summary information for the GC class.
(To get a list of classes with ri documentation, type ri with no arguments.)

### Chapter 5: 'Sharing Functionality'

#### Inheritance

Inheritance allows you to create a class that is a refinement or specialization of another class.
This class is called a subclass of the original, and the original is a superclass of the subclass.
People also talk of child and parent classes.

      class Parent                      # Declarating the parent class                      
        def say_hello                   # Declaring the function
          puts "Hello from #{self}"     # Printing the result
        end 
      end

      p = Parent.new                    # Creating the parent class instance
      p.say_hello                       # Executing the parent class method

      # Subclass the parent...

      class Child < Parent              # Declarating a child class from the superclass 'Parent' called 'Child'
      end

      c = Child.new                     # Creating the Child class instance
      c.say_hello                       # Executing the inheritanced method

        produces:
        Hello from #<Parent:0x0000010086b220> 
        Hello from #<Child:0x0000010086b108>

A parent class assumes that it will be subclassed and calls a method that it expects its children to implement.
This allows the parent to take on the brunt of the processing but to invoke what are effectively hook methods 
in subclasses to add application-level functionality.

#### Modules

Modules are a way of grouping together methods, classes, and constants. Modules give you two major benefits:

1 Modules provide a namespace and prevent name clashes.

2 Modules support the mixin facility.

      module Trig                               # Declarating the module called 'Tring'
      PI = 3.141592654                          # Defining 'PI' constant 
        def Trig.sin(x)                         # Defining 'sin' function
          # ..                        
        end 

        def Trig.cos(x)                         # Declarating 'cos' function 
          # ..
        end 
      end

      module Moral                              # Declarating the module called 'Tring'
      VERY_BAD  = 0                             # Defining 'VERY_BAD' variable
      BAD	      = 1                             # Defining 'BAD' variable
        def Moral.sin(badness)                  # Defining 'sin' fuction
          # ...
        end 
      end

      require_relative 'trig'                   # Including 'trig' module
      require_relative 'moral'                  # Including 'moral' module
      y = Trig.sin(Trig::PI/4)                  # Executing sin function over Trig module
      wrongdoing = Moral.sin(Moral::VERY_BAD)   # Executing sim fuction over Moral module



As with class methods, you call a module method by preceding its name with the module’s name and a period,
and you reference a constant using the module name and two colons.


#### Mixins
Modules have another, wonderfull use. at a stroke, they pretty much eliminate the nedd for inheritance, providing a facility called a mixin
you can include a module within a class fefinition. allowing access to all included in the module how metodos of  class itself

     module Debug                                # Definition a module "Debug"
       def who_am_i?                             # Definition a method
         "#{self.class.name} (id: #{self.object_id}): #{self.name}"
       end
     end

     class Phonograph                            #Another definition of a module
       include Debug                             #including the metod Debug
       attr_reader :name                         #definition a attribute accesor
       def initialize(name)                      #defining class initialize method
         @name = name
       end
       # ...
     end

     class EightTrack                           #another class whit the inclusion of "Debug"
       include Debug
       attr_reader :name
       def initialize(name)
         @name = name
       end
       # ...
     end

      ph = Phonograph.new("West End Blues")
      et = EightTrack.new("Surrealistic Pillow")
      
      ph.who_am_i? # => "Phonograph (id: 2151894340): West End Blues"
      et.who_am_i? # => "EightTrack (id: 2151894300): Surrealistic Pillow"

      #As you can see each class contains the method defined in the module "Debug" this is the functionality of the modules and heritage and is known as mixin

**Explanation**

A module is a collection of methods that can be included in many classes and each class can access the method comprising the module.
in other words is a way to not repeat code in one class and another through the modules you can add functionality to a class without having to be inherited from another class.
therefore a "Mixin" the use of inheritance and modules in a class

### Chapter 6 'Standar Types'

#### Numbers


Ruby supports integers and ﬂoating-point, rational, and complex numbers. Integers can be any
length. Integers within a certain range (normally −230 ...230 -1 or −262 ...262 -1) are held internally in binary form
and are objects of class Fixnum. Integers outside this range are stored in objects of class Bignum
(currently implemented as a variable-length set of short integers). This process is transparent,
and Ruby automatically manages the conversion back and forth:

     num = 1001
     5.times do
      puts "#{num.class}: #{num}"
      num *= num
     end

produces:

     Fixnum: 1002001
     Bignum: 1004006004001
     Bignum: 1008028056070056028008001
     Bignum: 1016120561824376019452881448012369820560120016001

You can  write integers using an optional leading sign, an optional base indicator

* 0 for octal
* 0d for decimal [the default]
* 0x for hex
* 0b for binary

     123456                  #Fixnum

     0d123456                #Fixnum

     123_456                 #Fixnum 

     -543                    #negative number

     0xaabb                  #hexadecimal 

     0377                    #Fixnum - octal 

     -0b10_1010              #Fixnum - binary (negated)

     123_456_789_123_456_789 #Bignum

A numeric literal with a decimal point and/or an exponent is turned into a Float object, corre-
sponding to the native architecture’s double data type.

Ruby doesn’t have a literal syntax for representing rational and complex numbers. Instead, you
create them using explicit calls to the constructor methods Rational and Complex (although, as
we’ll see, you can use the mathn library to make working with rational numbers easier).

**Examples**

      Rational(3, 4) * Rational(2, 3)   # => (1/2)
      Rational("3/4") * Rational("2/3") # => (1/2)

#### How Numbers Interact

 If you mix integers and ﬂoats, the result will be a ﬂoat; if you mix ﬂoats and complex numbers, the result will be
complex.

     1 + 2               #=> 3
     1 + 2.0             #=> 3.0
     1.0 + 2             #=> 3.0
     1.0 + Complex(1,2)  #=> (2.0+2i)
     1 + Rational(2,3)   #=> (5/3)
     1.0 + Rational(2,3) #=> 1.6666666666666665

The rjturn-type rule still applies when it comes to division.

     1.0 / 2  # => 0.5
     1 / 2.0  # => 0.5
     1 / 2    # => 0

If you’d prefer that integer division instead return a fraction (a Rational number), require the
mathn library.

     22 / 7                  # => 3
     Complex::I * Complex::I # => (-1+0i)
     require 'mathn'
     22 / 7                  # => (22/7)
     Complex::I * Complex::I # => -1

#### Looping Using Numbers

Integers also support several iterators. We’ve seen one already: 5.times in the code example on
page 100. Others include upto and downto for iterating up and down between two integers. Class
Numeric also provides the more general method step, which is more like a traditional for loop.

     3.times        { print "X" }
     1.upto(5)      {|i| printi, " " }
     99.downto(95)  {|i| printi, " " }
     50.step(80, 5) {|i| printi, " " }

**Produces**

     X X X 1 2 3 4 5 99 98 97 96 95 50 55 60 65 70 75 80

As with other iterators, if you leave the block off, the call returns an Enumerator object:

     10.downto(7).with_index {|num, index| puts "#{index}: #{num}"}

**Produces**

      0:10
      1:9
      2:8
      3:7

#### Strings

Ruby strings are simply sequences of characters. They normally hold printable characters,
but that is not a requirement; a string can also hold binary data. Strings are objects of class
String.

The type of string delimiter determines the degree of substitution performed. 
Within single-quoted strings, two consecutive backslashes are replaced by a single backslash, 
and a backslash followed by a single quote becomes a single quote.

      'escape using "  # => escape using "\"
      'That\'s right'  # => That's right

**Note**
 Double-quoted strings support a boatload more escape sequences. 

**Examples**

      "Seconds/day: #{24*60*60}"    # => Seconds/day: 86400
      "#{'Ho! '*3}Merry Christmas!" # => Ho! Ho! Ho! Merry Christmas!   
      "Safe level is #$SAFE"        # => Safe level is 0                

You have three more ways to construct string literals: %q, %Q, and here documents. %q and
%Q start delimited single- and double-quoted strings (you can think of %q as a thin quote, as in
’, and %Q as a thick quote, as in "):

      %q/general single-quoted string/  # => general single-quoted string   
      %Q!general double-quoted string!  # => general double-quoted string   
      %Q{Seconds/day: #{24*60*60}}      # => Seconds/day: 86400                

#### Strings and Encodigs

The defaul encoding for a string literal depends on the encoding of the source file that contains it. Whit no explicit encoding, a source
file (and its strings) will be US-ASCII.ASCII

     plain_string = "dog"
     puts "Encoding of #{plain_string.inspect} is #{plain_string.encoding}"
     produces:
     Encoding of "dog" is US-ASCII

**Character Constants**

Technically, Ruby does noy have a class for characters - characters are simply strings of lenght one. For historical reasons, character constants 
can be created by preceding the character (or sequencee that represents a character) whit a question mark:


sequence that represents a character) with a question mark:

     ?a       # => "a"      (printable character)
     ?\n      # => "\n"     (code for a newline (0x0a))
     ?\C-a    # => "\x01"   (control a)
     ?\M-a    # => "\xE1"   (meta sets bit 7)
     ?\M-\C-a # => "\x81"   (meta and control a)          
     ?\C-?    # => "\x7F"   (delete character)           

**Working whit Strings**

Strings is probably the largest built-in Ruby class, whit more than 100 standard methods. We won't go through them all here; the library reference has
a complete list. Insted, We'll look at some common strings idioms -- things that are likely to pop up during day to day proraming.

maybe we've been given a file containing information on a song playlist. For historical reasons, the list of songs is stored as lines in the file.
Each line holds he name of file containing the song, the song's duration, the artist, and the file, all in vertical bar-separated fields. A typical file may start like this:

     /jazz/j00132.mp3 | 3:45 | Fats Waller | Ain't Misbehavin'
     /jazz/j00319.mp3 | 2:58 | Louis Armstrong | Wonderful World
     /bgrass/bg0732.mp3| 4:09 | Strength in Numbers | Texas Red

To split each line into fields, and String#split will do the job nicely. In this case, we'll pass split a regular 
Our ﬁrst task is to split each line into ﬁelds, and String#split will do the job nicely. In this case,
we’ll pass split a regular expression, /\s*\|\s*/, that splits the line into tokens wherever split ﬁnds
a vertical bar, optionally surrounded by spaces. And, because the line read from the ﬁle has a
trailing newline, we’ll use String#chomp to strip it off just before we apply the split. We’ll store
details of each song in a Struct that contains an attribute for each of the three ﬁelds. (A Struct is

### Chapter 7 'Regular Expressions'

A regular expression is a pattern that can be matched against a string. It can be a simple pattern, such as the string must contain the sequence of letters “cat”, or the pattern can be complex, such as the string must start with a protocol identifier, followed by two literal forward slashes, followed by..., and so on

#### What Regular Expressions Let You Do

- You can test a string to see whether it matches a pattern.
- You can extract from a string the sections that match all or part of a pattern. 
- You can change the string, replacing parts that match a pattern.

#### Ruby’s Regular Expressions

Ruby acepts all characters except '.', '|', '(', ')', '[', ']', '{', '}', '+', '\', '^', '$', '*', and '?' match themselves. So, at the risk of creating something that sounds like a logic puzzle, here are some patterns and examples of strings they match and don’t match:

      /cat/       Matches "dog and cat" and "catch" but not "Cat" or "c.a.t."
      /123/       Matches "86512312" and "abc123" but not "1.23"
      /t a b/     Matches "hit a ball" but not "table"

If you want to match one of the special characters literally in a pattern, precede it with a back- slash, so /\*/ is a pattern that matches a single asterisk, and /\/ / is a pattern that matches a forward slash.

**Matching Strings with Patterns**

The Ruby operator =~ matches a string against a pattern. It returns the character offset into the string at which the match occurred:

Here is how it works

      /cat/ =~ "dog and cat"        # => 8
      /cat/ =~ "catch"	        # => 0
      /cat/ =~ "Cat"	        # => nil


You can put the string first if you prefer:


      "dog and cat" =~ /cat/        # => 8
      "catch" =~ /cat/	        # => 0
      "Cat" =~ /cat/	        # => nil


**Changing Strings with Patterns**

The sub method takes a pattern and some replacement text.3 If it finds a match for the pattern in the string, it replaces the matched substring with the replacement text.

The sub method changes only the first match it finds. To replace all matches, use gsub. (The g stands for global.)

      str = "Dog and Cat"
      new_str1 = str.sub(/a/, "*") 
      new_str2 = str.gsub(/a/, "*")
      puts "Using sub: #{new_str1}"
      puts "Using gsub: #{new_str2}"

produces:

      Using sub: Dog *nd Cat 
      Using gsub: Dog *nd C*t


#### Digging Deeper

You can also create regular expression objects by calling the Regexp class’s new method or by using the %r{...} syntax. The %r syntax is particularly useful when creating patterns that contain forward slashes:

      /mm\/dd/	              # => /mm\/dd/ 
      Regexp.new("mm/dd")         # => /mm\/dd/ 
      %r{mm/dd}	              # => /mm\/dd/

**Matching Against Patterns**

Once you have a regular expression object, you can match it against a string using the (Reg- exp#match(string) method or the match operators =~ (positive match) and !~ (negative match). The match operators are defined for both String and Regexp objects. One operand of the match operator must be a regular expression.

      name = "Fats Waller" 
      name =~ /a/                       # => 1 
      name =~ /z/                       # => nil 
      /a/ =~ name                       # => 1 
      /a/.match(name)                   #<MatchData "a">
      Regexp.new("all").match(name)     #<MatchData "all">

We can use these methods to write a method, show_regexp, that illustrates where a particular pattern matches:

      def show_regexp(string, pattern) 
        match = pattern.match(string) 
        if match
          "#{match.pre_match}->#{match[0]}<-#{match.post_match}"
        else
          "no match"
        end 
      end

We could use this method like this:

      show_regexp('very interesting', /t/)  # => very in->t<-eresting
      show_regexp('Fats Waller', /a/)       # => F->a<-ts Waller
      show_regexp('Fats Waller', /lle/)     # => Fats Wa->lle<-r
      show_regexp('Fats Waller', /z/)       # => no match

**Deeper Patterns**

So if you remember we mentioned that there are some charaacters that ruby does not asept, in ordor to treat this like regular character it is nessesary to scape them using a backslash like this:

      show_regexp('yes | no', /\|/)       	  # => yes ->|<- no 
      show_regexp('yes (no)', /\(no\)/)       # => yes ->(no)<- 
      show_regexp('are you sure?', /e\?/)     # => are you sur->e?<-

**Anchors**

The patterns '^' and '$' match the beginning and end of a line, respectively. These are often used to anchor a pattern match; for example, '/^option/' matches the word option only if it appears at the start of a line. Similarly, the sequence '\A' matches the beginning of a string, and '\z' and '\Z' match the end of a string. (Actually, '\Z' matches the end of a string unless the string ends with '\n', in which case it matches just before the '\n'.)

      str = "this is\nthe time"
      show_regexp(str, /^the/)      # => this is\n->the<- time 
      show_regexp(str, /is$/)       # => this ->is<-\nthe time 
      show_regexp(str, /\Athis/)    # => ->this<- is\nthe time 
      show_regexp(str, /\Athe/)     # => no match

**Character Classes**

A character class is a set of characters between brackets: [characters].

      show_regexp('Price $12.', /[aeiou]/)        # => Pr->i<-ce $12.
      show_regexp('Price $12.', /[\s]/)	      # => Price-> <-$12.
      show_regexp('Price $12.', /[$.]/)	      # => Price ->$<-12.


**Repetition**

If 'r' stands for the immediately preceding regular expression within a pattern, then

      r*	  Matches zero or more occurrences of r
      r+  	  Matches one or more occurrences of r
      r?	  Matches zero or one occurrence of r
      r{m,n}  Matches at least m and at most n occurrences of r 
      r{m,}	  Matches at least m occurrences of r
      r{,n}	  Matches at most n occurrences of r 
      r{m}	  Matches exactly m occurrences of r


**Alternation**

We know that the vertical bar is special, because our line-splitting pattern had to escape it with a backslash. That’s because an unescaped vertical bar, as in |, matches either the construct that precedes it or the construct that follows it

**Grouping**

\You can use parentheses to group terms within a regular expression. Everything within the group is treated as a single regular expression.

      show_regexp('banana', /an+/)      #=> b->an<-ana)
      show_regexp('banana', /(an)+/     #=> b->anan<-a)

#### Advanced Regular Expressions

**Regular Expression Extensions**

The sequence (?# comment) inserts a comment into the pattern. The content is ignored during pattern matching. As we’ll see, commenting complex regular expressions can be as helpful as commenting complex code.

      date = "12/25/2010"

      date =~ %r{(\d+)(/|:)(\d+)(/|:)(\d+)}
      [$1,$2,$3,$4,$5] # => ["12", "/", "25", "/", "2010"]

      date =~ %r{(\d+)(?:/|:)(\d+)(?:/|:)(\d+)}
      [$1,$2,$3]	# => ["12", "25", "2010"]

**Lookahead and Lookbehind**

For example, you might want to match every word in a string that is followed by a comma, but you don’t want the comma to form part of the match. Here you could use the charmingly named zero-width positive lookahead extension. (?=re) matches re at this point but does not consume it—you can look forward for the context of a match without affecting $&. In this example, we’ll use scan to pick out the words:

      str = "red, white, and blue"
      str.scan(/[a-z]+(?=,)/) # => ["red", "white"]


**Controlling Backtracking**

Say you’re given the problem of searching a string for a sequence of Xs not followed by an O. You know that a string of Xs can be represented as X+, and you can use a lookahead to check that it isn’t followed by an O

The sequence (?>re) nests an independent regular expression within the first regular expression. This expression is anchored at the current match position. If it consumes characters, these will no longer be available to the higher-level regular expression. This construct therefore inhibits backtracking.

      re = /((?>X+))(?!O)/

      # This one works 
      re =~ "test XXXY"	# => 5
      $1	# => "XXX"

      # Now this doesn't match 
      re =~ "test XXXO"	# => nil
      $1	# => nil

      # And this finds the second string of Xs
      re =~ "test XXXO XXXXY" # => 10
      $1	# => "XXXX"

**Named Subroutines**

There’s a trick that allows us to write subroutines inside regular expressions.
Recall that we can invoke a named group using \g<name>, and we define the group using (?<name>...). 
Normally, the definition of the group is itself matched as part of executing the pattern. However,
if you add the suffix {0} to the group, it means “zero matches of this group,” 
so the group is not executed when first encountered

### Chapter 8 'More About Methods'

#### Defining a Method

As we’ve seen, a method is defined using the keyword def. Method names should begin with a lowercase letter or underscore,1 followed by letters, digits, and underscores.
A method name may end with one of ?, !, or =. Methods that return a boolean result (so-called predicate methods) are often named with a trailing ?:

      1.even?	                # => false 
      2.even?	                # => true 
      1.instance_of?(Fixnum)  # => true


Ruby lets you specify default values for a method’s arguments—values that will be used if the caller doesn’t pass them explicitly. You do this using an equal sign (=) followed by a Ruby expression. That expression can include references to previous arguments in the list:

      def cool_dude(arg1="Miles", arg2="Coltrane", arg3="Roach") 
        "#{arg1}, #{arg2}, #{arg3}."
      end

      cool_dude                             # => "Miles. Coltrange, Roach"
      cool_dude("Bart")                     # => "Bart. Coltrange Roach"
      cool_dude("Bart", "Elwood")           # => "BArt. Elwood, Roach"
      cool_dude("Bart", "Elwood", "Linus")  # => "Bart. Elwood, Linus"

In ruby there is a way to make multiple captures into a single parameter . 
In order to do so, when you are defining the method arguments use the '*' for example : 

      def varas(arg1, *rest)

With that expresion you can asign to 'rest' more then one value

#### Calling method blocks

      class TaxCalculator 
          def initialize(name, &block)                            # '&' determinates any associated block is converted to a Proc object
            @name, @block = name, block                           
          end

          def get_tax(amount)                                     
            "#@name on #{amount} = #{ @block.call(amount) }"      # 'call' is used to execute the block code
          end 
      end

      tc = TaxCalculator.new("Sales tax") {|amt| amt * 0.075 }    

      tc.get_tax(100) # => "Sales tax on 100 = 7.5"               
      tc.get_tax(250) # => "Sales tax on 250 = 18.75"             

#### Calling a Method

      connection.download_mp3("jitterbug") {|p| show_progress(p) }

In this example, the object connection is the receiver, download_mp3 is the name of the method,
the string "jitterbug" is the parameter, and the stuff between the braces is the associated block.
During this method call, Ruby first sets self to the receiver and then invokes the method in that object.
For class and module methods, the receiver will be the class or module name.

      class InvoiceWriter 

        def initialize(order)
          @order = order
        end 

        def write_on(output)
          write_header_on(output) 
          write_body_on(output) 
          write_totals_on(output)
        end

        private

        def write_header_on(output) 
          puts "Header"
        end

        def write_body_on(output) 
         puts "body"
        end

        def write_totals_on(output) 
          puts "total"
        end 
      end

      writer = InvoiceWriter.new("hola") 
      writer.write_on(STDOUT)

#### Passing Parameters to a Method

Any parameters follow the method name. 
If no ambiguity exists, you can omit the parentheses around the argument list when calling a method.
2 However, except in the simplest cases we don’t recommend this—some subtle problems can trip you up.
3 Our rule is simple: if you have any doubt, use parentheses.

      # for some suitable value in obj:
      a = obj.hash	# Same as 
      a = obj.hash() # this.

      obj.some_method "Arg1", arg2, arg3	# Same thing as 
      obj.some_method("Arg1", arg2, arg3) # with parentheses.

#### Method Return Values

This next example uses return to exit from a loop inside the method:

      def meth_three 
        100.times do |num|
        square = num*num
        return num, square if square > 1000 end
      end



#### Splat! Expanding     Collections in Method Calls

In a single argument a method could get 'n' parameters, to do so we need to write a '*' before an argument.
Note: the total of armguments inside an array or hash plus the single arguments must be equal to the expected arguments.
Example: 

      def five(a, b, c, d,e)
         "I was passed #{a} #{b} #{c} #{d} #{e}"
      end

      puts five(1,2,3,4,5) 
      puts five(1, 2, 3, *['a','b'] )
      puts five(*['a', 'b'],*(1..3))
      puts five(*(10..14)) 
      puts five(*[1,2], 3, *(4..5))
      a=(1..5)
      puts five(*a)
      h= {
        '1' => 'uno', 
        '2' => 'dos',
        '3' => 'tres', 
        '4' => 'cuatro', 
        '5' => 'cinco',
      }
      puts five(*h)
      puts five(*h.values)
      puts five(*h.keys)

### Chapter 10 'Exceptions, catch and throw'

So far, we've been developing code in Pleasatnville, a wonderful place
were nothing ever, ever goes wrong. Every library call succeeds, users
never enter incorrect data, and resources are plentiful and cheap. Well, 
that's about change. Welcome to real world!

In the real world errors happen. Exceptions let you package information
about an error into an object. That exception object is then propagated 
back up the calling stack automatically until the runtime system finds
code that explicity declares that it knows how to handle that type of 
exception.

#### The exception class

Information about an exception is encapsulated in an object of a class Exception
or one of class Exception's children. Ruby predefines a tidy hierarchy of exceptions
When you need to rise an exception, you can use one of the built-in Exception classes
or you can create one of your own. Every Exception has asociated with it a message string
and stack backtrace. If you define your own exceptions, you can add extra information.

      Exception
        fatal
        NoMemoryError
        ScriptError
         LoadError
         NotImplementedError
         SyntaxError
        SecurityError
        SignalException
         Interrupt
        StandardError
          ArgumentError
          EncodingError
           Encoding::CompatibilityError
           Encoding::ConverterNotFoundError
           Encoding::InvalidByteSequenceError
           Encoding::UndefinedConversionError
          FiberError
          IndexError
           KeyError
            StopIteration
          IOError
           EOFError
         LocalJumpError
          Math::DomainError
          NameError
            NoMethodError
          RangeError
            FloatDomainError
          RegexpError
         RuntimeError
         SystemCallError
         ThreadError
         TypeError
         ZeroDivisionError
        SystemExit
       SystemStackError

#### Handling Exceptions

Here's some simple code that uses the open-uri
library to download the contents of a web page
and write it to a file by line:

      require 'open-uri'
      web_page = open("http://pragprog.com/podcasts")
      output = File.open("podcasts.html","w")
      while line = web_page.gets
       output.puts line
      end
      output.close

We certanly don't want to store an incomplete page
to the output file. Let's add some Exception handling
code and see how it helps.

      require 'open-uri'
      page = "podcasts"
      file_name = "#{page}.html"
      web_page = open("http://pragprog.com/#{page}")
      output = File.open(file_name,"w")
      begin
        while line = web_page.gets
          output.puts line
        end
       output.close
      rescue Exception
       STDERR.puts "Failed to download #{page}: #{$!}"
       output.close
       FIle.delete(file_name)
       raise
      end

You can have multiple rescue clauses in a begin block
and each rescue clause can specify multiple exceptions to catch.

At the end of each rescue clause, you can give Ruby the name of a
local variable to recieve the matched Exception. Most people find
this more readable than using $! all over the place.

      begin
       eval string
      rescue SyntaxError, NameError => boom
       print "String doesn't compile: " + boom
      rescue StandardError => bang
       print "Error running script: " +bang
      end

#### System Errors

System errors are raised when a call to the opening system returns an
error code. Ruby takes these errors and wraps them in each specific 
exception object.

      Errno::EAGAIN::Errno      # => 35
      Errno::EPERN::Errno       # => 1
      Errno::EIO::Errno         # => 5
      Errno::EWOULDBLOCK::Errno # => 35

#### Tidying Up

Sometimes you need to guarantee that some processing is done at the end 
of code, regardless of whether an exception was raised.

      f = File.open("testfile")
      begin
       # .. process
      rescue
       # .. handle error
      ensure
        f.close
      end

You can add an "else" clause.

      f = FIle.open("testfile")
      begin
       # .. process
      rescue
       # .. handle error
      else
       puts "Congratulations-- no errors!"
      ensure
        f.close
      end

#### Raising Exceptions

You can raise exceptions in your code with the 
Object#raise method.

      raise
      raise "bad mp3 endcoding"
      raise InterfaceException, "Keyboard failure", cancel

Here are some typical examples of raise in action

      raise
      raise "missing name" if name.nil?
      if i >= names.size
        raise IndexError, "#{i} >= size (#{names.size})"
      end

      raise ArgumentError, "Name too big", caller

#### Adding information to exceptions

You can define your own exceptions to hold any information
that you need to pass out from the site of an error.

      class RetryException < RuntimeError
        attr :ok_to_retry
        def initialize(ok_to_retry)
          @ok_to_retry = ok_to_retry
        end
      end

Somewhere down in depths of the code, a transient error occurs:

      def read_data(socket)
        data = socket.read(512)
        if data.nil?
          raise RetryException.new(true), "Transient read error"
        end
        #Normal processing
      end

Higher up the call stack, we handle the exception:

      begin
        stuff = read_data(socket)
        # .. Process stuff
      rescue RetryException => detail
        retry if detail.ok_to_retry
        raise
      end

#### Catch and Throw

Although the exception mechanism of raise and rescue is great for abandoning
excecution when things go wrong, it's sometimes nice to be able to jump out
of some deeply nested construct during normal processing.

      word_list = File.open("wordlist")
      catch (:done) do
        result = []
        while line =  word_list.gets
          word = line.chomp
          throw :done unless word =~ /^\w+$/
          result << word
        end
        puts result.reverse
      end

Catch defines a block is labeled with the given name (which any symbol or string).
When ruby encounters a throw, it zips it back up the call stack looking for a catch
block with a matching symbol.

      word_list = File.open("wordlist")
      word_in_error = catch(:done) do
        result = []
        while line = word_list.gets
          word = line.chomp
          throw(:done,word) unless word =~ /^\w+$/
          result << word
        end
        puts result.reverse
      end
      if word_in_error
        puts "Failed: '#{word_in_error}' found, but a word was expected"
      end

Produces:

      Failed: '(word in error)' found, but word was expected

The following example uses a throw to terminate interaction with the user if '!' is typed
in response to any prompt

      def prompt_and_get(prompt)
        print prompt
        res = readline.chomp
        throw :quit_requested if res == "!"
      end

      catch :quit_requested do
        name = promt_and get("Name: ")
        age = promt_and get("Age: ")
        sex = promt_and get("Sex: ")
        # ..
        # Process information
      end
    
As this example ilustrates, the throw does not have to appear within the static scope of catch.

#### Making Blocks More Dynamic

Normally, this is perfectly good enough—you associate a fixed block of code with a method in the same way you’d have a chunk of code after an
if or while statement.

      print "(t)imes or (p)lus: "
      operator = gets
      print "number: "
      number = Integer(gets)

      if operator =~ /^t/
        calc = lambda {|n| n*number }
      else
        calc = lambda {|n| n+number }
      end

      puts((1..10).collect(&calc).join(", "))

produces:

      (t)imes or (p)lus: t
      number: 2 2, 4, 6, 8, 10, 12, 14, 16, 18, 20

#### Collecting Hash Arguments

In ruby insted of passing a specific number of arguments in a given order we invoke the method with the name of the arguments for example:

      class SongList def search(field, params)
        # ...
      end end

      list = SongList.new
      list.search(:titles, { :genre => "jazz", :duration_less_than => 270 })

This will bring you a "jazz" song with a duration less then 4.5 minutes. 

### Chapter 9 'Expressions'

One of the first differences with Ruby is that anything that can reasonably return a value does:

just about everything is an expression.  What does this mean in practice?

Some obvious things include the ability to chain statements together:

      a = b = c = 0	                # => 0 
      [ 3, 1, 7, 0 ].sort.reverse   # => [7, 3, 1, 0]

#### Operator Expressions

In Ruby, many operators are implemented as method calls. For example, when you write 'a*b+c', 
you’re actually asking the object referenced by a to execute the method '*', passing in the parameter b.

      a, b, c = 1, 2, 3 
      a * b + c             # => 5 
      (a.*(b)).+(c)         # => 5

When you write this:

      some_obj[1,2,3]

you’re actually calling a method named [ ] on some_obj, passing it three parameters. You’d define this method using this:

      class SomeClass 
        def [](p1, p2, p3)
          # ...
        end 
      end

#### Miscellaneous Expressions

In the description of the command output expression, we said that the string in backquotes would “by default” be executed as a command. 
In fact, the string is passed to the method called Object#‘ (a single backquote).
If you want, you can override this. This example uses $?, which contains the status of the last external process run:

      alias old_backquote ‘ 
      def ‘(cmd)
        result = old_backquote(cmd) 
        if $? != 0
          puts "*** Command #{cmd} failed: status = #{$?.exitstatus}"
        end
        result
      end
      print ‘ls -l /etc/passwd‘ print ‘ls -l /etc/wibble‘
      
      'produces:'

      -rw-r--r-- 1 root wheel 3667 Jun 23 2009 /etc/passwd 

      ls: /etc/wibble: No such file or directory 

      Command ls -l /etc/wibble failed: status = 1

#### Assignment 

An assignment statement sets the variable or attribute on its left side (the lvalue) to refer to the value on the right (the rvalue).
It then returns that rvalue as the result of the assignment expression. This means you can chain assignments, and you can perform assignments in some unexpected places:

      a=b=1+2+3

      a     # => 6
      b     # => 6
      a = (b = 1 + 2) + 3
      a     # => 6
      b     # => 3

**Parallel assigment**

When we use a comma separated with multiple values, the rules of parallel asigment cames to play.

      int a=1;         #C,orJava,or...
      int b = 2; 
      int temp;

      temp = a; a = b; b = temp;

You can do this much more cleanly in Ruby:

      a=1 
      b=2 
      a, b = b, a

**Splats and Assignment**

So, if the splat is the last lvalue, it will soak up any rvalues that are left after assigning to previous lvalues:

      a,*b=1,2,3	    # a=1, b=[2,3] 
      a,*b=1	        # a=1, b=[]

**Nested Assignments**

It extracts the corresponding rvalue, assigning it to the parenthesized terms, before continuing with the higher-level assignment.

      a, (b, c), d = 1,2,3,4        # a=1, b=2, c=nil, d=3 
      a, (b, c), d = [1,2,3,4]      # a=1, b=2, c=nil, d=3 
      a, (b, c), d = 1,[2,3],4      # a=1, b=2, c=3, d=4 
      a, (b, c), d = 1,[2,3,4],5    # a=1, b=2, c=3, d=5 
      a, (b,*c), d = 1,[2,3,4],5    # a=1, b=2, c=[3, 4], d=5


#### Conditional Execution

Ruby has several different mechanisms for conditional execution of code; most of them should feel familiar,
and many have some neat twists. Before we get into them, though, we need to spend a short time looking at boolean expressions.

Both the keyword and and the operator && return their first argument if it is false

      nil &&99          # => nil    
      false && 99       # => false 
      "cat" && 99       # => 99

Similarly, both or and || return their first argument unless it is false, in which case they evaluate
and return their second argument.

      nil ||99      #=>99 
      false || 99   # => 99 
      "cat" || 99   # => "cat"

The defined? operator returns nil if its argument (which can be an arbitrary expression) is not defined; otherwise, it returns a description of that argument.

      defined? 1          # =>"expression"  
      defined? dummy      # => nil  
      defined? printf     # =>"method" 
      defined? Stringo    # => "constant" 
      defined? $_         # => "global-variable" 
      defined? Math::PI   # => "constant" 
      defined? a = 1      # => "assignment" 
      defined? 42.abs     # => "method" 
      defined? nil        # => "nil"


if you want to lay out your code more tightly, you must separate the boolean expres- sion from the following statements with the then keyword:

      if artist == "Gillespie" then handle = "Dizzy" 
      elsif artist == "Parker" then handle = "Bird" 
      else handle = "unknown" 
      end

Ruby also has a negated form of the if statement:

      unless duration > 180 
        listen_intently
      end

#### Case expressions

The Ruby case expression is a powerful beast: a multiway if on steroids. And just to make it even more powerful, it comes in two flavors.

      kind = case year
             when 1850..1889 then    "Blues"
             when 1890..1909 then    "Ragtime" 
             when 1910..1929 then    "New Orleans Jazz"
             when 1930..1939 then    "Swing"
             when 1940..1950 then    "Bebop"
             else                    "Jazz"
             end

#### Loops   

The while loop executes its body zero or more times as long as its condition is true.

The until loop is the opposite; it executes the body until the condition becomes true:

      until play_list.duration > 60
        play_list.add(song_list.pop)
      end

**for ... fn**

When you write this:

      for song in playlist song.play
      end

Ruby translates it into something like this:

      playlist.each do |song| song.play
      end

'Note:The only difference between the for loop and the each form is the scope of local variables that are defined in the body.'

**break, redo, and next**

The loop control constructs break, redo, and next let you alter the normal flow through a loop or iterator.

      while line = gets 
        next if line =~ /^\s*#/ # skip comments 
        break if line =~ /^END/	# stop at end
        
        # substitute stuff in backticks and try again

        redo if line.gsub!(/‘(.*?)‘/) { eval($1) } 
        
        # process line ...

      end

#### Variable Scope, Loops, and Blocks 

The while, until, and for loops are built into the language and do not introduce new scope;
previously existing locals can be used in the loop, and any new locals created will be available afterward

The scoping rules for blocks (such as those used by loop and each) are different. Normally,
the local variables created in these blocks are not accessible outside the block:

      [ 1, 2, 3 ].each do |x| 
        y=x+1
      end
      [ x, y ]

'produces:'

      prog.rb:4:in ‘<main>': undefined local variable or method ‘x' for main:Object (NameError)

'Note that the assignment to the variable doesn’t have to be executed;' 

      x = "initial value" 
      y = "another value" 
      [ 1, 2, 3 ].each do |x|
        y=x+1
      end
      [ x, y ]        # => ["initial value", 4]


### Chapter 11 'Basic Input Output'
Ruby provides what at ﬁrst sight looks like two separate sets of I/O routines. The ﬁrst is the
simple interface—we’ve been using it pretty much exclusively so far:

     print "Enter your name: "
     name = gets

A whole set of I/O-related methods is implemented in the Kernel module—gets, open, print,
printf, putc, puts, readline, readlines, and test—that makes it simple and convenient to write
straightforward Ruby programs.

The second way, which gives you a lot more control, is to use IO objects.

#### What Is an IO Object?

Ruby deﬁnes a single base class, IO, to handle input and output. This base class is subclassed
by classes File and BasicSocket to provide more specialized behavior, but the principles are
the same. An IO object is a bidirectional channel between a Ruby program and some external
resource.1 An IO object may have more to it than meets the eye, but in the end you still simply
write to it and read from it.

#### Opening and Closing Files

As you may expect,  you can create a new file object  using File.new
 
**example**

     file = File.new("testfile", "r")
       # ... process the file
     file.close

The ﬁrst parameter is the ﬁlename. The second is the mode string, which lets you open the ﬁle
for reading, writing, or both. (Here we opened testﬁle for reading with an "r". We could also have
used "w" for write or "r+" for read-write. 

But here Ruby can make life a little bit easier for you. The method 

      File.open 

also opens a ﬁle. In regular use, it behaves just like File.new. However, if you associate a block with the call,
open behaves differently. Instead of returning a new File object, it invokes the block, passing the
newly opened File as a parameter. When the block exits, the ﬁle is automatically closed.

      File.open("testfile", "r") do |file|
            # ... process the file
      end   # <- file automatically closed here

The difference between methods  In the earlier case, if an exception is raised while
processing the ﬁle, the call to ﬁle.close may not happen.

but this may not happen for a while. Meanwhile, resources are being held open.

If an exception is raised inside the block, the ﬁle is closed before the exception is propagated on to the caller. 
It’s as if the open method looks like the following:

     class File
      def File.open(*args)
       result = f = File.new(*args)
        if block_given?
         begin
           result = yield f
           ensure
           f.close
         end
        end
       result
      end
     end

#### Reading and Writing Files

The same methods that we’ve been using for “simple” I/O are available for all ﬁle objects. So,
gets reads a line from standard input, and ﬁle.gets reads a line from the ﬁle object ﬁle.

For example, we could create a program called copy.rb:

     while line = gets
      puts line
     end

running the example:

     $ ruby copy.rb
      These are lines
      These are lines
      that I am typing
      that I am typing
      ^D

We can also pass in one or more ﬁlenames on the command line, in which case gets will read
from each in turn:

      $ ruby copy.rb testfile
      This is line one
      This is line two
      This is line three
      And so on...

we can explicitly open the ﬁle and read from it:

     File.open("testfile") do |file|
      while line = file.gets
       puts line
      end
     end

produces:

     This is line one
     This is line two
     This is line three
     And so on...

##### Iterators for Reading

As well as using the usual loops to read data from an IO stream, you can also use various Ruby
iterators. IO#each_byte invokes a block with the next 8-bit byte from the IO object (in this case, 
an object of type File). The chr method converts an integer to the corresponding ASCII character:

     File.open("testfile") do |file|
       file.each_byte.with_index do |ch, index|
         print "#{ch.chr}:#{ch} "
         break if index > 10
       end
     end

oproduces:

     T:84 h:104 i:105 s:115
     :32 i:105 s:115
     :32 l:108 i:105 n:110 e:101


##### Writing to Files

With a couple of exceptions, every object you pass to puts and print is converted to a string by calling that
object’s to_s method. If for some reason the to_s method doesn’t return a valid string, a string is created
containing the object’s class name and ID, something like #<ClassName:0x123456>:

     # Note the "w", which opens the file for writing
     File.open("output.txt", "w") do |file|
      file.puts "Hello"
      file.puts "1 + 2 = #{1+2}"
     end
     # Now read the file in and print its contents to STDOUT
     puts File.read("output.txt")
     produces:
     Hello
     1 + 2 = 3

The exceptions are simple, too. The nil object will print as the empty string, and an array passed
to puts will be written as if each of its elements in turn were passed separately to puts.

#### Talkin to Networks

Ruby is ﬂuent in most of the Internet’s protocols, both low-level and high-level.
Ruby comes with a set of classes in the socket
These give you access to TCP, UDP, SOCKS, and Unix domain sockets, as well as any additional socket types
supported on your architecture. The library also provides helper classes to make writing servers easier. 
Here’s a simple program that gets infor-mation about our user website on a local web server using 
the HTTP OPTIONS request:

     require 'socket'
      client = TCPSocket.open('127.0.0.1', 'www')
       client.send("OPTIONS /~dave/ HTTP/1.0\n\n", 0)
       puts client.readlines
      client.close

     # 0 means standard packproduces:

     HTTP/1.1 200 OK
     Date: Wed, 11 May 2011 22:04:32 GMT
     Server: Apache/2.2.17 (Unix) mod_ssl/2.2.17 OpenSSL/0.9.8l DAV/2
     Allow: GET,HEAD,POST,OPTIONS,TRACE
     Content-Length: 0
     Connection: close
     Content-Type: text/html


The lib/net set of library modules provides hanlevel protocols (currently FTP, HTTP, POP, SMTP, and telnet). 

     require 'net/http'

     http = Net::HTTP.new('pragprog.com', 80)
      response = http.get('/titles/ruby3/programming-ruby-3')
       if response.message == "OK"
       puts response.body.scan(/<img alt=".*?" src="(.*?)"/m).uniq[0,4]
     end


produces:

     http://assets0.pragprog.com/images/logo.gif?1304984874
     http://assets3.pragprog.com/images/login-button.gif?1304984874
     http://imagery.pragprog.com/products/99/ruby3_xlargecover.jpg?1298589754
     http://imagery.pragprog.com/products/22/fr_rr_smallcover.jpg?1298589700


#####  Parsing HTML

     require 'open-uri'
      page = open('http://pragprog.com/titles/ruby3/programming-ruby-1-9').read
       if page =~ %r{<title>(.*?)</title>}m
       puts "Title is #{$1.inspect}"
     end

produces: 

     Title is "The Pragmatic Bookshelf | Programming Ruby 1.9"
     Having read HTML from a website, you might want to parse information out of it.

But regular expressions won’t always work. For example, if someone had an extra space in the
<title> tag, the match would have failed. For real-world use, you probably want to use a library

To use this in a real world you probably want to use  a library to parser html

Example using a gem:

     require 'open-uri'
     require 'hpricot'
     page = Hpricot(open('http://pragprog.com'))

     puts "Page title is " + page.at(:title).inner_html

     # Output the first paragraph in the div with an id="copyright"

     puts page.at('div#copyright p')

     # Output the second hyperlink in the site-links div

     puts "\nSecond hyperlink is"
     puts page.at('div#site-links a:nth(2)')

produces:

     Page title is The Pragmatic Bookshelf
     <p>
     The <em>Pragmatic Bookshelf™</em> is an imprint of
     <a href="http://pragprog.com/">The Pragmatic Programmers, LLC</a>.
     <br />
     Copyright © 1999–2011 The Pragmatic Programmers, LLC.
     All Rights Reserved.
     </p>
     Second hyperlink is
     <a href="http://pragprog.com/community">Connect!</a>

### Chapter 13 'Unit Testing'

We reviewed TDD and BDD.

#### TDD

Unit testing focus on the output of methods. We use test_unit a library included in ruby distribution.

#### BDD
We discussed about Behaviour Driven Development where we write our expectations from the user persepctive. The steps are:

1. We write the test
2. We run the test and test fails
3. We build application code
4. We run the test and test asserts


#### Tools

- test_unit
- rspec
- cucumber
- shoulda

**Test_unit**

Unit testing is testing that focuses on small chunks (units) of code, typically individual methods
or lines within methods. This is in contrast to most other forms of testing, which consider the
system as a whole

* advantadges

** you find the bug while the code is still fresh in your mind
** Unit testing helps developers write better code 
** it helps others understand how to use your code
** The flexibility of Ruby makes writing tests easy

Let’s say we’re testing a Roman number class. So far, the code is pretty simple: it just lets us
create an object representing a certain number and display that object in Roman numerals:

      # This code has bugs
      class Roman
        MAX_ROMAN = 4999

        def initialize(value)
          if value <= 0 || value > MAX_ROMAN
            fail "Roman values must be > 0 and <= #{MAX_ROMAN}"
          end
          @value = value
        end

        FACTORS = [["m", 1000], ["cm", 900], ["d",  500], ["cd", 400],
                  ["c",   100], ["xc",  90], ["l",   50], ["xl",  40],
                  ["x",    10], ["ix",   9], ["v",    5], ["iv",   4],
                  ["i",     1]]

        def to_s
          value = @value
          roman = ""
          for code, factor in FACTORS
            count, value = value.divmod(factor)
            roman << code unless count.zero?
          end
          roman
        end
      end

We could test this code by writing another program, like this:

      require_relative 'romanbug'
      require 'test/unit'
      class TestRoman < Test::Unit::TestCase
        def test_simple
            assert_equal("i",   Roman.new(1).to_s)
            assert_equal("ii",  Roman.new(2).to_s)
            assert_equal("iii", Roman.new(3).to_s)
            assert_equal("iv",  Roman.new(4).to_s)
            assert_equal("ix",  Roman.new(9).to_s)
        end
      end

produces:

        Loaded suite /tmp/prog
        Started
        F
        Finished in 0.000703 seconds.
          1) Failure:
        <"ii"> expected but was
        <"i">.

        1 tests, 2 assertions, 1 failures, 0 errors, 0 skips
        test_simple(TestRoman) [/tmp/prog.rb:6]:


The second assertion failed.See how the error message uses the fact that the assert
knows both the expected and actual values: it expected to get “ii” but instead got “i.” Looking
at our code, you can see a clear bug in to_s. If the count after dividing by the factor is greater
than zero, then we should output that many Roman digits. The existing code outputs just one.
The fix is easy:

      def to_s
      value = @value
      roman = ""
        for code, factor in FACTORS
          count, value = value.divmod(factor)
          roman << (code * count)
        end
        roman
      end

Now let’s run our tests again and already!



**RSpec**

RSpec is very much concerned with driving the design side of things. You can write and execute
specs with RSpec well before you’ve written a line of application code. These specs, when run,
will output the user stories that describe your application. Then, as you fill in the code, the specs
mutate into tests that validate that your code meets your expectations.

The scoring system used in lawn tennis originated in the Middle Ages. As players win successive
points, their scores are shown as 15, 30, and 40. The next point is a win unless your opponent
also has 40. If you’re both tied at 40, then different rules apply—the first player with a clear
two-point advantage is the winner.


We have to write a class that handles this scoring system. Let’s use RSpec specifications to drive
the process. We install RSpec with gem install rspec. We’ll then create our first specification file:

      describe "TennisScorer", "basic scoring" do
        it "should start with a score of 0-0"
        it "should be 15-0 if the server wins a point"
        it "should be 0-15 if the receiver wins a point"
        it "should be 15-15 after they both win a point"
        # ...
      end

Note: This file contains nothing more than a description of an aspect of the tennis scoring class (that
we haven’t yet written, by the way). It contains a description of the basic scoring system and we’ve assumed we have a class
TennisScorer in a file called tennis_scorer.rb

RSpec gives us an alternative way of setting up conditions for our tests. The let method
creates what looks like a variable (it’s actually a dynamically defined method) whose value is
given by evaluating a block. This lets us write the following:

      require_relative "tennis_scorer"
      describe TennisScorer, "basic scoring" do
        let(:ts) { TennisScorer.new}
        it "should start with a score of 0-0" do
        ts.score.should == "0-0"
        end
          it "should be 15-0 if the server wins a point" do
        ts.give_point_to(:server)
          ts.score.should == "15-0"
          end
          it "should be 0-15 if the receiver wins a point" do
        ts.give_point_to(:receiver)
          ts.score.should == "0-15"
          end
          it "should be 15-15 after they both win a point" do
          ts.give_point_to(:receiver)
        ts.give_point_to(:server)
          ts.score.should == "15-15"
          end
      end

We’re going to stop here, but I suggest that you might want to take this code and continue to
develop it. Write expectations such as these:

      it "should be 40-0 after the server wins three points"
      it "should be W-L after the server wins four points"
      it "should be L-W after the receiver wins four points"
      it "should be Deuce after each wins three points"
      it "should be A-server after each wins three points and the server gets one more"
      it "should be A-receiver after each wins three points and the receiver gets one more"

and so on. Note that none of these expectations is met by our current implementation.

**Shoulda**

RSpec is testing with attitude. On the other hand, Shoulda takes many of the ideas from RSpec
and humbly offers them to you for integration into your regular unit tests. For many developers,
particularly those with existing Test::Unit tests, this is a good compromise. You get much of the
descriptive power of RSpec-style expectations without having to commit to the full framework.

        Install Shoulda using gem install shoulda.

Let’s recast our final RSpec tennis scoring tests using Shoulda:

      require 'test/unit'
      require 'shoulda'
      require_relative 'tennis_scorer.rb'

      class TennisScorerTest < Test::Unit::TestCase

        def assert_score(target)
          assert_equal(target, @ts.score)
        end

        context "Tennis scores" do
          setup do
          @ts = TennisScorer.new
          end

          should "start with a score of 0-0" do
            assert_score("0-0")
          end

          context "where the server wins a point" do
            setup do
              @ts.give_point_to(:server)
            end

            should "be 15-0" do
              assert_score("15-0")
            end

            context "and the oponent wins a point" do
              setup do
                @ts.give_point_to(:receiver)
              end
              should "be 15-15" do
                assert_score("15-15")
              end
            end
          end

            should "be 0-15 if the receiver wins a point" do
              @ts.give_point_to(:receiver)
              assert_score("0-15")
            end
          end
        end

Let’s run it:

        $ ruby ts_shoulda_1.rb
        Loaded suite ts_shoulda_1
        Started

      Finished in 0.000803 seconds.
      4 tests, 4 assertions, 0 failures, 0 errors, 0 skips

Would we use these nested contexts for this tennis scoring example? We probably wouldn’t as it
stands, because the linear form is easier to read. But we use them all the time when we have tests
where we want to run through a complex scenario that builds from test to test. This nesting lets
us set up an environment, run some tests, then change the environment, run more tests, change
it again, run even more tests, and so on. It ends up making tests far more compact and removes
a lot of duplication


This is a summary from [Programming Ruby](http://pragprog.com/book/ruby/programming-ruby) book

