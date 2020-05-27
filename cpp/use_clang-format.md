# Automatically format c++ code using custom rules with *clang-format*

[Clang-format](https://clang.llvm.org/docs/ClangFormat.html) is a great tool to auto-format your c++ code, which can be embedded in all kinds of IDEs and editors.

## Installation on Mac

The easiest way is to use [homebrew](https://brew.sh/):

```bash
brew install clang-format
```

## Usage

You can run *clang-format* on e.g. all ```*.cpp``` files via
```bash
clang-format -i *cpp
```
The ```-i``` option will perform the changes and save the files.  

By default, it will look for a style file called ```.clang-format``` defining the code style. Otherwise, it will use some default style.

A list of all style options can be found under [this link](https://clang.llvm.org/docs/ClangFormatStyleOptions.html).

## My setup

My personal *clang-format* set up is defined inside a ```.clang-format``` file.
```bash
Language: Cpp
AccessModifierOffset: -2
AlignAfterOpenBracket: true
AlignConsecutiveAssignments: true
AllowShortFunctionsOnASingleLine: Inline
AllowShortIfStatementsOnASingleLine: Never
AllowShortLambdasOnASingleLine: Inline
BreakBeforeBraces: Custom
BraceWrapping:
   AfterCaseLabel: true
   AfterClass: true
   AfterControlStatement: Always
   AfterEnum: true
   AfterFunction: true
   AfterNamespace: true
   AfterStruct: true
   AfterUnion: true
   AfterExternBlock: true
   BeforeCatch: true
   BeforeElse: true
#   BeforeLambdaBody: true
#   BeforeWhile: true
   IndentBraces: false
   SplitEmptyFunction: true
   SplitEmptyRecord: true
   SplitEmptyNamespace: true
BreakConstructorInitializers: BeforeColon
ColumnLimit: 0
ConstructorInitializerIndentWidth: 0
ContinuationIndentWidth: 4
FixNamespaceComments: true
IncludeBlocks: Preserve
IndentCaseLabels: true
IndentWidth: 4
PointerAlignment: Left
SortIncludes: true
SortUsingDeclarations: true
SpaceAfterCStyleCast: true
SpaceBeforeCpp11BracedList: true
SpaceBeforeParens: Never
SpacesBeforeTrailingComments: 3
TabWidth: 4
UseTab: Always
```

(The two commented options are only supported in version 11, which is not released yet.)  

## Example
With this set up, *clang-format* will re-format this code
```cpp
#include <functional>
#include <cmath>

#include <string>
#include <iostream>
#include <vector>

using namespace std;

// Functions
namespace ns
{
class test
{
private:
double s;

public:
test(double t){s=t;}}
}

double func(double x,int y,std::string st)
{
for(int i=0;i<3;i++) cout<<i<<endl;
return x*y;
}

void func(){}

int main(){
auto func=[](double x) {return x;};
int variable_1=4;
int r=3;
std::vector<double>a={1,2,3,4};
std::vector<double>{1,2,3,4};
if(true) cout << "Shit format" << endl;	 // blabla comment
func(2);							 // bla comment

if(true){cout << "true" << endl;}
else if(true){cout << "true" << endl;}
else cout << "damn" << endl;
switch(fool){
case 1:
	bar();
	break;
default:
	plop();
}
}
```
into this nicely formatted version:
```cpp
#include <cmath>
#include <functional>

#include <iostream>
#include <string>
#include <vector>

using namespace std;

// Functions
namespace ns
{
class test
{
  private:
	double s;

  public:
	test(double t)
	{
		s = t;
	}
}
}	// namespace ns

double func(double x, int y, std::string st)
{
	for(int i = 0; i < 3; i++)
		cout << i << endl;
	return x * y;
}

void func()
{
}

int main()
{
	auto func = [](double x) {
		return x;
	};
	int variable_1		  = 4;
	int r				  = 3;
	std::vector<double> a = {1, 2, 3, 4};
	std::vector<double> {1, 2, 3, 4};
	if(true)
		cout << "Shit format" << endl;	 // blabla comment
	func(2);							 // bla comment

	if(true)
	{
		cout << "true" << endl;
	}
	else if(true)
	{
		cout << "true" << endl;
	}
	else
		cout << "damn" << endl;

	switch(fool)
	{
		case 1:
			bar();
			break;
		default:
			plop();
	}
}

```

## Setup with *Sublime Text 3*

There is a Sublime Text package for *clang-format* called [Clang Format](https://packagecontrol.io/packages/Clang%20Format).

This package can format the code directly in the editor, either using a ```.clang-format``` file or a custom style defined in the package settings.

The package settings file ```clang_format_custom.sublime-settings```, which can be reached via **Sublime Text -> Preferences -> Package Settings -> Clang Format -> Custom Style - User**, looks a bit different from the previous ```.clang-format``` file format:

```bash
{
   "Language": "Cpp",
   "AccessModifierOffset": -2,
   "AlignAfterOpenBracket": true,
   "AlignConsecutiveAssignments": true,
   "AllowShortFunctionsOnASingleLine": "Inline",
   "AllowShortIfStatementsOnASingleLine": "Never",
   "AllowShortLambdasOnASingleLine": "Inline",
   "BreakBeforeBraces": "Custom",
   "BraceWrapping":{
      "AfterCaseLabel": true,
      "AfterClass": true,
      "AfterControlStatement": "Always",
      "AfterEnum": true,
      "AfterFunction": true,
      "AfterNamespace": true,
      "AfterStruct": true,
      "AfterUnion": true,
      "AfterExternBlock": true,
      "BeforeCatch": true,
      "BeforeElse": true,
      // "BeforeLambdaBody": true,
      // "BeforeWhile": true,
      "IndentBraces": false,
      "SplitEmptyFunction": true,
      "SplitEmptyRecord": true,
      "SplitEmptyNamespace": true,
   },
   "BreakConstructorInitializers": "BeforeColon",
   "ColumnLimit": 0,
   "ConstructorInitializerIndentWidth": 0,
   "ContinuationIndentWidth": 4,
   "FixNamespaceComments": true,
   "IncludeBlocks": "Preserve",
   "IndentCaseLabels": true,
   "IndentWidth": 4,
   "PointerAlignment": "Left",
   "SortIncludes": true,
   "SortUsingDeclarations": true,
   "SpaceAfterCStyleCast": true,
   "SpaceBeforeCpp11BracedList": true,
   "SpaceBeforeParens": "Never",
   "SpacesBeforeTrailingComments": 3,
   "TabWidth": 4,
   "UseTab": "Always",
}
```

In the general package settings **Sublime Text -> Preferences -> Package Settings -> Clang Format -> Settings - User**, you can deactivate the option
```bash
	"format_on_save": true
```
Then, *clang-format* will run on any file everytime it is saved.

## Sources
[Research Software Hour 005](https://researchsoftwarehour.github.io/2020/05/26/rsh-005.html)

[(link to video)](https://youtu.be/WIYaXzXLLY4?t=2940)

[https://clang.llvm.org/docs/ClangFormat.html](https://clang.llvm.org/docs/ClangFormat.html)  
[https://clang.llvm.org/docs/ClangFormatStyleOptions.html](https://clang.llvm.org/docs/ClangFormatStyleOptions.html)  
[https://packagecontrol.io/packages/Clang%20Format](https://packagecontrol.io/packages/Clang%20Format)  