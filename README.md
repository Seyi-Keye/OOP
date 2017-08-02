# Object Oriented Programming (OOP)

A program that implements 
** abstraction, 
** encapsulation, 
** inheritance, 
** polymorphism, 
** methods, and 
** overloading

# Inheritance
 Inheritance is when a class inherits behavior from another class. The class that is inheriting behavior is called the subclass and the class it inherits from is called the superclass. A simple example is 
 ```
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

# Overloading
This occurs when a method that is available witin a subclass through inheritance takes in more number of arguments which in turn changes the output.
```

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
