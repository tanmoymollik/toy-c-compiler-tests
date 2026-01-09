# Toy C Compiler Test Suite

**[Work In Progress]**

This test suite is a fork of [writing-a-c-compiler-tests](https://github.com/nlsandler/writing-a-c-compiler-tests).

The original test suite only provides runner for x86 architecture.
This test suite is built on top of it to provide support for risc-v architecture.
Check out the description of the parent repo to understand how the code base
works.

This repo implements a new command line argument `--target` for the runner.
By default it's set to `x86_64` but can be overridden to `riscv64`.

*NOTE:* The tests for chapter 19 and 20 are intricately tied to the gnu x86_64
architecture. So this test suite won't work for those 2 chapters. I will try to
re-implement those test suites for risc-v in the future.

# Prerequisites

The test suite assumes that riscv64 toolchain is already installed. Library tests
are compiled using `riscv64-linux-gnu-gcc`. Make sure this is accessible from
your terminal.

You also need `qemu-user` installed. Note that this can only be installed on
Linux. So this test suite is good for developing on Linux while the parent repo
also works on MacOs through x86 arch simulation.

`qemu-riscv64` needs access to riscv64 `libc`. If you installed the riscv64
toolchain it should be available on your computer. Make sure that is installed
under `/usr/riscv64-linux-gnu`. The test suite is hard-coded with this location.
This is the default location when you install riscv64 toolchain using apt-get.

To make sure that you have all the prerequisites ready compile a simple c program
using `riscv64-linux-gnu-gcc` and make sure the following command executes
from your terminal:
```sh
qemu-riscv64 -L /usr/riscv64-linux-gnu your_program
```
This is the same command used by the test suite.

# Usage Example

```sh
./test_compiler my_compiler --chapter 4 --target riscv64
```