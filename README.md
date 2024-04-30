# strtoi_(base_)generic()

*Convert a string to a generic integer in C - the easy way!*

---

```C
static inline
int strtoi_generic(const char *str,
                   <integer-type> *res);
```

---

```C
static inline
int strtoi_base_generic(const char *str,
                        int base,
                        <integer-type> *res);
```

---

The main goal of this is to provide more easy to use and safer versions
for string to integer conversions in C. With a cleaner separation of return
values and error codes, without errno. In contrast to strto*() functions
these two function-look-alikes/macros here need less surrounding
wrapping/checks than strto*() functions. A single return value check is
enough to verify correct parsing.

Notably you can provide a pointer to any kind of integer type for result
storage - they will be able to check if the result would fit beforehand.

Yes, you heard right, generics in C!

Needs a modern C compiler for the C23 typeof() feature and the C11 _Generic()
feature.

## Example usage

Download the [strtoi_generic.h](strtoi_generic.h) and put it in the
same directory as this example (or your code):

```C
#include <stdio.h>
#include "strtoi_generic.h"

int main(int argc, char *argv[])
{
    char mystr[] = "123456789";
    long num;   // (un)signed char/short/int/long/long long/
                // (u)int{8/16/32/64}_t - whatever you want!
    int ret;

    ret = strtoi_generic(mystr, &num);
    if (ret < 0)
        printf("Error: %i\n", ret);
    else
        printf("OK, got: %li\n", num);

    return 0;
}
```

See [strtoi_generic.h](strtoi_generic.h) for a more detailed specification/documentation
of `strtoi_generic()` and `strtoi_base_generic()`.
