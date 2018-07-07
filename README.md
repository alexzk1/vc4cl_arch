# vc4cl_arch
installer for archlinux for vc4cl - OpenCL implementation running on the VideoCore IV GPU of the Raspberry Pi models

Original is here:

  https://github.com/doe300/VC4CL

Depends on preinstalled stdlib and compiler:

  https://github.com/alexzk1/vc4_stdlib_arch
  
  https://github.com/alexzk1/vc4c_archlinux

You must have it avail at runtime, so embedded opencl code in your program will be compiled.


So working chain is:

1. You embedd opencl code in your program.
2. That code is directed to opencl.
3. Opencl directs it to backend (this package).
4. Backend directs it to gpu compiler (vc4c).
5. Compiler produces code at runtime of your program, and it is executed by this backend.
