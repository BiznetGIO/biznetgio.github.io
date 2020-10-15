Integrations test is internal procedural check component or functional based on an analysis of product.
White box testing will do in this step. 
Whether your project include with unit testing, you can add to integrated test on gitlab ci.
This will automate to test your functional code before release on staging. 
Some note, it still ready support for python project such as microservice project. 

## Adding test for pre-served Makefile
Add this line below to your Makefile. 

```bash
.PHONY: test

test:
	sudo apk add libxml2-dev libxslt-dev
	sudo pip3 install -r requirements.txt
	sudo pip3 install -r requirements-dev.txt
	pytest -vv -s <project_test_folder>
```
Change `<project_test_folder>` with your unit testing folder. 


## Example Project Contain Unit Testing 
Here explain a python project ready support execute integrated tools on ci/cd.  
<p align="center">
    <img src="../img/giov2-api-test-folder
.png">
<br>
<span>figure 1 : example a unit testing</span> 
</p>


<p align="center">
    <img src="../img/giov2-api-makefile.png">
<br>
<span>figure 2 : Makefile file</span>
</p>

Output can be viewed as terminal linux(tty) on browser when pipeline test started. 

<p align="center">
    <img src="../img/giov2-api-integrated-test.png">
</br>
<span>figure 3 : automated test running on ci/cd</span>
</p>

