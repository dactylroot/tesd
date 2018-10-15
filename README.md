
# TESD

The easiest possible test to write - you don't even have to reach back up and press 't' again. A minimal testing environment free of integration needs.

No dependencies. No package to import. No framework APIs. No virtual environments needed. No setuptools or distutils. Just copy one module file to where your test scripts are. **Nothing** to import.

## Example

Put all tests in their own directory/zip with this `__main__.py`:

    .
    ├── myproj
    │   └── __init__.py       <-- your stuff
    └── tesds
      ├── __main__.py         <-- TESD __main__.py
      ├── function1test.py    <-- your tests
      ├── function2test.py    <-- your tests
      └── submoduletests.py   <-- your tests
      

Example Failing test `function2test.py`:

    import myproj
    assert False, "haven't implemented function 2"


Run tests:

    $ ls
    myproj  tesds
    $ python tesds
    tesd PASS - module function1test
    tesd FAIL - module function2test
      haven't implemented function 2
    tesd PASS - module submoduletests

## Detailed How-To

  1. Put test scripts in sibling directory of your code
      * or somewhere else and update `TEST_DIRECTORY` to point to test scripts
          * and update `WORKING_DIR` to point to your code
  2. When a test fails, make noise however you want.
      * Print
      * `assert` fail
      * throw `Error`
  3. Run tests
      * `python tesds`
      * `python3 tesds`
