# OSLab Project 

### 1- Install virtual machine
### 2- Build default kernel
### 3- Add "studentName()"
### 4- Add calculator to menu

<hr/>
<hr/>
<hr/>

## 1- Install virtual machine

- using lubuntu 16 iso, 1-GB RAM, 8-GB memory 

![fig](/screenshots/firstBuid/1-install.png)

![install](/screenshots/firstBuid/2-after-install.png)

- install git
```
$ sudo apt-get install git
```
![git](/screenshots/firstBuid/3-install-git.png)

- install toolchain
```
$ sudo add-apt-repository ppa:ops-class/os161-toolchain
$ sudo apt-get update
$ sudo apt-get install os161-toolchain
```

![toolchain](/screenshots/firstBuid/4-toolchain.png)
![toolchain](/screenshots/firstBuid/5-toolchain2.png)


- Creaete OSLab folder and clone repository
```
$ git clone https://github.com/Dodger23/os161 src
```
![toolchain](/screenshots/firstBuid/7-clone-os161.png)
![toolchain](/screenshots/firstBuid/8-after-clone.png)


</br>
<hr/>
<hr/>
<hr/>
</br>
</br>

## 2- Build defualt kernel

- Run configure file
![toolchain](/screenshots/firstBuid/9-configure.png)

- Go to kern/conf and configure DUMBVM
```
cd kern/conf
./config DUMBVM
```
![toolchain](/screenshots/firstBuid/10-.png)


- Go to DUMBVM and bmake
```
cd ../compile/DUMBVM
bmake depend
bmake
bmake install
```
!! NOTICE : BECAUSE THIS IS THE FIRST BUILD WE DON'T NEED TO RUN " bmake clean" !!

![fig](/screenshots/firstBuid/11-bmake-depend.png)
![fig](/screenshots/firstBuid/12-bmake.png)
![fig](/screenshots/firstBuid/13-bmake-install.png)


- To run the compiled kernel we go to root directory and run sys161 kernel</br>
!! NOTICE : DOWNLOAD "sys161.conf" IF THIS IS THE FIRST TIME !!
```
cd ~/root
sys161 kernel
```

![fig](/screenshots/firstBuid/14-Build.png)

</br>
<hr/>
<hr/>
<hr/>
</br>
</br>


## 3- Add "studentName()" 

- Go to os161/kern and make a new folder named "AAST" which will include our "studentName.c" file
- make new header file "AAST.h" and add our function in it
![fig](screenshots/secondBuild/2.png)


- make new C file "studentName.c"
- write function in "studentName.c" to print student name and ID 
- include header file "AAST.h"
- include header file "lib.h" to use "kprintf()" 
- include header file "types.h" to be able to use this file in main
![fig](/screenshots/secondBuild/1.png)


- Go to kern/conf.kern file to add our C file "studentName.c" path 
![fig](/screenshots/secondBuild/3.png)

- Go to main/main.c and add header file "AAST.h"
``` 
#include <AAST.h>
```
![fig](/screenshots/secondBuild/4.png)


- Notify th program that studentName() is an external function 
```
extern void studentName();
```
![fig](/screenshots/secondBuild/5.png)

- Call the studentName() function inside the boot function 
![fig](/screenshots/secondBuild/6.png)


- Recompile and build the kernel with same Build steps 
!! NOTICE : ADD "bmake clean" TO CLEAN PREVIOUS COMPILE FILES


- Go to ~/root and run sys161.conf to run 
```
cd ~/root
sys161 kernel
```

![fig](/screenshots/secondBuild/7.png) 


</br>
<hr/>
<hr/>
<hr/>
</br>
</br>


## 4- Add calculator to menu

- Add calculator function in studentName.c file 
- include the function definition in the header file "AAST.h"
![fig](/screenshots/Calculator/3.png)


- include header file "AAST.h" in the menue.c to be able to use the calculator function 
![fig](/screenshots/Calculator/1.png)

- Create new function "cmd_calculator" calls the our calculator function
![fig](/screenshots/Calculator/5.png)

- Add "[C] Calculator" to the menu options 
![fig](/screenshots/Calculator/6.png)


- Trigger the cmd_calculator() when choosing "C" from the menu
![fig](/screenshots/Calculator/4.png)


- Recompile and build the kernel with same Build steps</br>
!! NOTICE : ADD "bmake clean" TO CLEAN PREVIOUS COMPILE FILES

- Go to ~/root and run sys161.conf to run 
```
cd ~/root
sys161 kernel
```
![fig](/screenshots/Calculator/7.png)
![fig](/screenshots/Calculator/8.png)
![fig](/screenshots/Calculator/9.png)
![fig](/screenshots/Calculator/11.png)



 
