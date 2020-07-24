## Intialize Project with BGN Developer Tools

Tools support on Unix/Linux system or Debian and Redhat with all derivatives. 
Just going simple, after clone monorepo project from biznet gitlab type :

```bash
   ./bgn-dev init
```

Give an access as root permissions when command prompt sudo appear.

When initialize already done, you dont need to initialize again.   

!!! note
	If you use Windows 10 as your operating system, you can use WSL/WSL2 to run it. 
	But some feature may not working perfectly(WSL under development).  

## Run Sample Project

Try run some existing project to ensure tools already installed and running.

Example : 
Deploy `rdap` project on local development with command
```bash
   ./bgn-dev project deploy rdap
```
Check running process
```bash
   ./bgn-dev project ps rdap
```
<p align="center">
    <img src="../img/bgndev-rdap-localdeploy.gif">
</p>

## Play to Next Step 
Tools packed with a bunch usefull command instructions , type help to see this.

```bash
   ./bgn-dev help
```
or 


```bash
   ./bgn-dev
```
<p align="center">
    <img src="../img/bgndev-help.png">
</p>


