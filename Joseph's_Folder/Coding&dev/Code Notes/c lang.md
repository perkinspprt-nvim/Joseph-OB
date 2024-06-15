# C    
*Low-level go brrrrrr* 

Just some note taking while i study the C programming language.   
This is less of accurate note taking and more of a journal while i study C.   
I'll be studying from "C, the second edition by Brian Kernighan and Dennis Ritchie" since it is an official and trusted source.
I have indulged in the first few topics like how to run c use clang in the MacOs terminal and also know that i need to include the standard input and out put library. "include <stdio.h>".   
I’m personally working on some code using character input and output using "getchar" and "putchar" which only accept a character at a time. Here is some code i wrote today.   
```C

#include <stdio.h>

int main(){

int i = 0;
char message[100];
int c = 0;

while( c != EOF){
 printf("Input sentence (EOF = Ctrl + D) : ");
 c = getchar();
 if (c == EOF){
  break;
}
message[i] = c;
i++;
}
printf("\\nHere are your characters : ");

for (int i = 0; i < sizeof(message); i++){
 printf("\\t%c", message[i]);
}
printf("\\n");

}


```
had a few problems with how the counters and loop were operating but i got it somewhat working.   
FILE COPYING   
Using getchar and putchar, can write a surprising amount of programs like a letter for letter file reader.   
```C
include <stdio.h>
int main(){

int c;
c = getchar();
while(c != EOF){
 putchar(c);
}

}


```
this is the code to the file copier and i first tried making variable "c" a char not an int but it actually was quite buggy.   
OK! i got it, it seems that getchar and putchar do not actually work with characters but instead actually work with integer values that later get translated into there character dorm using the ASCII system. the reason why "int" would be better that "char" is because EOF and all the type-able characters are represented as int allowing for better compatibility and reading.   
CHARACTER COUNTING   
```C

#include <stdio.h>
int main(){

long charCounter;
charCounter = 0;

while(getchar() != EOF){
 charCounter ++;
}

printf("%ld\\n", charCounter);

}


```
I simply used a variable as a counter and incremented it every time "getchar" iterated and never ended due to it having not yet detected the End-Of-File (EOF) character.   
### Line Counting   
For Line counting, i plan to modify my code for character counting code.   
```C
well, i came up with this :
#include <stdio.h>
int main(){

long charCounter ;
int lineCounter, c;

charCounter = 0;
while((c = getchar()) != EOF){
 if(c == "\\n"){
  lineCounter++;
 }
 charCounter ++;
}

printf("\\nCharacters : %ld\\n", charCounter);
printf("\\nLines : %d\\n", lineCounter);
}


```
However, this isn't working   
Apparently "\n" is actually a combination of '\n' and "\0". it is actually a string literal combining a few elements and thus is a pointer somewhere in system memory which then points to '\n'. I have to take note to not make this mistake in the future.   
```C
I fixed the other mistake and now the code is fully working.

#include <stdio.h>
int main(){

long charCounter;
int lineCounter, c;

charCounter = 0;
lineCounter = 0;

printf("\\n enter message : ");
while((c = getchar()) != EOF){
 if(c == '\\n'){
  lineCounter++;
 }
charCounter++;
}
printf("\\n\\nCharacters : %ld\\n", charCounter);
printf("Lines : %d\\n\\n", lineCounter);
}


```
I discovered that for all counter variables, if i plan to increment them, i must set them to a starting value/ initialise. if i do not, i end up with obscure negative numbers as a result(-9664834).
i should now be extremely careful to avoid pointer and initialisation errors in the future.   
### Word Counter   
Hmm, Im trying my best to understand but basically, the code is a skimmed version of the UNIX WordCounter program and uses an IN and OUT state to track if it is in a word or not. depending on that, it decides whether to count a word or not.   
```C

I actually got it faster than i thought.
#include <stdio.h>

#define IN 1 /check if inside a word/
#define OUT 0 /check if outside a word/

int main(){

long charCounter;
int lineCounter, c, wordCounter, state;

charCounter = 0;
lineCounter = 0;
wordCounter = 0;

state = OUT;
printf("\\n enter message : ");
while((c = getchar()) != EOF){
 if(c == '\\n'){
  lineCounter++;
 }
 charCounter++;
 if(c == ' '||c == '\\n'||c == '\\t'){
  state = OUT;
 }
 else if(state == OUT){
  state = IN;
  wordCounter++;
 }
}

printf("\\n\\nCharacters : %ld\\n", charCounter);
printf("Lines : %d\\n", lineCounter);
printf("Total Words : %d\\n\\n", wordCounter);

}


```
This code is completely running. the state detection system works like this. IF it detects whitespace characters like '\n',' ' or '\t', it will automatically know that it isn't in a word. but when it sees that there is no white space character where it is, it will then check to see if the state is out. then it will change it to In and increment wordCounter. after that, it will comeback and if it is still in a character that isn’t a whitespace character, it will find State = IN, and won't increment it until it finds another white space character to make it reset the word detection.   
Ok time to embark onto the next topic.   
### Arrays   
alright, I’ll do arrays then go sleep.   
Im not going to follow the C, 2nd edition book simply because its method will eave me confused i my goal is to achieve some mastery. Im gonna follow some youtube tutorials.   
Notes :
What is an array ?
In C, an array is a collection of similar kinds of data.   
Why arrays ?
They help in data storage because rather than making separate variables to store 100 people's names, we can store them in one data group.   
You can create arrays by
"dataType nameOfArray[arraySize];"   
You can also create them with it's content ;
"dataType nameOfArray[] = {1, 2, 3};"   
In this kind of declaring, you can also include intended size in the square brackets as long as it corresponds and allows the elements within to coexist.   
if you tried to make the array with more elements that it can handle, the terminal will return :
/**Users/joseph/Documents/Coding/code/C/testing/beginner09.c:5:30**:**warning**:**excess elements in array initialiser [-Wexcess-initializers**]   
char numbers[2] = {1, 2, 3};   
So i guess you gotta write the code correctly.
To add values to the arrays, you have to use "arrayName[index] = elements;" to set an index position to a certain value or element.   
For loops are often used to iterate through an array. A for loop is usually written in this format.
for(counter = startingIndx; condition for loop to run under; action done after(used to increment counter))
{ code to be iterated.}   
