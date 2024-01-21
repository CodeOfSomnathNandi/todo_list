## Getting started

Every programming language has its own concept and approach to do basic things

## 1. Basic use of data types (Primitive types)

There are many primitive data types of different size. We have to learn which data type should I use for which value
For example 

```c
int main()
{
    int age; // We know that age can not greater than 128 for a human
    short age; // we can use short data type here 
    // TODO: check value range for short type
    return 0;
}
```

## 2. working with strings

Check all string functions for basic work like split a string, getting length of a string, getting char array to use for loop

## 3. learn memory concepts 

Check all memory related functions like malloc, realloc and calloc.

## 4. learn error handling 

Learn error handling for c language. Because error handling is required for building some error free apps

```c
#include <errno.h> 
#include <stdio.h> 

int main() 
{ 
	// If a file is opened which does not exist, 
	// then it will be an error and corresponding 
	// errno value will be set 
	FILE* fp; 

	// opening a file which does not exist 
	fp = fopen("GeeksForGeeks.txt", "r"); 

	printf("Value of errno: %d\n", errno); 

	return 0; 
}
```

For more information: https://www.geeksforgeeks.org/error-handling-in-c/


## 5. learning working with different file types

Most of the program is needed to save data in files. So learn file operations like file opening writing and reading.
1. Now learn about how to read, write binary files in c programming language. This type of operation is used for downloading files from internet. For more information: https://www.delftstack.com/howto/c/read-binary-file-in-c/
2. Now learn how to work with other file types like csv, xml and etc file types. This file types is needed for storing data in filesystem. For more information: https://www.geeksforgeeks.org/relational-database-from-csv-files-in-c/


## 6. learn from project

Best way for learn is making of projects. Projects are best for apply programming concepts 

1. Create a program for management employees in a company.Implement Adding employee and removing employee, changing salary, etc functions in this program.

## 7. learning threads in c langugage

Because today every languages uses threads for programms<br>
For more information: https://www.tutorialspoint.com/windows-thread-api-in-the-c-program<br>
For more information of thread.h: https://en.cppreference.com/w/c/thread
```c

#include<windows.h>
#include<stdio.h>
DWORD Sum;
/* data is shared by the thread(s) */
/* thread runs in this separate function */
DWORD WINAPI Summation(LPVOID Param){
   DWORD Upper = *(DWORD*)Param;
   for (DWORD i = 0; i <= Upper; i++)
   Sum += i;
   return 0;
}
int main(int argc, char *argv[]){
   DWORD ThreadId;
   HANDLE ThreadHandle;
   int Param;
   if (argc != 2){
      fprintf(stderr,"An integer parameter is required");
      return -1;
   }
   Param = atoi(argv[1]);
   if (Param < 0){
      fprintf(stderr,"An integer >= 0 is required");
      return -1;
   }
   /* create the thread */
   ThreadHandle = CreateThread( NULL, /* default security attributes */ 0, /* default stack size */    
   Summation, /* thread function */ &Param, /* parameter to thread function */ 0, /* default creation    flags */ &ThreadId);
   /* returns the thread identifier */
   if (ThreadHandle != NULL){
      /* now wait for the thread to finish */ WaitForSingleObject(ThreadHandle,INFINITE);
      /* close the thread handle */
      CloseHandle(ThreadHandle);
      printf("sum = %d",Sum);
   }
}
```

## 8. learning variable arguments

many of function takes variable arguments. For example

```c
int sum(int a, ...); // here ... is for variable arguments
```

This is a sample code 

```c
#include <stdio.h>
#include <stdarg.h>
 
void simple_printf(const char* fmt, ...)
{
    va_list args;
    va_start(args, fmt);
 
    while (*fmt != '\0') {
        if (*fmt == 'd') {
            int i = va_arg(args, int);
            printf("%d\n", i);
        } else if (*fmt == 'c') {
            // A 'char' variable will be promoted to 'int'
            // A character literal in C is already 'int' by itself
            int c = va_arg(args, int);
            printf("%c\n", c);
        } else if (*fmt == 'f') {
            double d = va_arg(args, double);
            printf("%f\n", d);
        }
        ++fmt;
    }
 
    va_end(args);
}
 
int main(void)
{
    simple_printf("dcff", 3, 'a', 1.999, 42.5); 
}
```

For more information: https://en.cppreference.com/w/c/variadic