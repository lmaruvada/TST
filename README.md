# TST
Solved a C++ test using TST.
Problem: 
The application 'buggy.cxx' performs the following functions:

a) It reads a list of ASCII words from STDIN, a word per input
line, terminated by the word 'end'.

b) It removes the duplicates, sorts the words alphabetically,
and prints them with the number of how many times each word
was encountered.

c) Then it repeatedly asks the user to enter a word and tries to
look it up in the word list which was entered initially. It
terminates when it encounters EOF.

The program has a number of bugs and design deficiencies. Please,
fix all problems that you can find and make all the improvements
you deem necessary so that the result satisfies your personal
standards.

The only restriction is that the multi-thread nature of the application
and the overall structure MUST be preserved. (In other words,
you shouldn't, for example, convert it to a single thread, even
if you think it would work better in that way).

Summary of my changes: 

 I chose to use a Ternary Search Trie for storing and getting the words. Since Vector is a dynamic array doubling in size as the number of input words increases. But the increase in size comes with making a new array with double size and copying the data from one array to another. The facilities provided by Vectors is good when the number of input words is smaller. 

While sort is not too bad with N*Ln N complexity the TST has certain advantages for strings. 

Average case complexity in TST:
Search : L+Ln N
Search Miss: Ln  N
Insert : L +  Ln N

 TST: Works only for strings (or digital keys).     Examines just enough key characters and search miss may involve only a few characters. Allows for ordered interation, prefix matches. The data in inserted sorted. 
I used mutex lock for the atomic operation of inserting input into the TST. Most likely my thread handling can be improved upon. This is one of the rare times I worked with threads. 

Comments and suggestions are welcome. My inspiration to use TST comes from the recent course I had taken in Coursera "Algorithms II" offered by Princeton University. 
