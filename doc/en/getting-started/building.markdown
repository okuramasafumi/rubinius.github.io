---
layout: doc_en
title: Building Rubinius
previous: Requirements
previous_url: getting-started/requirements
next: Running Rubinius
next_url: getting-started/running-rubinius
---

You can build and run Rubinius from the source directory. You do not need to
install Rubinius to run it. The directions below will detail both installing
Rubinius and running it from the source directory.

Rubinius uses LLVM for the JIT compiler and depends on LLVM 3.x. The
`configure` script will automatically check whether a version is already
available or will download one if not. If you do have LLVM installed and
Rubinius fails to link with it for any reason, pass `--skip-system` to the
`configure` script in the directions below.

### Getting the Source

The Rubinius source code is available as a tarball and as a project on Github.
You can [download the tarball
here](https://github.com/rubinius/rubinius/tarball/master).

To use Git:

  1. Change your current working directory to your development directory
  2. `git clone git://github.com/rubinius/rubinius.git`


### Installing Rubinius

If you are planning on using Rubinius to run your application, this is a good
option. However, you can also run Rubinius directly from the source directory.
See the next section for more details on that.

We recommend installing Rubinius to a location that does not require `sudo` or
superuser privileges. To install Rubinius:

  1. `bundle install`
  2. `./configure --prefix=/path/to/install/dir`
  3. `rake install`
  4. Follow the directions to add the Rubinius _bin_ directory to your PATH


### Running from the Source Directory

If you plan to work on Rubinius itself, you should use this option.

  1. `./configure`
  2. `rake`

If you are just trying out Rubinius, follow the directions to add the _bin_
directory to your PATH.

However, if you are developing Rubinius, you should NOT add the _bin_
directory to your PATH because the Rubinius build system will pick up the
`ruby` and `rake` links to the Rubinius executable. Rubinius needs a separate
Ruby executable to bootstrap itself during the build process.

### Development Mode for Debugging

If you are trying to debug the VM and want to attach a debugger, such as GDB,
then you will want to compile Rubinius without optimizations. You can do this
by setting the 'DEV' environment variable and then building.

For example: `DEV=1 rake build`
