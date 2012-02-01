# Ruby Basics

## Introduction

Ruby is a language of careful balance. Its creator, [Yukihiro “matz” Matsumoto](http://www.rubyist.net/~matz/), blended parts of his favorite languages (Perl, Smalltalk, Eiffel, Ada, and Lisp) to form a new language that balanced functional programming with imperative programming.

He has often said that he is “trying to make Ruby natural, not simple,” in a way that mirrors life.

Building on this, he adds:

Ruby is simple in appearance, but is very complex inside, just like our human body.

Initially, Matz looked at other languages to find an ideal syntax. Recalling his search, he said, “I wanted a scripting language that was more powerful than Perl, and more object-oriented than Python3.”

In Ruby, everything is an object. Every bit of information and code can be given their own properties and actions. Object-oriented programming calls properties by the name instance variables and actions are known as methods. Ruby’s pure object-oriented approach is most commonly demonstrated by a bit of code which applies an action to a number.

    5.times { print "We *love* Ruby -- it's outrageous!" }

##  Ruby and it's features

We'll start to talk more about Ruby and it's technical features, and if you wanna taste the Ruby's flavor at the same time that you are reding this, I recommend you to use the irb "Interactive Ruby" command-line environment just by using this command:

    $ irb
    ruby-1.9.2-p290 :001 > 

And now you'll be able to see what's happening on every step on this tutorial.

### Standard types

Ruby supports integer, float, rational, complex, strings, and almost every standard type that you need to use whe you are developing with ruby.

#### Numbers

Integers can be whatever size you want it to be, but Ruby divides this types in two specific types, like  'Bignum' and 'Fixnum'. The limit of a number to be considered Fixnum is 2^62-1, and if the number is bigger than this size, Ruby automatically recognize him like Bignum, lets check it out that.

    1.9.2-p290 :001 > n = 1
    1.9.2-p290 :002 > n.class
    => Fixnum 
    1.9.2-p290 :003 > n = 99999999999999999999999999999999999999999999999999
    1.9.2-p290 :004 > n.class
    => Bignum 

If you use decimal float numbers you don't need to define it, just use it like: 

    ruby-1.9.2-p290 :001 > n = 1.25;
    ruby-1.9.2-p290 :002 > n.class
     => Float 

And finally you can use rational numbers too, like:

    ruby-1.9.2-p290 :003 > Rational(3,4)*Rational(3,4)
     => (9/16) 
    ruby-1.9.2-p290 :004 > Complex(3,4)*Complex(3,4)
     => (-7+24i)

#### Strings

On ruby, strings are characters sequency as any other programming language, and are delimited by double quotes like:

    1.9.2-p290 :001 > s = "This is a string"
    1.9.2-p290 :002 > s.class
     => String 
    1.9.2-p290 :003 > print s
     This is a string => nil     

You can insert code inside the strings like, sums, functions, other objects, you just need to specify where is the Ruby function inside the string with this syntax #{}:

    1.9.2-p290 :001 > s = "Today is #{Time.now}"
    1.9.2-p290 :002 > print s
    Today is 2012-02-01 16:11:21 -0600 => nil 

#### Ranges

Ranges are data types that allows you to define a number sequence with a simple syntax like "1..10", lets watch this alive!

    1.9.2-p290 :001 > digito = 1..10
    1.9.2-p290 :002 > print digito
    1..10 => nil 
    1.9.2-p290 :003 > print digito.to_a
    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] => nil 
    1.9.2-p290 :004 > digito.class
     => Range 

As we know, this data types are not arrays at all, but you can manipulate it as arrays too. 

    1.9.2-p290 :005 > digito.min
     => 1 
    1.9.2-p290 :006 > digito.max
     => 10 
    1.9.2-p290 :007 > digito.reject { |i| i < 5 }
     => [5, 6, 7, 8, 9, 10] 
    1.9.2-p290 :008 > digito.inject(:+)
     => 55

You also can use ranges with conditions `range_example.rb`:

    while line = gets
      puts line if line =~ /start/ .. line =~ /end/
    end
    
    car_age = gets.to_f
    
    case car_age
    when 0...1
      puts "New car"
    when 1...3
      puts "Recent model"

### Control structures

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
