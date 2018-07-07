# vc4cl_arch
installer for archlinux for vc4cl - OpenCL implementation running on the VideoCore IV GPU of the Raspberry Pi models

Original is here:

  https://github.com/doe300/VC4CL

Depends on preinstalled stdlib and compiler:

  https://github.com/alexzk1/vc4_stdlib_arch
  
  https://github.com/alexzk1/vc4c_archlinux

You must have it avail at runtime, so embedded opencl code in your program will be compiled.


So working chain is:

1. You embedd opencl code in your program (it is C program called "kernel").
2. That code is directed to opencl.
3. Opencl directs it to backend (this package for raspbery-pi or CUDA on desktop).
4. Backend directs it to gpu compiler (vc4c).
5. Compiler produces code at runtime of your program, and it is executed by this backend.


There is another option. You can install compiler on your x86 desktop and produce already compiled kernels as binary blobs effectively skipping 1-4, which you will load manually. However those blobs will run only on PI. If you want do so, edit PKGBUILD and disable dependency.
