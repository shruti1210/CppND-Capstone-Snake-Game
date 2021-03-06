# CPPND: Capstone Snake Game

This is a starter repo for the Capstone project in the [Udacity C++ Nanodegree Program](https://www.udacity.com/course/c-plus-plus-nanodegree--nd213). The code for this repo was inspired by [this](https://codereview.stackexchange.com/questions/212296/snake-game-in-c-with-sdl) excellent StackOverflow post and set of responses.

<img src="snake_game.gif"/>

Rules:
* The user selects the difficulty level at the beginning: from 1 to 5.
* The higher the difficulty level, the faster the snake starts moving.
* The higher the difficutly level, more points you get by each meal eaten.

## Dependencies for Running Locally
* cmake >= 3.7
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* SDL2 >= 2.0
  * All installation instructions can be found [here](https://wiki.libsdl.org/Installation)
  * Note that for Linux, an `apt` or `apt-get` installation is preferred to building from source.
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory in the top level directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./SnakeGame`.

## New Features
* The user can select a level of difficulty from 1 to 5. The more difficulty, the more the snake speed increases and more points earns for eating food. [commit](https://github.com/lucaspastorduran/CppND-Capstone-Snake-Game/commit/efe02bd2192f236c80508c13fdfb1db822c95ba0)
* Snake speed is defined as private member in Snake, so Game must use "IncreaseSpeed" method to update its value. In that way, snake also controls its maximum speed set to 0.95. [commit](https://github.com/lucaspastorduran/CppND-Capstone-Snake-Game/commit/8a368253ebade78f06bd8a87ebbda8d94a67795e)
* Composition: Snake class is allocated in heap as a smart pointer inside Game class: [commit](https://github.com/lucaspastorduran/CppND-Capstone-Snake-Game/commit/ca23bdc6643ceb37782a597ca89b52b3498b4bf2)
* Composition: Conroller class is allocated in heap as a smart pointer inside Game class: [commit](https://github.com/lucaspastorduran/CppND-Capstone-Snake-Game/commit/ca23bdc6643ceb37782a597ca89b52b3498b4bf2)
* Memory Management: SDL_WIindow and SDL_Renderer are stored as unique_ptr's inside Renderer: [commit](https://github.com/lucaspastorduran/CppND-Capstone-Snake-Game/commit/31ed09fca1da8af03fa67591531c792c28dde0c1)

# Bugs Fixed
* Fix bug regarding placing food out of right boundaries: [commit](https://github.com/lucaspastorduran/CppND-Capstone-Snake-Game/commit/db211626a0bc68c7a0367db8740d7eb3fec5f72b)
* Fix bug of snake moving to the opposite direction: [commit](https://github.com/lucaspastorduran/CppND-Capstone-Snake-Game/commit/e859197f67da484c8a1b6c07ff63e512765b2393)

## Project Rubrics
* [x] README (All Rubric Points REQUIRED):
  * [x] A README with instructions is included with the project.
  * [x] The README indicates which project is chosen.
  * [x] The README includes information about each rubric point addressed.
* [x] Compiling and Testing (All Rubric Points REQUIRED)
* [x] The submission must compile and run.
* [ ] Loops, Functions, I/O
  * [ ] The project demonstrates an understanding of C++ functions and control structures.
  * [ ] The project reads data from a file and process the data, or the program writes data to a file.
  * [x] The project accepts user input and processes the input. --> User can select the level of difficulty: it is displayed in the window title and affects the increase of speed and points each time the snake eats food.
* [ ] Object Oriented Programming
  * [x] The project uses Object Oriented Programming techniques. --> Controller class is located inside Game in order to hide it from main and abstract.
  * [x] Classes use appropriate access specifiers for class members. --> Snake speed is updated through IncreaseSpeed method
  * [ ] Class constructors utilize member initialization lists.
  * [x] Classes abstract implementation details from their interfaces. --> Snake hides to controller its last moved direction.
  * [x] Classes encapsulate behavior. --> Controller only forwards the direction to move, then snake decides if it is allowed or not by checking last direction moved.
  * [ ] Classes follow an appropriate inheritance hierarchy.
  * [x] Overloaded functions allow the same function to operate on different parameters.
  * [ ] Derived class functions override virtual base class functions.
  * [ ] Templates generalize functions in the project.
* [ ] Memory Management
  * [ ] The project makes use of references in function declarations.
  * [x] The project uses destructors appropriately. --> Have set the proper destructors for SDL_Window and SDL_Renderer unique_ptr's, so no memory leaks.
  * [x] The project uses scope / Resource Acquisition Is Initialization (RAII) where appropriate. --> Smart pointers are used instead of raw pointers, which ise the RAII principle, deallocating memory as soon as their owner class goes out of scope.
  * [x] The project follows the Rule of 5. --> We construct the Render inside of Game by using move constructor.
  * [x] The project uses move semantics to move data, instead of copying it, where possible. --> When defining the level of difficulty in main, the value is passed to Game() class as it is not more useull inside main.
  * [x] The project uses smart pointers instead of raw pointers. --> Snake, Controller are allocated in heap and have smart pointers pointing to theme inside Game class. Also SDL_Window and SDL_Renderer inside Renderer.
* [ ] Concurrency
  * [ ] The project uses multithreading.
  * [ ] A promise and future is used in the project.
  * [ ] A mutex or lock is used in the project.
  * [ ] A condition variable is used in the project.
