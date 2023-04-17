# Scala Library
> com.kyledinh.scala-library.*
Example library to be published in GitHub.

## Generate GitHub Token
- https://github.com/settings/tokens
- Settings > Developer Settings > Personal access token > Token (classic) > "Generate new token" button 
[![GitHub Token Screenshot][github-token]](./docs/assets/github-token.png)

## Add GitHub Token to credentials used SBT
- Place generated token in `$HOME/.sbt/1.0/github.sbt`
```
credentials += 
  Credentials(
    "GitHub Package Registry",
    "maven.pkg.github.com",
    "GITHUB USERNAME",
    "GITHUB TOKEN")
```

## Commands to publish

- `sbtn publish`

## Example usage

[build.sbt](https://github.com/kyledinh/scala-3-workspace/blob/main/build.sbt)
```
externalResolvers += "ScalaLibrary packages" at "https://maven.pkg.github.com/kyledinh/scala-library"

lazy val root = project
  .in(file("."))
  .settings(
    name                                   := "scala-3-workspace",
    version                                := "0.1.0-SNAPSHOT",
    scalaVersion                           := "3.2.2",
    libraryDependencies += "org.scalameta" %% "munit" % "0.7.29" % Test,
    libraryDependencies += "com.kyledinh" %% "scala-library_3" % "0.1.0-SNAPSHOT"
  )
```

[scala code](https://github.com/kyledinh/scala-3-workspace/blob/main/src/main/scala/Main.scala)
```scala
import com.kyledinh.sudoku.*

@main def hello: Unit =
  println("Solving a Sudoku problem...")

val s1 = Sudoku.loadFromResource("puzzles/sudoku_5.txt")
val answer = Sudoku.simulate(s1)
```

## Resources
- Tutorial: https://medium.com/@supermanue/how-to-publish-a-scala-library-in-github-bfb0fa39c1e4

<!-- MARKDOWN LINKS & IMAGES -->
[github-token]: docs/assets/github-token.png
