# Use syntax highlighting in Markdown

It is possible to use language-specific code syntax highlighting in markdown files.


Without syntax highlighting simply writing a code block like

```text
	```
	#include <iostream>

	int main()
	{
	   std::cout <<"I don't know much." <<std::endl;
	   return 0;
	}
	```
```
will result in

```
#include <iostream>

int main()
{
   std::cout <<"I don't know much." <<std::endl;
   return 0;
}
```

By simply adding the language to the first line,

```text
	```c++
	#include <iostream>

	int main()
	{
		std::cout <<"TIL how to use syntax highlighting."<<std::endl;

		return 1;
	}
	```
```

this code snippet will appear nicely highlighted.

```c++
#include <iostream>

int main()
{
	std::cout <<"TIL how to use syntax highlighting."<<std::endl;

	return 1;
}
```

A list of supported languages can be found in the linked source.

## Source

[https://support.codebasehq.com/articles/tips-tricks/syntax-highlighting-in-markdown](https://support.codebasehq.com/articles/tips-tricks/syntax-highlighting-in-markdown)