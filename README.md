C program to count the number of vowels in a string.
In this article we will learn a simple C program to count the number of vowels in a string.
‘A’, ‘E’, ‘I’, ‘O’, ‘U’ are five vowels out of 26 characters in English alphabet letters.C programming is case sensitive, and hence lowercase and uppercase characters are considered differently, so we will have to check for both the cases.

Program count the number of vowels
Methods discussed
Problem Statement – Write a program to calculate total number of vowels in a sentence

We are going to discuss to methods in this post –

Iterative Method
Recursive Method
Algorithm
Initialize the variable.
Accept the input.
Initialize for loop.
Check and count the vowels.
Terminate for loop.
Print total count.
Method 1 (Iterative)
Run
#include <stdio.h>
#include <ctype.h>
 
int main()
{
    // Initializing variable.
    char str[100];  
    int i, vowels = 0;
    
    // Accepting input.
    printf("Enter the string: ");
    // best way to read string rather than gets/fgets
    scanf("%[^\n]s",&str);
    
    //Initializing for loop. 
    for(i = 0; str[i]; i++)  
    {
        //Counting the vowels.
        if(str[i]=='a'|| str[i]=='e'||str[i]=='i'||
           str[i]=='o'|| str[i]=='u'||str[i]=='A'||
           str[i]=='E'||str[i]=='I'||str[i]=='O' ||str[i]=='U')
        {
            vowels++;
        }
    }
 	
    //Printing the count of vowels.
    printf("Total number of vowels: = %d\n",vowels);
    
    return 0;
}
Enter the string: I am human
Total number of vowels: = 4
Note
The time complexity of above code in O(n) as in the code we are looping over the string once.
Method 2 (Recursive)
This method uses recursion in C

Additionally, we have used another function to convert the character into the upper case so we do not have to write separate ‘OR’ conditions of lowercase characters

Run
#include <stdio.h>
#include <ctype.h>
#include <string.h>
// toupper function is available in ctype.h header file

// Function to check the Vowel
int isVowel(char ch) 
{
    ch = toupper(ch);
    return (ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U');
}

// to count total number of vowel from 0 to n
int countVowel(char str[], int n) 
{
    if (n == 1) 
        return isVowel(str[n - 1]);
    
    return countVowel(str, n - 1) + isVowel(str[n - 1]);
}

int main() {
    // string object
    char str[10] = "Hey Dude";
    
    int len = strlen(str);
    // Total numbers of Vowel
    printf("%d", countVowel(str, len));
    return 0;

}
Output
3
Note
The time complexity of above code is also O(N) as total n recursive calls are made. Where N is length of string
Related Pages
Juggling algorithm for array rotation

Balanced Parenthesis Problem

Remove brackets from an algebraic expression

Remove spaces from a string

Remove the vowels from a String

Method 3 (Using a Function)
Below is another way of counting vowels in a string using a function –

Run
// Count Vowels using a function
#include <stdio.h>
#include <ctype.h>
// toupper/tolower function is available in ctype.h header file

int isVowel(char ch)
{
    // reduce number of or cases of upper / lower cases 
    // by converting input char to lowercase or uppercase
    ch = tolower(ch);
    if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u')
        return 1;
   
   return 0;
}
int getVowelCount(char a[])
{
   int count = 0, i = 0;
   char ch;
   
   while (a[i] != '\0'){  
      ch = a[i];
      
      if (isVowel(ch))
         count++;
      i++;
   }
   return count;
}


int main()
{
   char str[100];

   printf("Enter a string\n");
   // best way to read string rather than gets/fgets
   scanf("%[^\n]s",&str);
    
   // gets(str); do not use this
   
   printf("Total Vowels: %d\n", getVowelCount(str));
   
   return 0;
}
Output
Enter a string
i am human
Total Vowels: 4
Method 4 (Program to count vowels, consonants, whitespaces, digits)
Run
#include <stdio.h>
#include <ctype.h>
// toupper/tolower function is available in ctype.h header file
int main() {

  char str[100];
  int vowels = 0, consonants = 0, digits = 0, whitespaces = 0, special = 0;

  // get full line of string input
  printf("Enter string: \n");
  fgets(str, sizeof(str), stdin);
  
  // can also use this instead of fgets
  // scanf("%[^\n]s",&str);

  // loop through each character of the string
  for (int i = 0; str[i] != '\0'; ++i) {

    // convert to uppercase
    str[i] = toupper(str[i]);

    // checking for a vowel
    if (str[i] == 'A' || str[i] == 'E' || str[i] == 'I' ||
        str[i] == 'O' || str[i] == 'U') {

      // increment value of vowels by 1
      vowels++;
    }

    // if its b/w A-Z and wasn't vowel then its a consonant
    else if ((str[i] >= 'A' && str[i] <= 'Z')) {
      consonants++;
    }

    // checking for a digit
    else if (str[i] >= '0' && str[i] <= '9') {
      digits++;
    }

    // checking for a whitespace
    else if (str[i] == ' ') {
      whitespaces++;
    }
  }

  printf("Total No. of Vowels: %d\n", vowels);
  printf("Total No. of Consonants: %d\n", consonants);
  printf("Total No. of Digits: %d\n", digits);
  printf("Total No. of White spaces: %d\n", whitespaces);

  return 0;
}
Output
Enter string: 
I am a human 1001
Total No. of Vowels: 5
Total No. of Consonants: 4
Total No. of Digits: 4
Total No. of White spaces: 4
