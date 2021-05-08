# State of the Art - Scala Test Libraries

A rundown of current Scala testing libraries.

I encourage everyone to improve it through PRs! I really only have experience in a couple of these libraries, so I might be missing or misrepresenting something.

## Main points about each library

### [ScalaTest](https://github.com/scalatest/scalatest)
- ![GitHub stars](https://img.shields.io/github/stars/scalatest/scalatest)
- The most popular Scala testing tool.
- Great flexibility in [testing styles](https://www.scalatest.org/user_guide/selecting_a_style).
- Works with Java Code.
- Lots of features (TODO: List the more important ones)

### [Specs2](https://github.com/etorreborre/specs2)
- ![GitHub stars](https://img.shields.io/github/stars/etorreborre/specs2)
- A lot of flexibility.
- A lot of features.
- E.g. different styles of tests: Acceptance vs. Unit styles
  - Unit style is what we use normally (by default, no functional expectations).
  - Acceptance style separates between text and code (show example) (by default, functional expectations).


### [µTest](https://github.com/com-lihaoyi/utest)
- ![GitHub stars](https://img.shields.io/github/stars/com-lihaoyi/utest)
- Claims to only have the minimum necessary.
- Values uniformity over flexibility.

### [MUnit](https://github.com/scalameta/munit)
- ![GitHub stars](https://img.shields.io/github/stars/scalameta/munit)
- Built on top of JUnit.
- Source locations for errors.
- Highlighted stack traces.

### [Weaver Test](https://github.com/disneystreaming/weaver-test)
- ![GitHub stars](https://img.shields.io/github/stars/disneystreaming/weaver-test)
- Easily share cats-effect's Resources between tests.
- Errors appear at the very end of the run report, no matter how many suites were run.
- Provides a lazy logger to enrich reporting with ad-hoc information, ensuring it only gets displayed when a test fails.
- Integrates with specs2.
- Other native integrations: CE, ZIO, Monix, Scalacheck, Discipline.

## Comparison

|                              |    ScalaTest    |     Specs2      |     Weaver Test     | µTest |      MUnit      |
| ---------------------------- | :-------------: | :-------------: | :-----------------: | :---: | :-------------: |
| Test filtering               |       Yes       |       Yes       |         Yes         |  Yes  |       Yes       |
| Nested tests                 |       Yes       |       Yes       |         No          |  Yes  |       No        |
| Tagging                      |       Yes       |       Yes       | Limited<sup>6</sup> |  No   |       No        |
| Flexibility in test styles   |       YES       |    Somewhat     |         No          |  No   |       No        |
| Error messages quality       |      Great      |       Ok        |        Great        |  Ok   |      Great      |
| Choices of matchers          |      A lot      |      A lot      |       Limited       |  No   |     Limited     |
| Parallelism                  | Yes<sup>4</sup> |       Yes       |         Yes         |  ???  |       No        |
| Output flexibility           |       Yes       |       Yes       |         No          |  Yes  | Yes<sup>7</sup> |
| Functional style¹            |       No        | Yes<sup>5</sup> |         Yes         |  No   |       No        |
| Shared cats-effect Resources |       No        |       No        |         Yes         |  No   |       No        |
| Scalacheck integration       |       Yes       |       Yes       |         Yes         |  No   |       Yes       |
| Async tests²                 |       Yes       |       No        |         No          |  Yes  |       Yes       |
| Native support for effects³  |       No        |       No        |         Yes         |  No   |       No        |

1. Non-exception based.
2. Supports test bodies that return a `Future[T]`.
3. Supports test bodies that return an effect, e.g. cats-effect's `IO`.
4. Not the default.
5. Only in Acceptance style.
6. `ignored` and `cancelled`.
7. Through JUnit.

## Extras
- [Cats Effect Testing](https://github.com/typelevel/cats-effect-testing) - Integration between cats-effect and test frameworks.
