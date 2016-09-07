Building AVE
============
To build the a version of AVE, first download the source code from [GitHub](/git).

The `build.py` file in the downloaded folder allows you to build the different versions.

To build the [Python version](/docs/python.md), run `./build.py python`.
To build the [EMF badge version](/docs/badge.md), run `./build.py emf`.
To build the [JavaScript version](/docs/javascript.md), run `./build.py javascript`.
To build the [website version](/docs/javascript.md), run `./build.py website`.

By default, these will build in a folder called `build`. You can change this by passing another argument, for example `./build.py python /path/to/build/in`.
