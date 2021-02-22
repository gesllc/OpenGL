

Hi, my name is Pablo Colapinto and welcome to Up and Running with OpenGL. In this course, we'll be learning how to render real time content using the OpenGL API,' the world's current standard for cross-platform graphics. I'll begin by showing you how to create a window context for our graphics using the GLFW library. Then we'll add some geometric primitives in this window using OpenGL's Legacy Immediate mode before moving on modern OpenGL programming.

Next we'll investigate how to generate 3D meshes by sending buffers of vertex data to the GPU, and how to manipulate our virtual scene using matrix transforms. Finally, we'll explore textures and lighting using the GLSL shading language, and add some basic interactivity using our keyboard and mouse. By the end of this course, you'll be up to speed with modern OpenGL, and the new advanced programmable Pipeline. Now let's get started with Up and Running with OpenGL.



OpenGL itself can be wrapped in a variety of languages and bindings exist in Python and Ruby for example. But for this course, we'll be programming in C++. So some familiarity with C or C++ would be helpful. A great course to get up to speed with C++ is Bill Wyman's C/C++ essential training. Graphics programming itself, because it involves negotiating with the GPU, and some mathematics. Can be a challenging subject. Patience will go a long way.

Beyond that, an open imagination is all you need to become an expert OpenGL programmer.

The exercise files folder includes everything you need to set up a working OpenGL environment. The examples folder has all of the .cpp source code that we use in this course. We're going to be using CMake to generate the actual Xcode project files or Visual Studio files if you're on Windows, from these .cpp files. Alternatively, you can also use the run.sh script if you're on a Unix-like system, feeding it the file path to the .cpp file.

So for instance, you could do ./run.sh examples/cube.cpp to compile and run that project. The GLFW folder contains a popular library for generating GL window contexts in a cross-platform manner. The GLM folder contains a popular mathematics library we'll be using for generating matrix transforms. The Include folder contains some encapsulated OpenGL functionality that we'll be going over throughout the course.

The Resources folder contains any assets that we'll be importing into our project, such as this flower bumpmap which we'll be using as a texture. Finally, in the Win folder, I've included the Windows-specific version of the GLU extension wrangler library. I've included GLU here for those of you buidling on Windows since knowing exactly where GLU is can be helpful. The CMake list files will also help CMake find the relevant include-paths, such as the exercise files path itself, the include folder and GLFW's include-path.

With these resources and examples, we have everything we need to get up and running with OpenGL.

On OS X, we're gonna wanna make sure we have Xcode installed. We can get Xcode for free from the Mac App Store. Xcode will install most of the tools we need for this course, except for CMake. We want to use CMake to help us in cross compiling our code and making sure that our project files are pointing to the right libraries. CMake is a great tool for writing code that will work across different platforms. I like building CMake from source, so on the CMake website, let's download the Unix/Linux Source tar files.

www.cmake.org/cmake/resources/software.html

Once they are downloaded, cd into the CMake file directory. Here we can type dot slash bootstrap && make && make install. Depending on your user permissions, you may need to write sudo make install. This will build, compile and install the CMake command line tools onto our OS platform. With CMake installed, we can cd into our exercise files folder.

Where we are gonna do here is use CMake to generate an Xcode project file that contains all the lessons for this course. Let's make an Xcode directory, cd into the Xcode directory and type cmake space dash capital G for generate space Xcode in quotes capital X lower-case c o d e space dot dot and hit return.

Cmake is now generating an Xcode project file for us that points to the correct libraries and include header files. If we look inside of our exercise files folder, we see our Xcode directory, and the Xcode project that CMake has generated for us. Let's open that. In our project hierarchy we have all the example files that we're going to be looking at throughout this course. We also have some of the demos that come included with GLFW, the windowing library.

To follow along with the lessons, open the folder that corresponds to the lesson name. In the Source Files directory, we'll find our dot cpp files that correspond to the current lesson. To compile all the current lesson, navigate to the list of targets, select the target and build that. My Xcode project will look a little different. The name of my Xcode project will be at the top of the screen, corresponding to the current lesson.

In the file hierarchy on the left-hand side of the screen, the name of the current lesson also corresponds with the name of the project. So in your Xcode project file, which includes all the lessons in one project file, just make sure that you are in the same folder as the name of the current lesson, and you should be able to follow along.








