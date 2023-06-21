# Monty

This project is a simple interpreter for Monty ByteCodes. The interpreter reads a bytecode file and executes the bytecode commands.

## The Monty Language

Monty 0.98 is a scripting language that is first compiled into Monty byte codes, similar to Python. It utilizes a unique stack with specific instructions for manipulation.

## Monty Byte Code Files

Files containing Monty byte codes usually have the .m extension. Although the industry commonly uses this standard, it is not required by the language specification. Each line in the file contains only one instruction. The opcode and its argument can be preceded or followed by any number of spaces. Here are some examples:

```
push 0
push 1
push 2
push 3
pall
```

## Objectives

- Understand the concepts of LIFO and FIFO
- Understand the purpose and usage of stacks and queues
- Familiarize with common implementations of stacks and queues
- Identify common use cases for stacks and queues
- Learn the appropriate use of global variables

## Resources

- [Difference between Stack and Queue Data Structures](https://www.educative.io/edpresso/difference-between-stack-and-queue-data-structures)

## General Requirements

- Allowed editors: vi, vim, emacs
- All files are compiled on Ubuntu 20.04 LTS using gcc with the following options: -Wall -Werror -Wextra -pedantic -std=gnu89
- Each file must end with a new line
- There should be a README.md file at the root of the project
- Only one global variable is allowed
- Each file should contain no more than 5 functions
- The C standard library is allowed
- Function prototypes should be included in the header file monty.h
- All header files should be include guarded

## Data Structures

To complete this project, the following data structures should be used and included in the header file:

```c
/**
 * struct stack_s - doubly linked list representation of a stack (or queue)
 * @n: integer
 * @prev: points to the previous element of the stack (or queue)
 * @next: points to the next element of the stack (or queue)
 *
 * Description: doubly linked list node structure
 * for stack, queues, LIFO, FIFO
 */
typedef struct stack_s
{
        int n;
        struct stack_s *prev;
        struct stack_s *next;
} stack_t;

/**
 * struct instruction_s - opcode and its function
 * @opcode: the opcode
 * @f: function to handle the opcode
 *
 * Description: opcode and its function
 * for stack, queues, LIFO, FIFO
 */
typedef struct instruction_s
{
        char *opcode;
        void (*f)(stack_t **stack, unsigned int line_number);
} instruction_t;
```

## Files Description

S/N | Files | Description
--- | ----- | -----------
1   | bf    | TODO
2   | TODO  | TODO
3   | TODO  | TODO
4   | TODO  | TODO
5   | TODO  | TODO

## Compilation & Output

The codes can be compiled using the following command:

```
gcc -Wall -Werror -Wextra -pedantic -std=c89 *.c -o monty
```

The output should be printed on stdout, and any error messages should be printed on stderr.

## Examples

Example 1:

```bash
$ cat -e bytecodes/000.m
push 0$
push 1$
push 2$
push 3$
pall$
$ ./monty bytecodes/000.m
0
1
2
3
```

Monty byte

 code files can contain blank lines (empty or made of spaces only), and any additional text after the opcode or its required argument is not considered.

Example 2:

```bash
$ cat -e bytecodes/001.m
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$
$
push 2$
push 3$
pall$
$
$
$
push 4$
$
push 5$
push 6$
$
pall This is the end of our program. Monty is awesome!$
$ ./monty bytecodes/001.m
0
1
2
3
4
5
6
This is the end of our program. Monty is awesome!
```

Example 3:

```bash
$ cat -e bytecodes/00.m
push 1$
push 2$
push 3$
pall$
$ ./monty bytecodes/00.m
3
2
1
```

```bash
$ cat bytecodes/07.m
push 1
push 2
push 3
pall
pop
pall
pop
pall
pop
pall
$ ./monty bytecodes/07.m
3
2
1
2
1
1
```

```bash
$ cat bytecodes/09.m
push 1
push 2
push 3
pall
swap
pall
$ ./monty bytecodes/09.m
3
2
1
2
3
1
```