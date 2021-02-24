
OpenGL Up & Running Course Instructor's Dialog
==============================================

Introduction
------------

**Welcome**

Hi, my name is Pablo Colapinto and welcome to Up and Running with OpenGL. In this course, we'll be learning how to render real time content using the OpenGL API,' the world's current standard for cross-platform graphics. I'll begin by showing you how to create a window context for our graphics using the GLFW library. Then we'll add some geometric primitives in this window using OpenGL's Legacy Immediate mode before moving on modern OpenGL programming.

Next we'll investigate how to generate 3D meshes by sending buffers of vertex data to the GPU, and how to manipulate our virtual scene using matrix transforms. Finally, we'll explore textures and lighting using the GLSL shading language, and add some basic interactivity using our keyboard and mouse. By the end of this course, you'll be up to speed with modern OpenGL, and the new advanced programmable Pipeline. Now let's get started with Up and Running with OpenGL.

**What You Should Know**

OpenGL itself can be wrapped in a variety of languages and bindings exist in Python and Ruby for example. But for this course, we'll be programming in C++. So some familiarity with C or C++ would be helpful. A great course to get up to speed with C++ is Bill Wyman's C/C++ essential training. Graphics programming itself, because it involves negotiating with the GPU, and some mathematics. Can be a challenging subject. Patience will go a long way.

Beyond that, an open imagination is all you need to become an expert OpenGL programmer.

**Using The Exercise Files**

    The exercise files folder includes everything you need to set up a working OpenGL environment. The examples folder has all of the .cpp source code that we use in this course. We're going to be using CMake to generate the actual Xcode project files or Visual Studio files if you're on Windows, from these .cpp files. Alternatively, you can also use the run.sh script if you're on a Unix-like system, feeding it the file path to the .cpp file.

    So for instance, you could do ./run.sh examples/cube.cpp to compile and run that project. The GLFW folder contains a popular library for generating GL window contexts in a cross-platform manner. The GLM folder contains a popular mathematics library we'll be using for generating matrix transforms. The Include folder contains some encapsulated OpenGL functionality that we'll be going over throughout the course.

    The Resources folder contains any assets that we'll be importing into our project, such as this flower bumpmap which we'll be using as a texture. Finally, in the Win folder, I've included the Windows-specific version of the GLU extension wrangler library. I've included GLU here for those of you buidling on Windows since knowing exactly where GLU is can be helpful. The CMake list files will also help CMake find the relevant include-paths, such as the exercise files path itself, the include folder and GLFW's include-path.

    With these resources and examples, we have everything we need to get up and running with OpenGL.

## 1. Setting Up OpenGL Development Environment  

### 1.1 Setting up in OS X

    On OS X, we're gonna wanna make sure we have Xcode installed. We can get Xcode for free from the Mac App Store. Xcode will install most of the tools we need for this course, except for CMake. We want to use CMake to help us in cross compiling our code and making sure that our project files are pointing to the right libraries. CMake is a great tool for writing code that will work across different platforms. I like building CMake from source, so on the CMake website, let's download the Unix/Linux Source tar files.

www.cmake.org/cmake/resources/software.html

    Once they are downloaded, cd into the CMake file directory. Here we can type dot slash bootstrap && make && make install. Depending on your user permissions, you may need to write sudo make install. This will build, compile and install the CMake command line tools onto our OS platform. With CMake installed, we can cd into our exercise files folder.

    Where we are gonna do here is use CMake to generate an Xcode project file that contains all the lessons for this course. Let's make an Xcode directory, cd into the Xcode directory and type cmake space dash capital G for generate space Xcode in quotes capital X lower-case c o d e space dot dot and hit return.

    Cmake is now generating an Xcode project file for us that points to the correct libraries and include header files. If we look inside of our exercise files folder, we see our Xcode directory, and the Xcode project that CMake has generated for us. Let's open that. In our project hierarchy we have all the example files that we're going to be looking at throughout this course. We also have some of the demos that come included with GLFW, the windowing library.

    To follow along with the lessons, open the folder that corresponds to the lesson name. In the Source Files directory, we'll find our dot cpp files that correspond to the current lesson. To compile all the current lesson, navigate to the list of targets, select the target and build that. My Xcode project will look a little different. The name of my Xcode project will be at the top of the screen, corresponding to the current lesson.

    In the file hierarchy on the left-hand side of the screen, the name of the current lesson also corresponds with the name of the project. So in your Xcode project file, which includes all the lessons in one project file, just make sure that you are in the same folder as the name of the current lesson, and you should be able to follow along.

### 1.2 Setting up in Windows  

    On Windows, we're going to want to make sure we have Visual Studio installed. Visual Studio includes most of the tools we're going to need for this course with the exception of CMake. CMake, we can download from the cmake.org website. In the resources section, download the Win32 installer. Launch the executable and follow instructions to install CMake. With CMake installed, we want to navigate to our Visual Studio Developer tools command prompt. This is different than the Windows built-in command prompt, since it points to different libraries that we're going to need to use.

    Inside the developer command prompt for Visual Studio, we want to CD into our exercise files folder. Inside our exercise files folder, we want to make a new directory. We'll call it Visual Studio. We can CD into that new directory. Inside the Visual Studio folder, we can use CMake to generate a Visual Studio project, which will contain all the lessons for this course.

    We type CMake, space, dash, capital G, space, quotes, Visual, space, Studio, space, and here we want to insert the addition of Visual Studio that we haven't installed. In my case, it's Visual Studio 12, so I put 12, and quotes, space, dot, dot, and hit return. CMake is now generating a Visual Studio pro project which will contain all the lessons for this course.

    We navigate into our exercise files folder, and into our Visual Studio folder that we've created. We can click on any of these project files. We can open up the UAR OpenGL project file. On the right in our solution explorer, we can see a list of all the example files that we used in this course along with some example files that are included automatically by GLFW, our window in library. To follow along with the lessons in this course, open up the respective project file.

    Open up the Source Files folder. Double-click on the dot cpp file inside. You'll be able to see the source code from the lessons. To compile a particular lesson, click on the top solution UAR OpenGL, and then the properties window. Scroll down to where it says start up project, and select the respective project. Go, then compile that, and you should be able to follow along.

    In the lesson videos, I'll be using individual Xcode project files. The name of the example file will be at the top of my screen. To follow along, just pick the right example from the right hand side of your Visual Studio project.

### 1.3 Setting up from Scratch

    I recommend for this course that you use CMake to automate the generation of your project files But, if you're having trouble using CMake, you can build your project from scratch. So, an Xcode for example, you wanna set your headers search paths to search in the exercise files include directory, the exercise files directory, and the exercise files/GLFW/include directory. You also need to make sure that you're linking to the correct libraries. You wanna make sure that you're linking to GLFW itself.

    GLFW will need to be built using CMake. so you'll need to CD into the GLFW directory, and build GLFW from there. You'll want to point to wherever GLU is installed on your system. And you'll need to link to the Cocoa OpenGL I/O kit, core foundation, and core video frameworks. If you're on a Windows machine, you need to make sure that you're linked to the GLU library and OpenGL 32.lib in addition to the GLFW library.

    Also make sure that your library search paths are set so that they search in the correct directory for those libraries. And making sure that your header search paths are set correctly. And you're linking to all the necessary libraries. And your library search paths are searching in the right directory for those libraries. You should have no trouble building an OpenGL environment from scratch.

## 2. Introducing OpenGL

### 2.1 Understanding OpenGL

    The GL in OpenGL stands for graphics library. It specifies a protocol for rendering graphics on your computer screen. Provides an API for transferring data between your CPU and your GPU, or graphics processing unit. The ultimate goal of OpenGL is to effectively generate pixels on your screen. We call this administration of data transfer the OpenGL pipeline. And we'll be investigating that pipeline in this course. As an open standard, OpenGL works on a variety of platforms.

    From PCs to Linux boxes to MacBooks. And various flavors of it, such as OpenGL|ES work on embedded devices like iPhones and Android tablets. WebGL, another flavor is a version of OpenGL that works online. To give us more flexibility as developers, we cover basic OpenGL best practices here, so that the lessons and techniques that you learn will be applicable to those other environments, and will help you generate all sorts of visual content on all sorts of devices.

    So if you're looking for a way to program real-time interactive graphics on a variety of platforms and devices, learning OpenGL is essential. OpenGL has been undergoing constant revisions and updates and will likely continue to do so. As of this tutorial, OpenGL is on version 4. Your graphics card may be using versions 2 or 3. Add to that the various flavors of OpenGL used on phones and on the web, and what we have is a lot of ways of doing things. So what is the right way? This course is designed to clarify and highlight the correct way to render graphics using OpenGL.

    The methods we cover work on OpenGL 2 and above, and represent the best practices for sending data to your graphics card for rending onto your screen. Ready? Let's get started.

### 2.2 Introduction to OpenGL Terminology

    Let's explore some terminology that we're going to be using throughout this course. Let's start with a pixel. A pixel is the smallest indivisible square or rectangular region of your screen. Any pixel on our screen has a red, green, blue, and alpha component. So, when we talk about creating color, we'll talk about creating red, green, blue, and alpha values. These are usually stored as four floating-point values. A vertex, in the graphics world, is a set of attributes. At the very least, a vertex can be considered a coordinate position in space.

    So, in 2D a vertex would have an X and Y coordinate. In 3D, a vertex would have an X, Y, and Z coordinate. Vertices can also have other information. As we'll see, a vertex can also have other information attached to it, such as color information or texture coordinate information or a normal direction. We'll talk about these in due course. When we talk about frames, we'll be talking about frames of animation. Using the GLFW Library, our code will typically run at about 60 frames per second.

    Each frame will be executing a draw loop or a main loop. A framebuffer is an array of pixels. This is the image that you actually see on your screen. There are two framebuffers, the front buffer and the back buffer. At any given moment, in OpenGL, you're seeing the front buffer, while the back buffer is being rendered to. We swap these buffers every frame of animation, so that the new buffer that you see was the last one to be written to. Filling these buffers is called rendering.

    Finally, we should mention that OpenGL specifies its own data types. So, if you're a C programmer, you're familiar with int and unsigned byte and float. If we want to make sure that our GPU is receiving the same type of information, it's safe to say that if we want to send data to the GPU, we should use GL's versions of these types. So, we want to call it GLubyte or GLuint or GLfloat. Open GL will also specify enumerations for naming these types. You'll find that a lot of our functions will call for a particular data type to be specified.

    These are usually written in all capitals, GL UNSIGNED BYTE, GL UNSIGNED INT, or GL FLOAT. So, we've taken a quick peek at some of the terminology we have to look forward to. Now let's get started.

### 2.3 Creating a Context and Getting Version Info



### 2.4 Creating a Context and a Window



### 2.5 Creating a Context and Getting Extension Information



### 2.6 Cleaning Up the Code: Making an Application Structure




## 3. Intermediate Mode

### 3.1 Drawing Geometric Primitives





### 3.2 Rotating, Translating and Scaling





