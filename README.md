
# TESD

The easiest possible test to write - you don't even have to reach back up and press 't' again. A minimal testing environment free of integration needs.

Copy a module and add test scripts to it. No framework APIs. No virtual environments needed. No setuptools or distutils. No dependencies. No package to import. **Nothing** to import.

## Example

Put all tests in their own directory/zip with this `__main__.py`:

    .
    ├── myproj
    │   └── __init__.py       <-- your stuff
    └── tesds
      ├── __main__.py         <-- TESDS __main__.py
      ├── function1test.py    <-- your tests
      ├── function2test.py    <-- your tests
      └── submoduletests.py   <-- your tests
      

Failing `function2test.py`:

    import myproj
    assert False, "haven't implemented function 2"


Run tests:

    $ ls
    myproj  tesds
    $ python tesds
    tesd PASS - module function1test
    haven't implemented function 2
    tesd FAIL - module function2test
    tesd PASS - module submoduletests

## Detailed How-To

  1. Put test scripts in `TEST_DIRECTORY`.
      * Default: directory containing `__main__.py`
  2. Tell the scripts where to find your stuff
      * Default: `WORKING_DIR = '.'` (Your current working directory) point to its parent directory.
  3. If a test fails, make noise however you want.
      * Print
      * `assert` fail
      * throw `Error`
  4. Run tests
      * `python tesds`
      * `python3 tesds`
