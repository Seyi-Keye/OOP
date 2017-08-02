# Object Oriented Programming (OOP)

Object Oriented Programming, often referred to as OOP, is a programming paradigm that was created to deal with the growing complexity of large software systems. Programmers found out very early on that as applications grew in complexity and size, they became very difficult to maintain. One small change at any point in the program would trigger a ripple effect of errors due to dependencies throughout the entire program.

Programmers needed a way to create containers for data that could be changed and manipulated without affecting the entire program. They needed a way to section off areas of code that performed certain procedures so that their programs could become the interaction of many small parts, as opposed to one massive blob of dependency.

A program that implements 
- abstraction, 
- encapsulation, 
- inheritance, 
- polymorphism, 
- methods, and 
- overloading
will be used in shedding more light on OOP. 

## Abstraction
Abstraction, is process in which a programmer hides all but the relevant data about an object in order to reduce complexity and increase efficiency.

## Encapsulation 
Encapsulation is hiding pieces of functionality and making it unavailable to the rest of the code base. It is a form of data protection, so that data cannot be manipulated or changed without obvious intention. It is what defines the boundaries in your application and allows your code to achieve new levels of complexity. The `private` keyword will be used to explain encapsulation.

``` ruby
class Phone
  def check_security
    p #{passwordable}
  end
  
  def self.get_security_detail
    detail = #{passwordable}
    p detail
  end
  
  private
  def passwordable
    p 'I have a password'
  end
end

seyi = Phone.new
seyi.check_security       //=> nil
Phone.get_security_detail   //=> nil
```
In both instances it returns a `nil` because `passwordable` is a private method. Reasons being that,
- `private` methods cannot be accessed outside its defined class and
-  cannot be called with an instance of a class
It can only be accessed within the class. 
allmethods below the `private` keyword is treated as a `private method`.

## Inheritance
 Inheritance is when a class inherits behavior from another class. The class that is inheriting behavior is called the subclass and the class it inherits from is called the superclass. A simple example is 
 ``` ruby
class Phone
  def calling
    p "My phone is ringing"
  end
end 

class Nokia < Phone
end 

seyi = Nokia.new       //=> #<Nokia:0x0055e7ef5fb478>
seyi.calling           //=> "My phone is ringing"
```

From the example above, the Phone class is the super class that has method `calling` which it passes down to its subclass. In this case, `Nokia` is a Phone and it inherits the `calling` from `Phone`.

## Polymorphism
Inherited function or method with different output. A method that takes on different shape or output. The parent method can be referenced by using a `super` keyword. "Poly" stands for "many" and "morph" stands for "forms". OOP gives us flexibility in using pre-written code for new purposes.
``` ruby
class Phone
  def calling
    p "My phone is ringing"
  end
end 

class Nokia < Phone
  def calling
    p "I am calling you"
    super
  end
end 
end

seyi = Nokia.new    //=> #<Nokia:0x0055e7ef5fb478>
seyi.calling        //=> "I am calling you"
                    //   "My phone is ringing"
```
Even though the method name is the same, the output at the subclass level and that at the super class level is different, this is polymorphism.

## Methods
Methods describe the behavior the programmer is trying to represent within for a class. Methods are defined witin classes and/or modules and they exhibit actions that are specatular to the class or module i question.

``` ruby
class Phone
 def callable
 end
 
 def ringable
 end
end
```
`callable` and `ringable` are methods because they define the behaviour of `Phone`.
There are different types of methods which includes and not limited to
`Instance method `
``` ruby
class Phone
 def initialize
  p "I am called every time an instance of Phone is made"
 end
end
```
`Accessor method`
``` ruby
class Phone
  attr_accessor :tone

  def initialize(tone)
    @tone = tone
  end

  def ringable
    "#{@tone} ring tone!"
  end
end

seyi = Phone.new("Pop")
puts seyi.ringable         //=> Pop ring tone!
puts seyi.tone             //=> Pop
seyi.tone = 'flute'        // sets tone to flute
puts seyi.tone             //=> "flute"
```
` attr_accessor` gives the opportunity for a `setter method` and a `getter method` to be used. ` attr_writer` allows for just `setter methods` while ` attr_reader` allows for only the `getter method`.

`class methods`
Class methods are methods we can call directly on the class itself, without having to instantiate any objects. When defining a class method, we prepend the method name with the reserved word `self`.
``` ruby
class Phone
  def self.ringable
   p "ringing!"
  end
end

Phone.ringable    //=> "ringing!"
```

## Overloading
This occurs when a method that is available witin a subclass through inheritance takes in more number of arguments which in turn changes the output.
``` ruby
class Phone
  def calling
    p "My phone is ringing"
  end
end 

class Nokia < Phone
  def calling(number)
    p "I am calling #{number}"
  end
end 

class Tecno < Phone
  def calling(mine, yours)
    p "#{mine} is dailing #{yours}"
  end
end

seyi = Nokia.new                      //=> #<Nokia:0x0055e7ef5fb478>
seyi.calling('123457')                //=> "I am calling 123457"
trail = Tecno.new                     //=> #<Tecno:0x0055ce63ea2e78>
trail.calling('00111', '41900')       //=> "00111 is dailing 41900"
```
The example above explains overloading, the `calling` method was inherited by the two sibling classes `Nokia and Tecno` from `Phone`. they each overloaded the initial method by passing in more number of arguments to `calling` than the original in the super class thereby each recreating a new output to suite each instance.

