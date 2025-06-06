# Sudoku Solver Dancing and Failing

This project aims to produce a solver for the general [sudoku puzzle](https://en.wikipedia.org/wiki/Sudoku). The general variant is basically the sudoku with no specific size. Classically, the sudoku uses `9`x`9` grid, but in general it can any size divisible into equal blocks, e.g., `4`x`4`, `16`x`16`, `25`x`25`, etc.

This time we will implement a bit smarter solver operation on so-called `first-fail` principle.
We will also an existing solver implementend in `C` and run it directly from Python in a separate process.

## TODO: 

There are several tasks to complete:
- [ ] reuse configuration from the previous lab
- [ ] copy already implementd methods from the previous lab
    - some of them will require tweaking (specified in the comments)
- [ ] implement:
    - `src/utils/recursion_limit.py` — context-manager making it easier to bypass some Python limitations
    - `src/solvers/solver.py` — an abstract Solver class being an interface for all the other solvers
    - `src/solvers/first_fail_solver.py` — a smarter version of the naive solver
    - `src/solvers/dancing_links_solver.py` — solver calling an external implementation implemented in `C`
- [ ] use `benchmark.py` to compare your solvers :)
- [ ] modify the `main.py` file, so:
    - [ ] it accepts `-a` flag specifying the algorithm:
      - tip: for enum `Color` one could write: `parser.add_argument('color', type=Color, choices=list(Color))`, we are using the `SudokuSolverType` enum

    ```
    usage: sudolver [-h] [--algorithm {naive,first_fail,dancing_links}] [--time-limit TIME_LIMIT] puzzle_path

    Sudolver - yet another sudoku solver.

    positional arguments:
    puzzle_path           path to the file containing a sudoku puzzle

    options:
    -h, --help            show this help message and exit
    --algorithm, -a {naive,first_fail,dancing_links}
                            algorithm used to solver the sudoku
    --time-limit, -t TIME_LIMIT
                            time limit for the solver (in seconds)
    ```
- [ ] keep your code tidy by running `ruff format` and `ruff check` or using vs code `ruff` extension
    - bobot won't give points if your file is not well formatted 


## Grading

* [ ] Make sure, you have a **private** group
  * [how to create a group](https://docs.gitlab.com/ee/user/group/#create-a-group)
* [ ] Fork this project into your private group
  * [how to create a fork](https://docs.gitlab.com/ee/user/project/repository/forking_workflow.html#creating-a-fork)
* [ ] Add @bobot-is-a-bot as the new project's member (role: **maintainer**)
  * [how to add an user](https://docs.gitlab.com/ee/user/project/members/index.html#add-a-user)

## How To Submit Solutions

* [ ] Clone repository: git clone:
    ```bash
    git clone <repository url>
    ```
* [ ] Solve the exercises
    * use WebIDE, whatever
* [ ] Commit your changes
    ```bash
    git add <path to the changed files>
    git commit -m <commit message>
    ```
* [ ] Push changes to the gitlab master branch
    ```bash
    git push 
    ```

The rest will be taken care of automatically. You can check the `GRADE.md` file for your grade / test results. Be aware that it may take some time (up to one hour) till this file appears.

## Project Structure

    .
    ├── puzzles                     # contains puzzles of various sizes
    ├── src                         # source directory
    │   ├── model                   # - directory with the problem model 
    │   │   └── grid.py             # TODO: representation of the sudoku grid
    │   ├── solvers                 # TODO: directory with the sudoku solvers
    │   └── utils                   # TODO: various utilities              
    ├── benchmark.py                # you may use this script to compare solvers
    ├── main.py                     # TODO: create this file with `uv init`
    ├── pyproject.toml              # TODO: create this file with `uv init`
    └── README.md                   # the README you are reading now