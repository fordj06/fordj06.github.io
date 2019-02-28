---
published: true
---
# VHDL Style Requirements Automated Testing

[GitHub Repo](https://github.com/jeremiah-c-leary/vhdl-style-guide)

[Official Docs](https://vhdl-style-guide.readthedocs.io/en/latest/index.html)

### Introduction
VHDL Style Guide (VSG) provides coding style guide enforcement for VHDL code. Using VSG will ensure that all developers working on the VHDL portion of the project will meet the same VHDL style rules. The benefits of this are: 
- Improved readability 
- Simplified debugging 
- Facilitates more efficient and effective code review
  
The VSG project is an open source tool that will analyse a VHDL file and compare the code to a set of rules that are based off of the IEEE VHDL standard. These rules are fully configurable via JSON config files. You are also able to create your own rules using Python if required. 

---
### Installation
All methods of install require that you have Python already installed. If you need to install Python download the windows installer from [here](https://www.python.org/ftp/python/3.6.8/python-3.6.8-amd64.exe) then follow the installation wizard, ensuring that you add Python to PATH variables.

 The simplest installation method is to use pip. Pip is included with the Python install. In a command window enter the command. 

 ``` 
 pip install vsg
 ```

VSG should now be ready to use. To test the install, in a command prompt enter: 

```
vsg
```
You should see the following in response 

![Install test](https://i.postimg.cc/BnSRgV0J/term1.png "term1")

---
### Command Line Usage
Basic usage of vsg in the command line is very simple. To test a VHDL file for style violations simply change to the working directory which contains the file you wish to test using ```cd <directory_path>```.

![CL example](https://i.postimg.cc/8k7XHFXn/cd.png "cd")

Now that you are in the directory containing the file you wish to test simply enter ```vsg -f file_name.vhd```. You should get the following output

![alt text](https://i.postimg.cc/cCV80kf2/CLop.png "Logo Title")

The tool has multiple test phases and will not progress until all violations of the previous phase have been fixed. To automatically fix some of the violations you can use the command ```vsg -f file_name.vhd --fix```. This will fix a number of the violations, such as white space violations and variable case violations but cannot add labels or names. You will have to manually edit the file to make these changes.   

---
### Usage within ModelSim
Because its expected that you will have to manually edit the file it is useful that you can run the test from within ModelSim. To use vsg from within ModelSim simply open the project file you are currently working on and wish to test then in the Transcript window change the working directory to that of the project. A simple way to do this is to right click on the file path displayed at the top of the file viewer and copying the path. 

![modelsim](https://i.postimg.cc/pdvnZQgv/ms-cd.png "cd_ms")

You can then use the `cd` command in the Transcript window, followed by the path of the directory. If you have copied the label you must delete the file name, leaving just the folder path. 

![modelsim](https://i.postimg.cc/sXYBZMnX/ms-ls.png "cd_ls")

You can then us the `ls` command to observe the file contents. Note that the Transcript window is UNIX based so when entering in requires forward slash `/` separators rather than the back slashes `\` that are used on windows.  

In this example we will take a file which contains the VHDL of a 8 bit register. We will input a file that compiles and works but violates a number of style rules. We start with this file... 

![before](https://i.postimg.cc/jSCqjSk0/before.png "before")

To analyse the file for violations simply enter `vsg -f file_name.vhd` into the transcript window.  

![-f](https://i.postimg.cc/XYpyRZXG/find.png "find violations")

To make corrections either edit the file manually or use the command `vsg -f file_name.vhd --fix` into the transcript window. 

![fix](https://i.postimg.cc/9FJcGJmZ/fix.png "fix")

Because all of the violations in the example were white space and case related the tool is able to fix them all. If we now compare the VHDL file we can compare with the original file.

![after](https://i.postimg.cc/0NfVH9Pj/after.png "after")

For violations that cannot be fixed by the tool you can get examples of the required fixed from the online documentation, located [here](https://vhdl-style-guide.readthedocs.io/en/latest/rules.html).

---
### Custom Configuration

*TO FOLLOW*
