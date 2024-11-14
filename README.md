# > 𝐂 𝐂𝐎𝐃𝐄 𝐂𝐎𝐍𝐕𝐄𝐍𝐓𝐈𝐎𝐍

𝑩𝒚: 𝑹𝒂𝒇𝒂𝒆𝒍 𝑽. 𝑽𝒐𝒍𝒌𝒎𝒆𝒓

## > 𝐀𝐥𝐥𝐦𝐚𝐧 𝐂𝐨𝐝𝐞 𝐒𝐭𝐲𝐥𝐞

## > 𝐍𝐨𝐦𝐞𝐧𝐜𝐥𝐚𝐭𝐮𝐫𝐞
...

### - 𝐃𝐞𝐟𝐢𝐧𝐞 𝐍𝐚𝐦𝐞𝐬

```
> Head:       SCREAMING_SNAKE_CASE
```

```c
#define ARRAY_SIZE (unsigned int)(100U)
```

### - 𝐌𝐚𝐜𝐫𝐨 𝐍𝐚𝐦𝐞𝐬
```
> Head:       SCREAMING_SNAKE_CASE
> Variables:  snake_case
```

```c
#define DIVISION_OP(numerator_num, denominator_num) (float)( numerator_num / denominator_num)
```

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

### - 𝐒𝐭𝐫𝐮𝐜𝐭𝐮𝐫𝐞 𝐍𝐚𝐦𝐞𝐬

```
> Head:       camelCase
> Instance:   snake_case
> Variables:  snake_case
```

```c
struct personData
{
    unsigned int person_age;
    char *person_name;
}

int main(int argc, char *argv[])
{
    struct personData my_person;

    return 0;
}
```
...

### - 𝐓𝐲𝐩𝐞𝐝𝐞𝐟 𝐍𝐚𝐦𝐞𝐬

```
> Head:       snake_case
> Postfix:     _t
> Variables:  snake_case
```

```c
typedef enum ageSteos
{
    CHILD_AGE,
    TEEN_AGE,
    ADULT_AGE,
    ELDER_AGE,
    INVALID_AGE
} age_steps_t;

typedef struct personData
{
    unsigned int age;
    age_steps_t life_step;

    char *name;
} person_t;

int main(int argc, char *argv[])
{
    person_t person;
    age_steps_t current_step;

    current_step = (person.age < 12u) ? CHILD_AGE :
                   ((person.age > 12u) && (person.age < 18u)) ? TEEN_AGE  :
                   ((person.age > 18u) && (person.age < 60u)) ? ADULT_AGE :
                   (person.age > 60u) ? ELDER_AGE : INVALID_AGE

    person.life_step = current_step;

    return 0;
}
```
...

### - 𝐕𝐚𝐫𝐢𝐚𝐛𝐥𝐞 𝐍𝐚𝐦𝐞𝐬

...

### - 𝐅𝐮𝐧𝐜𝐭𝐢𝐨𝐧 𝐍𝐚𝐦𝐞𝐬

...

## > 𝐂𝐨𝐦𝐦𝐞𝐧𝐭𝐬

# > 𝐆𝐨𝐨𝐝 𝐂𝐨𝐝𝐢𝐧𝐠 𝐏𝐫𝐚𝐜𝐭𝐢𝐜𝐞𝐬 𝐢𝐧 𝐂
