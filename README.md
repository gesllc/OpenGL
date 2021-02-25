# OpenGL
Working repository for Lynda.com Course \'Up &amp; Running with OpenGL\'
---------------------------------------------------------------

### Also found stackoverflow recommendations for these tutorials  
`http://www.arcsynthesis.org/gltut/`  
`http://tomdalling.com/blog/category/modern-opengl/`  
`http://www.codeincodeblock.com/2013/07/modern-opengl-32-tutorial-series-with.html`  

### Steps for installing CMake (from Instructor\'s transcript)
- Get source code from `www.cmake.org/cmake/resources/software.html`  
- Download Unix/Linux Source file `cmake-3.20.0-rc1.tar.gz`  
- `mkdir ~/tmp`  
- `cd ~/tmp`  
- `mv ~/Downloads/cmake-xxx .`  
- `tar xvf cmake-xxx`  
- `cd cmake-xxx`  
- `./configure`  
- `gmake`  
- `su -`  
- `gmake install`  
- `exit`
- `which cmake` should show `/usr/local/bin/cmake`  

### After all the above, cmake was available and would run OK, but could not build the project.
- `cd ExerciseFiles`  
- `mkdir Project`  
- `cmake -G "Unix Makefiles" ..`  
- The command above failed with error messages: 
- Could not find a package configuration file provided by "Glew" with any of  
- the following names:
  
- GlewConfig.cmake  
- glew-config.cmake
  
- Add the installation prefix of "Glew" to CMAKE\_PREFIX\_PATH or set "Glew\_DIR"  
- to a directory containing of the above files...   
- However neither of those files exist in the ExerciseFiles directory structure.  

### Appears Glew was not installed (Attempted on CentOS 8S).
- From `glew.sourceforge.net/build.html` installed requirements.  
- As root, `yum install libXmu-devel libXi-devel libGL-devel dos2unix git wget`  
- Downloaded source into repositories directory:
- `git clone https://github.com/nigels-com/glew.git glew`  
- Then from instructions from github README.md:  
- `make extensions`  
- FAILED - Installed python, then still needed to create link
- `ln -s /usr/bin/python2.7 /usr/bin/python`  
- `make extensions`  
- `make`  
- As root, `make install`  

### Although the C8S steps above were promising, on Debian Buster followed instructions from Tom Dalling repo...
- `git clone https://github.com/tomdalling/opengl-series.git`  
- `su -`  
- `apt-get install libglm-dev libglew-dev libglfw3-dev`  
- `exit`  
- `cd platforms/linux`  
- `make`  
- `cd ../../`  
- `./source/01_project_skeleton/01_skeleton-debug`  
- The command above opened a basic openGL window




