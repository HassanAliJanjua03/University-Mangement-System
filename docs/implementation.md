# Implementation notes

This is my second-semester group project, retained as a record of how we approached introductory C++ programming. The source remains in [University Management System.cpp](../University%20Management%20System.cpp).

## Function map

| Area | Main functions |
| --- | --- |
| Main menu | `main()` |
| Academic portal | `portal()`, `enter_marksA()` through `enter_marksD()`, `check_marksA()` through `check_marksD()` |
| Café | `cafe()`, `caf()` |
| Game | `game()`, `g()`, `dash_board()`, `user_turn()`, `gameover()` |

## Data handling

Marks entry writes one CSV per section, using output mode (which can overwrite existing records). Marks lookup opens separate grade CSV files that are not in the repository. The reader uses fixed-size arrays and does not check the number of records against their capacity. The writer also generates some marks with `rand()`. These are educational routines and should not be used with real student data.

## Running and reviewing the code

The source uses GNU-style variable-length arrays, so a GNU-compatible C++ compiler is the appropriate starting point. The build command in the [main README](../README.md) is a suggested command, not a verified successful build. Use a disposable working directory so the CSV output cannot overwrite anything valuable.

The original source contains a hard-coded demonstration login. It is not a secure authentication mechanism; never reuse those values as real credentials. Do not enter real student names, roll numbers or grades.

## Known issues and improvement ideas

| Issue observed in source | Improvement |
| --- | --- |
| Entry and lookup use different CSV files and layouts | Introduce one consistent student record schema |
| Fixed-size and variable-length arrays | Use vectors and bounds-checked parsing |
| Some marks are randomly generated | Separate synthetic test data from entered grades |
| Hard-coded demonstration login | Replace with proper authentication if developing beyond coursework |
| Roti price displayed as 12 but billing adds 200 | Store menu items and prices in a single data structure |
| Game state stored globally | Reset board, turn and draw flag for every new game |
| Invalid moves can fall through using previous coordinates | Validate positions before indexing the board |
| Some non-void functions do not return a value | Correct return types and check compiler warnings |

## Suggested checks (not executed)

- Confirm each main-menu choice and the exit path.
- Review marks entry in a disposable folder; verify the generated CSV fields.
- Check missing-file and malformed-file handling before attempting lookup.
- Order known café items and compare the total against the displayed prices.
- Exercise game win, draw, repeated moves and restart behavior after fixing the input/state issues.

These are proposed checks, not reported test results.

[Back to the project](../README.md)
