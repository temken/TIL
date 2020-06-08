# Fix the seed of a pseudo-random number generator

When using pseudo-random number generators like [this one](https://www.cplusplus.com/reference/random/mt19937/), I use a random seed.
```cpp
#include <random>

int main()
{
	std::random_device rd;
	std::mt19937 PRNG(rd());
	// ...
}
```

If I want to fix the seed, such that the generated pseudo-random numbers are the same everytime the code runs, I can fix it either by
```cpp
#include <random>

int main()
{
	const int fixed_seed = 1;
	std::mt19937 PRNG(fixed_seed);
	// ...
}
```
or
```cpp
#include <random>

int main()
{
	const int fixed_seed = 1;
	std::mt19937 PRNG;
	PRNG.seed(fixed_seed);
	// ...
}
```

This is particularly useful for debugging or writing unit tests of functions with random outputs.

## Source
[https://www.cplusplus.com/reference/random/mt19937/](https://www.cplusplus.com/reference/random/mt19937/)   
[https://stackoverflow.com/questions/25644465/fix-seed-globaly-in-c11-random](https://stackoverflow.com/questions/25644465/fix-seed-globaly-in-c11-random)
