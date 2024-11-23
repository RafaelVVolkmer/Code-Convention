# > 𝐂 𝐂𝐎𝐃𝐄 𝐂𝐎𝐍𝐕𝐄𝐍𝐓𝐈𝐎𝐍

𝑩𝒚: 𝑹𝒂𝒇𝒂𝒆𝒍 𝑽. 𝑽𝒐𝒍𝒌𝒎𝒆𝒓

This document refers to a proposed C coding convention developed by me, Rafael V. Volkmer, during my years of experience with the language. It exemplifies a series of best practices focused on facilitating code understanding for readers. I am not mandating this in an imperative way, saying that everyone should use this style because it's the best or anything like that, but rather presenting a standardized alternative that, for me and those who work with me, has been working very well.

I hope that, if it fits your style, you consider adopting all or some aspects of the pragmatic organization outlined in this document, as it is derived from practical experience in the job market with the language.

[Simple RPN Calculator Project That Uses This Convention](https://github.com/RafaelVVolkmer/RPN-Calculator)

## > 𝐀𝐥𝐥𝐦𝐚𝐧 𝐂𝐨𝐝𝐞 𝐒𝐭𝐲𝐥𝐞

The Allman style, also known as BSD indent style, is characterized by placing braces on their own lines. This style enhances readability by clearly delineating code blocks, making it easier to identify the beginning and end of structures such as functions, loops, and conditionals.

> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:
```c
int main(void)
{
    if (condition)
    {
        // Code block
    }
    else
    {
        // Code block
    }

    return 0;
}
```

# > 𝐌𝐨𝐝𝐮𝐥𝐞𝐬

The structure of a C codebase should always be kept modularized, meaning it should be separated into code sets that encompass the handling of specific functionalities. These modules should then be included in the main file to generate the binary. Thus, the .h and .c structures are used as follows:

```
Header file (.h) -> Prototypes of public functions and structures.
```

```
Source file (.c) -> Implementation of the logic for private functions and structures.
```

> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:

We have a calculator in C:

```
Calculator (module) -> calculator.h / calculator.c
```

- In header file (calculator.h):
```c
typedef enum calculatorOps
{
    CALCULATOR_ADD,
    CALCULATOR_SUB,
    CALCULATOR_MUL,
    CALCULATOR_DIV
} calculator_ops_t;

int Calculator_makeOperation(int num_a, int num_b, calculator_ops_t operation);
```

- In source file (calculator.c):
```c
#include "calculator.h"

int Calculator_makeOperation(int num_a, int num_b, calculator_ops_t operation)
{
    int result = 0u;

    result = (operation == CALCULATOR_ADD) ? (int)(num_a + num_b) :
             (operation == CALCULATOR_SUB) ? (int)(num_a - num_b) :
             (operation == CALCULATOR_MUL) ? (int)(num_a * num_b) :
             (operation == CALCULATOR_DIV) ? (int)(num_a / num_b) : 0u;

    return result;
};
```

# > 𝐍𝐨𝐦𝐞𝐧𝐜𝐥𝐚𝐭𝐮𝐫𝐞

Naming in C is an extremely important aspect. It is always necessary to maintain standardized names, with a clean architecture, following the same flow throughout the code, differentiating the types of structures present. Names should always be designed to facilitate the reader's understanding, making them more palatable. Thus, the convention follows the following terms:

## 
### - 𝐃𝐞𝐟𝐢𝐧𝐞 𝐍𝐚𝐦𝐞𝐬
```
> Head:       SCREAMING_SNAKE_CASE
```
> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:
```c
#define ARRAY_SIZE (unsigned int)(100U)
```
## 
### - 𝐌𝐚𝐜𝐫𝐨 𝐍𝐚𝐦𝐞𝐬
```
> Head:       SCREAMING_SNAKE_CASE
> Variables:  snake_case
```
> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:
```c
#define DIVISION_OP(numerator_num, denominator_num) (float)( numerator_num / denominator_num)
```
## 
### - 𝐄𝐧𝐮𝐦 𝐍𝐚𝐦𝐞𝐬

```
> Head:       camelCase
> Values:     SCREAMING_SNAKE_CASE
```
> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:
```c
enum enumerationValues
{
    FIRST_VALUE,
    SECOND_VALUE
};
```
## 
### - 𝐒𝐭𝐫𝐮𝐜𝐭𝐮𝐫𝐞 𝐍𝐚𝐦𝐞𝐬

```
> Head:       camelCase
> Instance:   snake_case
> Variables:  snake_case
```
> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:
```c
struct personData
{
    unsigned int     person_age;
    char             *person_name;
}

int main(int argc, char *argv[])
{
    struct personData my_person;

    return 0;
}
```
## 
### - 𝐓𝐲𝐩𝐞𝐝𝐞𝐟 𝐍𝐚𝐦𝐞𝐬

```
> Head:       snake_case
> Postfix:     _t
> Variables:  snake_case
```
> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:
```c
typedef enum ageSteps
{
    CHILD_AGE,
    TEEN_AGE,
    ADULT_AGE,
    ELDER_AGE,
    INVALID_AGE
} age_steps_t;

typedef struct personData
{
    unsigned int    age;
    age_steps_t     life_step;

    char *name;
} person_t;
```
## 
### - 𝐕𝐚𝐫𝐢𝐚𝐛𝐥𝐞 𝐍𝐚𝐦𝐞𝐬

```
> Head:       snake_case
```
> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:
```c
int main (void)
{
    int num_one = 1u;
    int num_two = 2u;

    return 0;
}
```
## 
### - 𝐅𝐮𝐧𝐜𝐭𝐢𝐨𝐧 𝐍𝐚𝐦𝐞𝐬
```
> Prefix:     CamelCase_ (module name)
> Head:       camelCase
> Params:     snake_case
```
> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:
```c
double Calculator_factorialCalculate(unsigned int base_number);

double Calculator_factorialCalculate(unsigned int base_number) 
{
    double ret = 0u;

    if (base_number == 0u || base_number == 1u)
    {
        ret = 1.0;
        goto end_of_function;
    }

    ret = (base_number * RPNCalculator_factorialCalculate(base_number - 1u));

end_of_function:
    return ret;
}
```

# > 𝐂𝐨𝐦𝐦𝐞𝐧𝐭𝐬

## 
### - 𝐇𝐞𝐚𝐝𝐞𝐫 𝐟𝐨𝐫 𝐡𝐞𝐚𝐝𝐞𝐫 𝐟𝐢𝐥𝐞𝐬
```c
 /** ============================================================================
    @addtogroup StackOperation
    @addtogroup StackOperation stack_ops

    @package    stack_ops
    @brief      This module provides functionalities for stack operations,
                including managing operator and value stacks for an RPN calculator.

    @file       stackops.h

    @author     Rafael V. Volkmer (rafael.v.volkmer@gmail.com)
    @date       16.11.2024
 
    @details    The Stack Operations module manages operator and value stacks used 
                in a Reverse Polish Notation (RPN) calculator. 
                It provides functionalities to push and pop operators and numerical 
                values, check stack states, and peek at the top elements without 
                odifying the stacks.
     
    @note       - Ensure that the stacks are properly initialized before 
                  performing any push or pop operations.
                - The module is designed for single-threaded environments. 
                  For multi-threaded applications, synchronization mechanisms 
                  should be implemented to ensure thread safety.
 =========================================================================== **/
 ```

## 
### - 𝐇𝐞𝐚𝐝𝐞𝐫 𝐟𝐨𝐫 𝐬𝐨𝐮𝐫𝐜𝐞 𝐟𝐢𝐥𝐞𝐬
```c
 /** ===========================================================================
    @ingroup    StackOperation
    @addtogroup StackOperation stack_ops

    @package    stack_ops
    @brief      This module provides functionalities for stack operations,
                including managing operator and value stacks for an RPN 
                calculator.

    @file       stackops.c
    @headerfile stackops.h

    @author     Rafael V. Volkmer (rafael.v.volkmer@gmail.com)
    @date       16.11.2024
 
    @details    The Stack Operations module manages operator and value stacks 
                used in a Reverse Polish Notation (RPN) calculator. 
                It provides functionalities to push and pop operators and 
                numerical values, check stack states, and peek at the top 
                elements without odifying the stacks.
     
    @note       - Ensure that the stacks are properly initialized before 
                  performing any push or pop operations.
                - The module is designed for single-threaded environments. 
                  For multi-threaded applications, synchronization mechanisms 
                  should be implemented to ensure thread safety.
 =========================================================================== **/
```

## 
### - 𝐒𝐞𝐜𝐭𝐢𝐨𝐧𝐬
```c
/* ==================================== *\
 *             INCLUDED FILE            *
\* ==================================== */

/*< Dependencies >*/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>

/*< Implements >*/
#include <stackops.h>
```

## 
### - 𝐌𝐚𝐜𝐫𝐨𝐬 𝐚𝐧𝐝 𝐃𝐞𝐟𝐢𝐧𝐞𝐬
```c
/** ====================================
  @def      FUNCTION_SUCCESS
  @package  stack_ops
  @brief    Indicates successful function 
            execution.
     
  @details  Represents a successful 
            operation, typically with 
            a value of 0.
 ==================================== **/ 
#define FUNCTION_SUCCESS    (unsigned int)(0U)
```

## 
### - 𝐄𝐧𝐮𝐦𝐬
```c
/** ============================================================================
  @enum     operatorIndex
  @package  RPN_calculator

  @typedef  operator_index_t

  @brief    Defines indices for operators.

  @details  Enumerates the indices corresponding to supported operators,
            used for operator identification and lookup.
 =========================================================================== **/
typedef enum operatorIndex
{
    OP_ADD,    /*< Addition operator '+'           >*/
    OP_SUB,    /*< Subtraction operator '-'        >*/
    OP_MUL,    /*< Multiplication operator '*'     >*/
    OP_DIV,    /*< Division operator '/'           >*/
    OP_POW,    /*< Exponentiation operator '^'     >*/
    OP_FACT,   /*< Factorial operator '!'          >*/
    OP_COUNT   /*< Total number of operators       >*/
} operator_index_t;
```

## 
### - 𝐒𝐭𝐫𝐮𝐜𝐭𝐬
```c
/** ============================================================================
  @struct   stack_val_t
  @package  stack_ops

  @typedef  stack_val_t

  @brief    Represents the value stack structure.

  @details  Contains an array to store numerical values and an integer to keep 
            track of the top index of the stack.
============================================================================ **/
typedef struct 
{
    double  data[MAX_STACK_SIZE];   /*< Array to store numerical values         >*/
    int     top;                    /*< Index of the top element in the stack   >*/
} stack_val_t;
```

## 
### - 𝐆𝐥𝐨𝐛𝐚𝐥 𝐯𝐚𝐫𝐢𝐚𝐛𝐥𝐞𝐬
```c
/** ============================================================================
  @var      operators_str
  @package  RPN_calculator

  @brief    Array of strings representing operator symbols.

  @details  Maps operator indices defined in `operator_index_t` to their
            corresponding string representations. This array is used for
            operator identification and processing in expression parsing and
            evaluation.
 =========================================================================== **/
const char* operators_str[OP_COUNT] =
{
    [OP_ADD]  = "+",
    [OP_SUB]  = "-",
    [OP_MUL]  = "*",
    [OP_DIV]  = "/",
    [OP_POW]  = "^",
    [OP_FACT] = "!"
};
```

## 
### - 𝐅𝐮𝐧𝐜𝐭𝐢𝐨𝐧𝐬 𝐚𝐧𝐝 𝐩𝐫𝐨𝐭𝐨𝐭𝐲𝐩𝐞𝐬
```c
/** ============================================================================
  @fn       RPNCalculator_applyOperation
  @package  RPN_calculator

  @brief    Applies an arithmetic operation to two operands.

  @details  Determines the operation to perform based on the operator token and
            applies it to the provided operands. Supports addition, subtraction,
            multiplication, division, and exponentiation.

  @param    operation    [in]:  String representing the operator.
  @param    num_a        [in]:  The first operand.
  @param    num_b        [in]:  The second operand.

  @return   The result of the operation as a double.
            Returns - EINVAL if the operation is invalid
            (e.g., division by zero).
 =========================================================================== **/
double RPNCalculator_applyOperation(const char* operation, double num_a, double num_b) 
{
    /*< Variable Declarations >*/
    double ret = FUNCTION_SUCCESS; /*< Return Control >*/

    int operation_index = 0u;

    /*< Security Checks >*/
    if(operation == NULL)
    {
        ret = -(ENOMEM);
        goto end_of_function;
    }

    /*< Assign Initial Values >*/
    operation_index = RPNCalculator_whichOperator(operation);

    /*< Start Function Algorithm >*/
    ret = (operation_index == OP_ADD)                  ? (num_a + num_b)   :
          (operation_index == OP_SUB)                  ? (num_a - num_b)   :
          (operation_index == OP_MUL)                  ? (num_a * num_b)   :
          (operation_index == OP_DIV && num_b != 0u)   ? (num_a / num_b)   :
          (operation_index == OP_POW)                  ? pow(num_a, num_b) : -(EINVAL);

    /*< Function Output >*/
end_of_function:
    return ret;
}
```

## 
### - 𝐄𝐧𝐝 𝐨𝐟 𝐟𝐢𝐥𝐞
```c
/*< end of file >*/
```
