Whether your project include with some unit testing, you can add to integrated test on gitlab ci.
This will automate to test your functional code before release on staging. 
Some note, this still ready support for python project such as microservice project. 

## Adding test for pre-served Makefile
Add this line below to your Makefile. 
Change `<project test folder>` with your unit testing folder. 

```
.PHONY: test

test:
	sudo apk add libxml2-dev libxslt-dev
	sudo pip3 install -r requirements.txt
	sudo pip3 install -r requirements-dev.txt
	pytest -vv -s <project test folder>
```

This will automate running your unit testing on gitlab-ci. 
Output can be viewed as terminal linux(tty) on browser when pipeline test started. 

