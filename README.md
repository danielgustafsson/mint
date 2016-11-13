# Mint Unit

A minimal unit testing framework for C code.  Mint Unit has a TAP like output
syntax, but unlike TAP implementations it stops on the first failing test
following the fail-fast fail-hard idea of being forced to fix tests rather than
observe broken ones. This code was influenced by a minimal test framework
published in [Jera Tech Notes](http://www.jera.com/techinfo/jtns/jtn002.html).

## Usage

To use Mint Unit, include `mintunit.h` header file in your testing application
and start writing tests. Sample usage of mint unit can be seen below:

```C
#include <stdio.h>
#include "mintunit.h"

static char *
test_foo(void)
{
	 mt_assert("Test foo function", foo(5) == 5);
	 mt_is_null("Test bar function returns NULL", bar(5));
	 return NULL;
}

static char *
run_tests(void)
{
	mt_init(1);
	mt_run_test("Testing foo", test_foo);
	return NULL;
}

int
main(int argc, char **argv)
{
	char *test_result = run_tests();
	if (!test_result)
		printf("\n# All tests passed\n");
	printf("# Test Suites run: %d\n# Unit Tests run : %d\n", tests_run, units_run);

	return test_result == NULL ? 0 : 1;
}
```

## License

Mint Unit is licensed under the MIT license.
