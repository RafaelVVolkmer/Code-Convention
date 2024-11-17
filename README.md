# > 𝐂 𝐂𝐎𝐃𝐄 𝐂𝐎𝐍𝐕𝐄𝐍𝐓𝐈𝐎𝐍

𝑩𝒚: 𝑹𝒂𝒇𝒂𝒆𝒍 𝑽. 𝑽𝒐𝒍𝒌𝒎𝒆𝒓

This document refers to a proposed C coding convention developed by me, Rafael V. Volkmer, during my years of experience with the language. It exemplifies a series of best practices focused on facilitating code understanding for readers. I am not mandating this in an imperative way, saying that everyone should use this style because it's the best or anything like that, but rather presenting a standardized alternative that, for me and those who work with me, has been working very well.

I hope that, if it fits your style, you consider adopting all or some aspects of the pragmatic organization outlined in this document, as it is derived from practical experience in the job market with the language.

## > 𝐀𝐥𝐥𝐦𝐚𝐧 𝐂𝐨𝐝𝐞 𝐒𝐭𝐲𝐥𝐞

## > 𝐍𝐨𝐦𝐞𝐧𝐜𝐥𝐚𝐭𝐮𝐫𝐞
...
## 
### - 𝐃𝐞𝐟𝐢𝐧𝐞 𝐍𝐚𝐦𝐞𝐬

One of the most standard structures in the C language offers a powerful tool for processing attributes at compile time, making coding more dynamic and customizable for the user.

As a standard convention of the language, evidenced by the code present in the largest known repository of these implementations, the Linux Kernel, the convention is to define macros using all uppercase letters, categorized as SCREAMING CASE. Words are separated by "_", thus forming SCREAMING_SNAKE_CASE. This makes the structure more recognizable because when encountering something entirely in uppercase letters, it becomes clear that it is a standard immutable compile-time definition.

> 𝐄𝐱𝐚𝐦𝐩𝐥𝐞:
```
> Head:       SCREAMING_SNAKE_CASE
```

```c
#define ARRAY_SIZE (unsigned int)(100U)
```

Defines are extremely important and fundamental structures, protected by this convention. They must be strictly adhered to in all C code, regardless of whether the convention proposed in this document is followed or not.
## 
### - 𝐌𝐚𝐜𝐫𝐨 𝐍𝐚𝐦𝐞𝐬
```
> Head:       SCREAMING_SNAKE_CASE
> Variables:  snake_case
```

```c
#define DIVISION_OP(numerator_num, denominator_num) (float)( numerator_num / denominator_num)
```
## 
### - 𝐄𝐧𝐮𝐦 𝐍𝐚𝐦𝐞𝐬

```
> Head:       camelCase
> Values:     SCREAMING_SNAKE_CASE
```

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
...
## 
### - 𝐕𝐚𝐫𝐢𝐚𝐛𝐥𝐞 𝐍𝐚𝐦𝐞𝐬

```
> Head:       snake_case
```

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

```c
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

...

# > 𝐂𝐨𝐦𝐦𝐞𝐧𝐭𝐬

# > 𝐆𝐨𝐨𝐝 𝐂𝐨𝐝𝐢𝐧𝐠 𝐏𝐫𝐚𝐜𝐭𝐢𝐜𝐞𝐬 𝐢𝐧 𝐂
