### Tips
- Ruby’s strings are mutable
- Call the￼ `freeze` method on a string (or on any object) to prevent any future modifications to that object.
-  The value of nil is treated the same as false, and any other value is the same as true. 
- puts prints a string of text to the console and appends a newline
- =begin =end \__END__
As we’ve seen, =begin and =end at the beginning of a line delimit multiline comments. And the token __END__ marks the end of the program (and the beginning of a data section) if it appears on a line by itself with no leading or trailing whitespace.
- When Ruby requires a Boolean value, nil behaves like false, and any value other than nil or false behaves like true.
- When Ruby sees !=, it simply uses the == operator and then inverts the result.
- There are two important differences between the clone and dup methods defined by Object. First, clone copies both the frozen and tainted state (defined shortly) of an object, whereas dup only copies the tainted state; calling dup on a frozen object returns an unfrozen copy. Second, clone copies any singleton methods of the object, whereas dup does not.
-  if the user does not specify the array, you want to create a new, empty array. You might use this line:
results ||= []
- When an rvalue is preceded by an asterisk, it means that that value is an array (or an array-like object) and that its elements should each be rvalues. 
- Module.#[prepend](http://dev.af83.com/2012/10/19/ruby-2-0-module-prepend.html)

	```
	x, y, z = 1, *[2,3] # Same as x,y,z = 1,2,3
	x,*y = 1, 2, 3 # x=1; y=[2,3] 
	*x,y = 1, 2 # x=[1]; y=2
	x,*y = 1 # x=1; y=[]
	x, y, *z = 1, *[2,3,4] # x=1; y=2; z=[3,4].
	```

```
#!/usr/bin/ruby -w  		##shebang comment 
# -*- coding: utf-8 -*-   	##coding comment
require 'socket' 			##load networking library
...  						##program code goes here
__END__ 
...  						##mark end of code program data goes here
```

### Tools
#### irb
#### ri
```
ri Array
ri Array.sort 
ri Hash#each 
ri Math::sqrt
```
#### gem
```
gem list
gem enviroment
gem update rails gem update
gem update --system gem uninstall rails
# List installed gems
# Display RubyGems configuration information # Update a named gem
# Update all installed gems
# Update RubyGems itself
# Remove an installed gem
```

### Symbol
#### Variables
- \$ Global variables are prefixed with a dollar sign. 

- @ Instance variables are prefixed with a single at sign, and class variables are prefixed with two at signs. Instance variables and class variables are explained in Chapter 7.
- ? As a helpful convention, methods that return Boolean values often have names that end with a question mark.

- ! Method names may end with an exclamation point to indicate that they should be used cautiously. This naming convention is often to distinguish mutator methods that alter the object on which they are invoked from variants that return a modified copy of the original object.

- = Methods whose names end with an equals sign can be invoked by placing the method name, without the equals sign, on the left side of an assignment operator

```
$files # A global variable
@data # An instance variable
@@counter # A class variable
empty? # A Boolean-valued method or predicate
sort! # An in-place alternative to the regular sort method timeout= # A method invoked by assignment
```

### Methods
```
def square(x) 
	x*x
end
```

```
def polar(x,y)
	theta = Math.atan2(y,x) 
	r = Math.hypot(x,y) 
	[r, theta]
end
```

### Assignment
```
x, y = 1, 2
```

### Regular expression
```
/[Rr]uby/ # Matches "Ruby" or "ruby" 
/\d{5}/ # Matches 5 consecutive digits 
1..3 # All x where 1 <= x <= 3 
1...3 # All x where 1 <= x < 3
```

### Class
#### Sequence 
```
s = Sequence.new(1, 10, 2) #From 1 to 10 by 2's
s.each{|x| print x }
```


### Loop
```
9.downto(1) {|n| print n }
```
```
1.upto(10) do |x| 
	print x
end
```


### String
#### Operator
- +
- <<
```
alphabet = "A"
alphabet << ?B # Alphabet is now "AB"
```
- *
```
ellipsis = '.'*3 # Evaluates to '...'
```

```
a = 0;
"#{a=a+1} " * 3 # Returns "1 1 1 ", not "1 2 3 "
```

###Array
```
words = %w[this is a test] open = %w| ( [ { < | white = %W(\s \t \r \n)
# Same as: ['this', 'is', 'a', 'test'] # Same as: ['(', '[', '{', '<']
# Same as: ["\s", "\t", "\r", "\n"]
```

- union and intersection
```
a = [1, 1, 2, 2, 3, 3, 4] b = [5, 5, 4, 4, 3, 3, 2]
a | b # [1, 2, 3, 4, 5]: duplicates are removed
b | a # [5, 4, 3, 2, 1]: elements are the same, but order is different
a & b # [2, 3, 4]
b & a # [4, 3, 2]
```

- +
```
a = [1, 2, 3] + [4, 5] a = a + [[6, 7, 8]]
a = a + 9
# [1, 2, 3, 4, 5]
# [1, 2, 3, 4, 5, [6, 7, 8]]
# Error: righthand side must be an array
```

- <<
```
a = []
a << 1
a << 2 << 3 a << [4,5,6]
# Start with an empty array # a is [1]
# a is [1, 2, 3]
# a is [1, 2, 3, [4, 5, 6]]
```

### Hashes
- =>
```
numbers = { "one" => 1, "two" => 2, "three" => 3 }
numbers = { :one => 1, :two => 2, :three => 3 }
```

### Ranges

- define
```
1..10 # The integers 1 through 10, including 10
1.0...10.0 # The numbers between 1.0 and 10.0, excluding 10.0 itself
```

- enumerate
```
r = 'a'..'c'
r.each {|l| print "[#{l}]"} # Prints "[a][b][c]"
r.step(2) { |l| print "[#{l}]"} # Prints "[a][c]"
r.to_a # => ['a','b','c']: Enumerable defines to_a
```

- test
```
r = 0...100
r.member? 50 # => true: 50 is a member of the range
r.include? 100 # => false: 100 is excluded from the range
r.include? 99.9 # => true: 99.9 is less than 100
```

### Symbols

```
:symbol
:"symbol"
:'another long symbol'
# A Symbol literal
# The same literal
# Quotes are useful for symbols with spaces
s = "string"
sym = :"#{s}"
# The Symbol :string
```

- Usage
	- Symbols are often used to refer to method names in reflective code. For example, suppose we want to know if some object has an each method:
	```
o.respond_to? :each
	```

	- Here’s another example. It tests whether a given object responds to a specified method, and, if so, invokes that method:

	```
name = :size
if o.respond_to? name
		o.send(name) 
end
	```

- Note
	- Two strings with the same content will both convert to exactly the same Symbol object. Two distinct Symbol objects will always have different content.



### Bool
- Check

```
o == nil # Is o nil?
o.nil? # Another way to test
```

### Object
- id: object_id method, \__id__

- Check
	- class: 
	```
	o.class == String # true if is o a String
	o.instance_of? String # true if o is a String
	```
	
		```
		x= 1
		x.instance_of? Fixnum # This is the value we're working with
		x.instance_of? Numeric # true: is an instance of Fixnum
		x.is_a? Fixnum # false: instance_of? doesn't check inheritance # true: x is a Fixnum
		x.is_a? Integer # true: x is an Integer
		x.is_a? Numeric # true: x is a Numeric
		x.is_a? Comparable # true: works with mixin modules, too
		x.is_a? Object # true for any value of x
		Numeric === x # true: x is_a Numeric
		```

	- method:
		
		```
	o.respond_to? :"<<" # true if o has an << operator
		```
	>The shortcoming of this approach is that it only checks the name of a method, not the arguments for that method. 

	- Object Equality

	- equal?
	```
	a = "Ruby" # One reference to one String object
	b = c = "Ruby" # Two references to another String object 
	a.equal?(b) # false: a and b are different objects
	b.equal?(c) # true: b and c refer to the same object
	a.object_id == b.object_id # Works like a.equal?(b)
	```
	
	- ==
	```
	a == b # true: but these two distinct objects have equal values
	```

	- eql?
	
		```
1 == 1.0 # true: Fixnum and Float objects can be == 
1.eql?(1.0) # false: but they are never eql!
		```
	
	 > The Hash class uses eql? to check whether two hash keys are equal.

	- ===
	```
	(1..10) === 5 # true: 5 is in the range 1..10
	/\d+/ === "123" # true: the string matches the regular expression String === "s" # true: "s" is an instance of the class String :s === "s" # true in Ruby 1.9
	```

	- =~
		- The =~ operator is defined by String and Regexp (and Symbol in Ruby 1.9) to perform pattern matching
		- !~ is defined as the inverse of =~

- <=>
	```
		1 <=> 5 	# -1
		5 <=> 5 	# 0
		9 <=> 5 	# 1
		"1" <=> 5 # nil: integers and strings are not comparable
	```

- Implicit conversion
	- The most common methods in this category are to_s, to_i, to_f, and to_a to convert to String, Integer, Float, and Array, respectively.

### Variables
- Constant
	
```
Conversions::CM_PER_INCH # Constant defined in the Conversions module 
modules[0]::NAME # Constant defined by an element of an array
::ARGV # The global constant ARGV
```