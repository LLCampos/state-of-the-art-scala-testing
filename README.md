# State of the Art - Scala Test Libraries

A rundown of current Scala testing libraries.

I encourage everyone to improve it through PRs! I really only have experience in a couple of these libraries, so I might be missing or misrepresenting something.

## Selling points for each library

### [Specs2](https://etorreborre.github.io/specs2/)
- A lot of flexibility
- A lot of features!
- E.g. different styles of tests: Acceptance vs. Unit styles
  - Unit style is what we use normally (by default, no functional expectations)
  - Acceptance style separates between text and code (show example) (by default, functional expectations)

### [ScalaTest](https://www.scalatest.org/)
- The most popular Scala testing tool
- Flexible: even works with Java Code
- Great flexibility in [testing styles](https://www.scalatest.org/user_guide/selecting_a_style)
- Also lot of features

### [µTest](https://github.com/com-lihaoyi/utest)
- Claims to only have the minimum necessary
- Values uniformity over flexibility

### [MUnit](https://github.com/scalameta/munit)
- Built on top of JUnit
- Source locations for errors
- Helpful diffs
- Highlighted stack traces


### [Weaver Test](https://github.com/disneystreaming/weaver-test)
- Easily share resources between tests
- More "functional style"
- Native effects support
- Errors appear at the very end of the run report, no matter how many suites were run.
- Provides a lazy logger to enrich reporting with ad-hoc information, ensuring it only gets displayed when a test fails.
- Integrate imperfectly with specs2
- Other native integrations: CE, ZIO, Monix, Scalacheck, Discipline

## Extras
- [Cats Effect Testing](https://github.com/typelevel/cats-effect-testing) - Integration between cats-effect and test frameworks

## Comparison

|                            |       [ScalaTest](https://www.scalatest.org/)       |          [Specs2]()          |            [Weaver Test](https://github.com/disneystreaming/weaver-test)             | [µTest](https://github.com/com-lihaoyi/utest) |  [MUnit](https://github.com/scalameta/munit)  |
| -------------------------- | :-------------------: | :----------------------: | :--------------------------------: | :---: | :-----: |
| GitHub Stars               |          951          |           696            |                187                 |  438  |   207   |
| Native support for effects |          No           |            No            |                Yes                 |  No   |   No    |
| Functional tests           |          No           | Only in Acceptance style |                Yes                 |  No   |   No    |
| Shared Resources           |          No           |            No            |                Yes                 |  No   |   No    |
| Parallelism                | Yes (not the default) |           Yes            |                Yes                 |  ???  |   No    |
| Tagging                    |          Yes          |           Yes            | Limited. `ignored` and `cancelled` |  No   |   No    |
| Nested tests               |          Yes          |           Yes            |                 No                 |  Yes  |   No    |
| Flexibility in test styles |          YES          |         Somewhat         |                 No                 |  No   |   No    |
| Choices of matchers        |         A lot         |          A lot           |              Limited               |  No   | Limited |
| Output flexibility         |          Yes          |           Yes            |                 No                 |  Yes  |   No    |
| Test filtering             |          Yes          |           Yes            |                Yes                 |  Yes  |   Yes   |
| Scalacheck integration     |          Yes          |           Yes            |                Yes                 |  No   |   Yes   |
| Error messages             |         Great         |            Ok            |               Great                |  Ok   |  Great  |