<!-- Copyright 2023 Thomas Brown -->
<!-- Distributed under the Boost Software License, Version 1.0. (See -->
<!-- accompanying file LICENSE_1_0.txt or copy at -->
<!-- http://www.boost.org/LICENSE_1_0.txt) -->

# Boost.Build module for FlatBuffers

## Overview

This project adds support for the FlatBuffers to Boost.Build.

The following is the simplest approach to using this module.  It
assumes a main program named `example.cpp` and two FlatBuffers
protocol definition files named `a.fbs` and `b.fbs`.

```jam
import pkg-config ;

# Jamroot
exe example
  : # sources
    example.cpp

    a.fbs
    b.fbs

    flatbuffers
  ;

lib flatbuffers ;
```

## Requirements

* Boost.Build from Boost C++ Libraries 1.71.0 (or later)
* AsciiDoctor (for documentation)
* Flatbuffers (`flatc` and `flatbuffers`)

## Documentation

The documentation is contained within the Boost.Build module file
(*e.g.*, `flatc.jam`) using inline documentation based on AsciiDoc.  A
top-level document brings in documentation from each module.

Run the following command to build an HTML version of the
documentation.

```shell
b2
```

Run the following command to view the help in the terminal.

```shell
b2 --help protoc
```

This requires that the root directory of this project is reflected in
the Boost.Build path.  This can be done by setting the
`BOOST_BUILD_PATH` environment variable.

## Testing

There are several test projects in the `test` directory.  All tests
are run by default using the default build configuration when
Boost.Build is run in the `test` directory.  Each test can also be run
individually by running Boost.Build in the directory of the desired
test to run.

Run the following command to run all the tests using the default build
configuration.  This adds the directory containing the `flatc.jam`
file to the Boost.Build path.

```shell
cd test && BOOST_BUILD_PATH="$(pwd)"/.. b2 --verbose-test -j 8
```
