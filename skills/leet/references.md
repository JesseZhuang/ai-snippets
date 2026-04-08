# Repo Layout References

## Python — InCodeLearning-Python3

- Solutions: `algorithm/<topic>/<snake_case>.py` — class `Solution`
- Tests: `test/test_<name>.py` — `unittest`, `self.solutions = [Solution()]`

## Java — algorithm-java

- Solutions: `src/main/java/<topic>/PascalCase.java` — `public final` class, `private` constructor, `public static` methods
- Tests: `src/test/java/<topic>/PascalCaseTest.java` — JUnit 5

## Rust — in_code_learning_rust/crates/leet

- Solutions: `src/<topic>/<snake_case>.rs` — `pub struct Solution;`, `impl Solution`, `#[cfg(test)] mod tests` in same file
- Module registration: add `pub mod <name>;` in `src/<topic>/mod.rs`

## C++ — CSAPP/leetcode

- Solutions: `src/<topic>/PascalCase.hpp` — header-only, `class Solution`
- Tests: `test/<topic>/PascalCaseTest.cpp` — GoogleTest `TEST(topic, snake_case)`
- Register test: add to `test/CMakeLists.txt` if needed

## Blog — astro-leet

- Template: `src/content/blog/0-leet-template.md`
- Posts: `src/content/blog/leet-<4digit>-<kebab-title>.md`
- Sections: YAML front matter, Description, Idea (with complexity), Java, Python, C++, Rust

# Mixed Code Block format example

```javascript []
console.log('Hello world!')
```
```python []
print('Hello world!')
```
```ruby []
puts 'Hello world!'
```
