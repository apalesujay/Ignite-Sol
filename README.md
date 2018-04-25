# Answers to Ignite Solutions Technical Puzzles - 1

###Question 1:
Write a function that takes an array of integers and returns that array rotated by N positions using Python or Ruby or JavaScript.
For example, if N=2, given the input array [1, 2, 3, 4, 5, 6]
the function should return [5, 6, 1, 2, 3, 4]
####Solution:
*Language* : ***Python 3***

	def rotate_array(array,N):
    	'''
    	Function returns the array rotated by 'N' positions.
    	'''
    	array_length = len(array)
		
    	#If the value of N is greater than the length of array then we recalculate the value of N
    	if N > array_length:
        	N = N % array_length
		
    	#Rotate the array by N positions
    	array = array[-N:] + array[:-N]
		
    	return array
		
	#Driver code
	array = list(map(int, input("Enter integer values separated by a space\nAnd hit ENTER to proceed further:\n").split()))
	N = int(input("Enter a number to rotate the array:\n"))
	print(rotate_array(array,N))

### Question 2:
In JavaScript, answer if the following expressions result in true or false (and explain your answer)
a. "0" == 0 // true or false?
b. "" == 0 // true or false?
c. "" == "0"// true or false?
#### Solution:
**a.** true
When we use  '==' operator in javascript , the comparison is pretty straigh forward if operands on both the side of '==' are of same type. But if the operands do not have same data type then javascript converts the type of one operand to match with other(if the type conversion is possible).
In this case, the first operand is of type **String** and the second operand is of type **Number**.  So as per the** ECMAScript** rules, if one operand is a String and another operand is a Number then the String operand is converted to type Number(if the type conversion is possible). Thus, in this case the result is **true** because the first operand i.e. **"0"** can be coerced to number **0** so as to match the data type of second operator i.e. **0**.

**b.** true
In this case, the first operand is an **empty String** and the second operand is a **Number**. Similar to the previous case, first operand gets converted to a Number. And in javascript, if the String is empty i.e. **""** and is coerced to type Number then we get output as Number **0**. Hence the result is **true** as both the operands are Number **0**.

**c.** false
In this case, both the operands around '==' operator are of type String but the first operand is an empty String and the second operand is not an empty String. And the result of comparison of two strings is true only if both the strings have same sequence of characters. Hence, the result of this case is **false** as the character sequence doesn't match

### Question 3:
Most languages have a built in sort method that will sort an array of strings alphabetically. Demonstrate how to sort an array of strings by the length of each string, shortest strings first.

Hint: *clean, small code wins*
#### Solution:
*Language* : ***Python 3***

	def sort_by_length(string_list):
		'''
		Functions returns the list of strings sorted by length of each string
		'''
		string_list.sort(key=len)
		return string_list

	#Driver code
	string_list = list(input().split())
	print(sort_by_length(string_list))

### Question 4:
	function weird(x) {
		var tmp = 3;
		return function(y) {
			return x + y + ++tmp;
		}
	}
	var funny = weird(2);
	var final_answer = funny(10);

What is the value of 'final_answer' at the end of this snippet? Please explain your answer.
#### Solution:
Value of variable **final_answer** at the end of code snoppet is **16**. The explaination is given below:
- In our code, first line 7 gets executed and 'weird()' gets called on line 7 with argument 2 being passed to it.
- Now control gets transferred to line 1 in our code. Here value of 'x' becomes 2 and program control now immediately enters inside weird().
- On line 2, value of 'tmp' variable becomes 3.
- As we proceed to line 3 of our code, an anonymous function with a single parameter 'y' is returned.
- The control again moves to line 7 and and the anonymous functions which was returned in last step is assigned to variable 'funny'.
- On the next line in our code i.e. line 8, funny() is called with argument 10 and control enters inside function at line 3. Value of variable 'y' becomes 10 here.
- Inside this function, at line 4, value of expression `x + y + ++tmp` is calculated. As we can see from the previous steps 'x = 2', 'y = 10' and 'tmp = 3'. Thus the value of the expression calculates to 16 and this value is returned immediately on the same line.
- Finally the control gets transferred back to the line 8 and the value returned in the last step gets assigned to variable 'final_anwer'. Hence, the value of 'final_answer' is 16.

### Question 5:
Consider the following pattern:
`A → D` `M → P` `X → A`
`a → d` `m → p` `x → a`
Now, write a program to solve the following message using Python, JavaScript or Ruby.

***Vrphwklqj phdqlqjixo***

Hint: *The answer is something meaningful.*
#### Solution:
*Language* : ***Python***

	def decoder(message):
		decoded_message = ""
		key = 3
		for char in message:
			ascii_value = ord(char) - key
			
			if char.islower():
				
				#If ascii_value is less than ascii_value of 'a'
				#then loop around by adding 26 to ascii_value
				if ascii_value < ord('a'):
					ascii_value += 26
					decoded_message += chr(ascii_value)
				else:
					decoded_message += chr(ascii_value)
					
			elif char.isupper():
				
				#If ascii_value is less than ascii_value of 'A'
				#then loop around by adding 26 to ascii_value
				if ascii_value < ord('A'):
					ascii_value += 26
					decoded_message += chr(ascii_value)
				else:
					decoded_message += chr(ascii_value)
			else:
				decoded_message += char
				
		return decoded_message

	#Driver code
	message = "Vrphwklqj phdqlqjixo"
	print(decoder(message))

### Question 6:
Use the following paragraphs (in italics below) as input to the program you wrote for Question 5. It should output a meaningful question. Write a program to solve that question.

Zulwh d surjudp (lq Sbwkrq, MdydVfulsw ru Uxeb) wr srsxodwh dqg wkhq vruw d udqgrpob glvwulexwhg olvw ri 1 ploolrq lqwhjhuv, hdfk lqwhjhu kdylqj d ydoxh >= 1 dqg <= 100 zlwkrxw xvlqj dqb exlowlq/hawhuqdo oleudub/ixqfwlrq iru vruwlqj.

Brxu surjudp vkrxog fduhixoob frqvlghu wkh lqsxw dqg frph xs zlwk wkh prvw hiilflhqw vruwlqj vroxwlrq brx fdq wklqn ri. Surylgh wkh vsdfh dqg wlph frpsohalwb ri brxu dojrulwkp.
#### Solution:
*Language* : ***Python***

	import time
	from random import randint
	
	def timed(f):
	'''
	Decorator function for just showing the time required by some other function.
	In our case, it is used to show the time required by countingsort() function to sort million integers.
	'''
		def _timed(*args, **kwargs):
			start = time.time()
			v = f(*args, **kwargs)
			t = time.time() - start
			print ("runtime for function %s: %s" %(f.__name__, str(t)))
			return v
		return _timed
		
	@timed
	def countingsort(A, high=None):
	'''
	Function for sorting a very big list of integers.
	'''
		# high and low can be provided as parameters for optimizations
		# assume good input for a counting sort algorithm
		if high is None:
			high = max(A)
		
		N = len(A)
		#Create buckets list containing bucket for each value and initialize each bucket with zero
		buckets = [0 for x in range(high + 1)]
		#Increment the count of bucket by 1 for a particular value in million_ints
		for value in million_ints:
			buckets[value] += 1
			
		#Create right indices
		#Initialize to zero
		indexes = [0 for x in range(high + 1)]
		for i in range(len(indexes)):
			if i > 0:
				indexes[i] = indexes[i-1] + buckets[i-1]
				
		#Sort
		#Initilize the result array with zero
		result = [0 for x in range(N)]
		for value in million_ints:
			index = indexes[value]
			result[index] = value
			indexes[value] += 1
		return result
	
	#Driver code
	if __name__ == '__main__':
	#Populate the list with million random intergers having value >= 1 and value <= 100
		million_ints = [randint(1, 101) for x in range(1000000)]
		print("Done generating list")
		countingsort(million_ints)

**Complexity Analysis**:
Counting sort has a ***O(k + N)***  running time.

The first loop goes through an array , which has 'N' elements. This step has a running time of *O(N*. The second loop has running time of *O(k)* as it iterates over 'k' . The third loop iterates again through array of size 'n'. So this has also a running time of *O(N)* . Therefore, the counting sort algorithm has a running time of ***O(n + k)***.

Counting sort has ***space complexity*** of ***O(k + N)***.

We can reduce time and space complexity to O(N) as k is nigligible as compared to N.


### Question 7:
####Solution:
*Language* : ***Python***

	def reverse(string):
		'''
		Function to reverse each word in string where a word is defined as a continuous sequence of alphanumeric characters or hyphen '-'.
		'''
		word = statement = ""
		
		for char in string:
		
			#If the character in string is either alphanumeric or hyphen '-'
			#then reverse the words in string
			if char.isalnum() or char == '-':
				word = char + word
		
			#If the character is neither alphanumeric nor hyphen '-'
			#then attach the previous word to the statement
			#and set word to empy string
			#and attach the current character(i.e. special character or space) to the statement
			else:
				if word:
					statement += word
					word = ""
					statement += char
		return statement + word
		
	#Driver Code
	string = input("Enter a string to reverse each word:\n")
	print(reverse(string))