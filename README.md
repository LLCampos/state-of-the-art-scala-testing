# State of the Art - Scala Test Libraries

A rundown of current Scala testing libraries.

PRs with improvements and fixes are encouraged. As you can see by the `???`s in the table, it is still incomplete.

## Comparison

|                                  |    ScalaTest    |     Specs2      |     Weaver Test     |     µTest      |      MUnit      | JUnit + sbt JUnit Interface |
| -------------------------------- | :-------------: | :-------------: | :-----------------: | :------------: | :-------------: | :-------------------------: |
| **Test filtering**               |       Yes       |       Yes       |         Yes         |      Yes       |       Yes       |             Yes             |
| **Nested tests**                 |       Yes       |       Yes       |         No          |      Yes       |       No        |             No              |
| **Tagging**                      |       Yes       |       Yes       | Limited<sup>6</sup> |       No       |       Yes       |             Yes             |
| **Flexibility in test styles**   |       YES       |    Somewhat     |         No          |       No       |       No        |             No              |
| **Error messages quality**       |      Great      |       Ok        |        Great        |       Ok       |      Great      |             ???             |
| **Choices of matchers**          |      A lot      |      A lot      |       Limited       |       No       |     Limited     |             ???             |
| **Parallelism within suite**     | Yes<sup>4</sup> |       Yes       |         Yes         |      ???       |       No        |             ???             |
| **Parallelism across suites**    |       Yes       |       Yes       |         Yes         |      Yes       |       Yes       |             ???             |
| **Output flexibility**           |       Yes       |       Yes       |         No          |      Yes       | Yes<sup>7</sup> |             ???             |
| **Functional style**¹            |       No        | Yes<sup>5</sup> |         Yes         |       No       |       No        |             No              |
| **Shared cats-effect Resources** |       No        |       No        |         Yes         |       No       |       No        |             No              |
| **Scalacheck integration**       |       Yes       |       Yes       |         Yes         |       No       |       Yes       |             ???             |
| **Async tests**²                 |       Yes       |       Yes        |         No          |      Yes       |       Yes       |             No              |
| **Native support for effects**³  | No<sup>8</sup>  | No<sup>8</sup>  |   Yes<sup>9</sup>   | No<sup>8</sup> | No<sup>10</sup> |             No              |
| **Scala.js support**             |       Yes       |       Yes       |         Yes         |      Yes       |       Yes       |             Yes             |

1. Non-exception based.
2. Supports test bodies that return a `Future[T]`.
3. Supports test bodies that return an effect, e.g. cats-effect's `IO`.
4. Not the default.
5. Only in Acceptance style.
6. `ignored` and `cancelled`.
7. Through JUnit.
8. For `cats-effect`, supported through [cats-effect-testing](https://github.com/typelevel/cats-effect-testing).
9. `cats-effect`, `Monix`, `Monix BIO`, `ZIO` 
10. For `cats-effect`, supported through [munit-cats-effect](https://github.com/typelevel/munit-cats-effect).

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

### [JUnit](https://github.com/junit-team/junit5) through [JUnit Interface](https://github.com/sbt/junit-interface)
- An implementation of sbt's test interface for JUnit 4. This allows you to run JUnit tests from sbt.
- Unlike Scala testing frameworks like ScalaTest (which can also run JUnit test cases), both JUnit and this adapter are pure Java, so you can run JUnit tests with any Scala version supported by sbt without having to build a binary-compatible test framework first.

## Extras
- [Cats Effect Testing](https://github.com/typelevel/cats-effect-testing) - Integration between cats-effect and test frameworks.
