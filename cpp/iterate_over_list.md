# Iterate over a list with a ```for``` loop

It is possible in python to simply iterate over the entries of a list.
```python
for thing in things:
	do_something(thing)
	# ...
```

What I did so far in ```C++``` to do the same was the (more involved) *old-school* for-loop.
```cpp
for(unsigned int i = 0; i < things.size(); i++)
{
	do_something(things[i]);
	// ...
}
```

However, I learned that, starting with *c++11*, it is also possible to directly iterate over the list/vector without using an index. 

```cpp
for(auto thing : things)
{
	do_something(thing);
	// ...
}
```
This is closer to the ```python``` for loop, despite a less intuitive syntax.

## 3 ways to access the list entry

1. Access by value. (see previous example)
	- ```thing``` is a **copy** of the list/vector entry
	- therefore, changes to ```thing``` do not affect the list/vector ```things```

2. Access by reference.
	- ```thing``` refers to the actual list/vector entry
	- no copy is created
	- therefore, changes to ```thing``` will change the list/vector ```things```
```cpp
for(auto& thing : things)
{
	do_something(thing);
	// ...
}
```

3. Access by constant reference.
	- ```thing``` refers to the actual list/vector entry
	- no copy is created
	- it is not possible to change ```thing```
```cpp
for(const auto& thing : things)
{
	do_something(thing);
	// ...
}
```

## Source
[https://en.cppreference.com/w/cpp/language/range-for](https://en.cppreference.com/w/cpp/language/range-for)   
[https://stackoverflow.com/questions/15176104/c11-range-based-loop-get-item-by-value-or-reference-to-const](https://stackoverflow.com/questions/15176104/c11-range-based-loop-get-item-by-value-or-reference-to-const)