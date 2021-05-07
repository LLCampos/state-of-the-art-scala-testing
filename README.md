# State of the Art - Scala Test Libraries

A rundown of current Scala testing libraries.

I encourage everyone to improve it through PRs! I really only have experience in a couple of these libraries, so I might be missing or misrepresenting something.

## Main points about each library


### [ScalaTest](https://github.com/scalatest/scalatest)
- ![GitHub stars](https://img.shields.io/github/stars/scalatest/scalatest)
- The most popular Scala testing tool
- Great flexibility in [testing styles](https://www.scalatest.org/user_guide/selecting_a_style)
- Works with Java Code
- Lots of features (TODO: List the more important ones)

### [Specs2](https://github.com/etorreborre/specs2)
- ![GitHub stars](https://img.shields.io/github/stars/etorreborre/specs2)
- A lot of flexibility
- A lot of features!
- E.g. different styles of tests: Acceptance vs. Unit styles
  - Unit style is what we use normally (by default, no functional expectations)
  - Acceptance style separates between text and code (show example) (by default, functional expectations)


### [µTest](https://github.com/com-lihaoyi/utest)
- ![GitHub stars](https://img.shields.io/github/stars/com-lihaoyi/utest)
- Claims to only have the minimum necessary (not a surprise, considered it was developed by Li Haoyi!)
- Values uniformity over flexibility

### [MUnit](https://github.com/scalameta/munit)
- ![GitHub stars](https://img.shields.io/github/stars/scalameta/munit)
- Built on top of JUnit
- Source locations for errors
- Helpful diffs
- Highlighted stack traces


### [Weaver Test](https://github.com/disneystreaming/weaver-test)
- ![GitHub stars](https://img.shields.io/github/stars/disneystreaming/weaver-test)
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

|                            |       ScalaTest       |          Specs2          |            Weaver Test             | µTest |  MUnit  |
| -------------------------- | :-------------------: | :----------------------: | :--------------------------------: | :---: | :-----: |
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