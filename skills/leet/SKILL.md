---
name: leetcode
description: Draft Astro blog posts for LeetCode problems using the local 0-leet-template, then implement solutions plus tests in Java (algorithm-java), Python (InCodeLearning-Python3), C++ (CSAPP/leetcode), and Rust (in_code_learning_rust/crates/leet), with explicit review checkpoints before creating files, running tests, or committing astro-leet.
---

agent only need to slack me success/failure and one sentence summary. save logs of the workflow in /tmp/leet-<date and time>

## commands to run unit tests

replace the argument in commands below with the newly generated test file with to run tests only in that file

- Python `cd InCodeLearning-Python3 && source .venv/bin/activate && python -m unittest discover -s test -p "test_binary_search.py"`
- Java `cd algorithm-java && ./gradlew test --tests "hash.FindUniqueBinaryStringTest"`
- Rust `cd in_code_learning_rust && cargo test -p leet tree::lowest_common_ancestor_bt_iii`
- C++ `CSAPP/leetcode/cmake-build-debug/test/LeetCode_test --gtest_filter=deque.basic_calculator_ii`, use system cmake or `/Applications/CLion.app/Contents/bin/cmake/mac/aarch64/bin/cmake`

## workflow

1. pick a random leetcode question not in the astro-leet repo yet
1. use agent knowledge, pick the best solution
1. only add a second solution that is popular and uses a different data structure or algorithm
1. implement the solutions in python, unit tests covering edge cases, all logic branches, consider constraints given
1. comment on lines where appropriate to incicate time and space complexities, e.g., two nested for loops, outer O(m), inner O(n), so together O(m*n).
1. use 3 subagents to work in parallel to implement the solutions and unit tests in the other three programming languages. if solution already exists in a repo (for exmaple, the java repo has many solutions not included in a blog psot yet), just use that solution directly, agent do not need to re-implement.
1. run the unit tests (refer to commands above) and modify until all tests pass
1. after user finish, use 4 subagents to commit in the 4 repos (for CSAPP/leetcode repo, commit in parent folder CSAPP) and push all 4 repos
1. following the template `astro-leet/src/content/blog/_0-leet-template.md`, **use code committed and pushed in above step** to create a markdown file (name `leet-<4 digit id>-<kebab-title>.md`) to explain the solutions (including time and space complexities). Draw diagrams with pure ascii as needed to help the explanation. If equation is needed, refer to https://katex.org/docs/api. make sure the constraints section from leetcode and link to the question is included.
1. remove the line `draft: true` and make sure the line `featured: true` is in the file.
1. look for oldest posts with `featured: true` line (can use a temp file to remember), keep 10 most recent featured post in total
1. commit and push astro-leet repo.

See [references.md](references.md) for repo layouts and file conventions.

## common mistakes

please avoid

1. forget to include common methods in the blog post
