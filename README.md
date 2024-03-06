# 3D-Raytracer #

<p align="center" width="100%">
    <img width="55%" src="https://github.com/ThomasCrisafulli/3D-Raytracer/blob/main/Project%20Photos/Raytracer_Demo_3.PNG">
</p>

# Why I Designed This Project #

This is a project I started just after I finished high school. The current version shown was last worked on during the middle of my sophomore year of college. This project is a personal project I worked on partially to improve my programming and mathematics skills and was not written for any class or academic endeavor. 

The code for this project is available, however due to starting it just after high school, much of the code is not up to my standards and thus will be uploaded after it has been refactored.

# Overview #

The latest version, shown here, is a fully 3D raytracing rendering engine, which has keyboard and mouse support for navigating the rendered scene. The mouse is used for controlling where the camera is pointed, while the keyboard is used for movement in the forward, backwards, left, right, up, and down directions relative to where the camera is pointing. The rendering code, along with the user interface code was written from scratch, although to provide a way to interface cleanly with Windows, OpenGL is used. OpenGL is only used to collect mouse and keyboard inputs, and to create a window that accepts a custom framebuffer. The framebuffer and all of the rendering math, along with processing how the keyboard and mouse commands correspond to movement in 3D space is handled solely by the code I wrote.

The way this ray tracer works is by extending a plane some settable distance away from the camera in the direction the camera is pointing, and, by subdividing this plane into a grid of pixels, projects out a series of rays from the camera's origin toward each pixel on the grid. These rays are then extended out past the grid and tested for any intersections with objects in the scene. If an object is not intersected, the location of the ray a large distance away is used to compute where the ray should intersect the "sky."

# Performance #

This project currently runs all rendering math on the CPU, instead of the GPU. This is due to trying to write code in a sustainable and testable way, before later optimizing for performance. Ideally, this rendering code will at some point be ported to run primarily on the GPU for significantly better performance. Although this code was first written to run on a single CPU thread, it was extended later in development to be able to use all of the CPU cores on a processor, although this is still experimental and does not account for CPU architectures that have heterogeneous processor architectures, e.g. big and little CPU cores.

### Benchmark and Photos ###
On a 9th Generation i7 Intel laptop processor, running on a single CPU thread at a rendering resolution of 800 x 800 pixels, this project runs at an average of 40 FPS (20-30 ms per frame, depending on what is visible), rendering the scenes shown in the pictures below. When running on all CPU cores, the maximum framerate of the monitor I am using is reached, and I cannot get accurate test results.

<p align="center" width="100%">
    <img width="70%" src="https://github.com/ThomasCrisafulli/3D-Raytracer/blob/main/Project%20Photos/Raytracer_Demo_1.png">
</p>

<p align="center" width="100%">
    <img width="70%" src="https://github.com/ThomasCrisafulli/3D-Raytracer/blob/main/Project%20Photos/Raytracer_Demo_2.png">
</p>

