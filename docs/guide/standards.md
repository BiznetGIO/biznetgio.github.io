# Developer Standard

---

## Style Guide

Software engineers must use these conventions to make the code more secure also more readable by another engineer: 

1. For code style, use the standard such as: 
	1. Python 
		* [PEP-0257](https://www.python.org/dev/peps/pep-0257/) - python officially recommends to follow the high-level docstring conventions. This describes how the classes, functions, and codes should be documented and how this really helps for code readability.  
		* [PEP-3101](https://www.python.org/dev/peps/pep-3101/) - This is the new system for built-in string formatting operations, intended as a replacement for the existing ‘%’ string formatting operator. 
		* [PEP-0008](https://www.python.org/dev/peps/pep-0008/) - python coding style guidelines which strongly recommend naming conventions, comments, formatting and lot more... 
		* [GPSG](https://google.github.io/styleguide/pyguide.html) - Google Python Style Guideline talks about do’s and don'ts for python programs and it explains technically with proof and concepts. 
		* [Python Anti-Patterns](https://docs.quantifiedcode.com/python-anti-patterns/) - provides anti-pattern with a technical explanation of best practices and it covers anti-pattern for Django framework also. 
		* Reference : [The Hitchhikers Guide to Python - the book written by Kenneth and Tany](https://docs.python-guide.org/#writing-great-python-code), this book covers lots of recommended best practices from the section called Writing Great Python Code. will use PEP-8 
	2. PHP will use PSR-0, PSR-1 or PSR-2 

3. Meaningless / ambiguous variable name should not be used. 
4. Default language for any messages such as comments, warning, error, etc. will be using English and not using Bahasa Indonesia 

## Commit Message Guide

We use the pattern bellow for commit message:

``` bash
Add: <your commit message>
Update: <your commit message>
Remove: <your commit message>
Fix: <your commit message>
```

- `Add`: for feature additions.
- `Update`: for feature update.
- `Remove`: for feature dropping, etc.
- `Fix`: for bug fixing, style, etc.


## Comments  
For every code and function, there must be a comment. Refer to PEP-8, the comment must: 

 * Complete sentence, its first word should be capitalized, unless it is an identifier that begins with a lower case letter 
 * If a comment is short, the period at the end can be omitted 
 * Use two spaces after a sentence-ending period 
 * Use English 