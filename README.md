# profiling-cpp

#This guide explains how to profile a C++ executable using gprof, then visualize the results using gprof2dot and Graphviz for generating a call graph visualization.

**Prerequisites**
CMake
gprof
gprof2dot
Graphviz (for dot command)

**Instructions**

1. Compile using CMAKE with Profiling Flags

$ cmake -DCMAKE_CXX_FLAGS=-pg -DCMAKE_EXE_LINKER_FLAGS=-pg -DCMAKE_SHARED_LINKER_FLAGS=-pg <source-dir>
$ make

2. Run the Executable:
 
$ ./executable

3. Generate Profile Data using GNU gprof:

$ gprof executable gmon.out > output.txt

4. Install gprof2dot with pip:
 
$ pip install gprof2dot

5. Convert Profile Data to DOT Format using gprof2dot:

$ gprof2dot -o output.dot output.txt --node-label=self-time

6. Generate PNG Visualization using dot:
   
$ dot -Tpng -o output.png output.dot
