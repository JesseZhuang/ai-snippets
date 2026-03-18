---
name: leetcode
description: Draft Astro blog posts for LeetCode problems using the local 0-leet-template, then implement solutions plus tests in Java (algorithm-java), Python (InCodeLearning-Python3), C++ (CSAPP/leetcode), and Rust (rust/crates/leet), with explicit review checkpoints before creating files, running tests, or committing astro-leetcode.
---

## commands to run unit tests

replace the argument in commands below with the newly generated test file with to run tests only in that file

- Python `cd /Volumes/code/InCodeLearning-Python3 && source venv312/bin/activate && python -m unittest discover -s test -p "test_binary_search.py"`
- Java `cd /Volumes/code/algorithm-java && ./gradlew test --tests "hash.FindUniqueBinaryStringTest"`
- Rust `cd /Volumes/code/rust cargo test tree::lowest_common_ancestor_bt_iii`
- C++ `/Volumes/code/CSAPP/leetcode/cmake-build-debug/test/LeetCode_test --gtest_filter=deque.basic_calculator_ii`, cmake is at `/Applications/CLion.app/Contents/bin/cmake/mac/aarch64/bin/cmake` (do not rebuild unless you need to)

## workflow

1. ask the user which leetcode question to do
1. use agent knowledge, pick the best solution
1. only add a second solution that is popular and uses a different data structure or algorithm
1. present the solutions to the user to review and finalize
1. implement the solutions in python,  unit tests covering edge cases, ask user to review
1. take the user modified python implementation, use 3 subagents to work in parallel to implement the solutions and unit tests in the other three programming languages
1. run the unit tests (refer to commands above) and modify until all tests pass
1. ask user to review and test the code on leetcode
1. after user finish, use 4 subagents to commit in the 4 repos (for CSAPP/leetcode repo, commit in parent folder CSAPP) and push all 4 repos
1. following the template `/Volumes/code/astro-leetcode/src/content/blog/0-leet-template.md`, **use code committed and pushed in above step** to create a markdown file (name `leet-<4 digit id>-<kebab-title>.md`) to explain the solutions (including time and space complexities). Draw ascii diagrams as needed to help the explanation. If equation is needed, refer to https://katex.org/docs/api. ask the user to review. make sure the constraints section from leetcode is included.
1. after user finish, remove the line `draft: true` and make sure the line `featured: true` is in the file.
1. look for oldest posts with `featured: true` line (can use a temp file to remember), keep 6 most recent featured post in total
1. commit in astro-leetcode repo and finish.
