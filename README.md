# Scala Library
> com.kyledinh.scala-library.*

### Use GitHub Packages as a maven repository to host your Scala packages.

1. [Generate A GitHub Token](#generate-github-token)
2. [Add GitHub Token to SBT Build](#add-github-token-to-credentials-used-by-sbt)
3. [STB Command to compile and publish](#commands-to-publish)
4. [Example usage in a project](#example-usage)

### Software Versions 

| Software            | Version        | Install                                          |
|---------------------|----------------|--------------------------------------------------|
| JVM                 | openjdk 17.0.4 | https://sdkman.io/install                        |
| Scala               | 3.2.2          | https://www.scala-lang.org/download              |
| sbt                 | 1.8.2          | https://www.scala-sbt.org/download.html          |
| sbt-github-packages | 0.5.3          | https://github.com/djspiewak/sbt-github-packages |

<br><hr><br>

## Generate GitHub Token
- https://github.com/settings/tokens
- Settings > Developer Settings > Personal access token > Token (classic) > "Generate new token" button 
[![GitHub Token Screenshot][github-token]](./docs/assets/github-token.png)

<br><hr><br>


## Add GitHub Token to credentials used by SBT
- Place generated token in `$HOME/.sbt/1.0/github.sbt`
```
credentials += 
  Credentials(
    "GitHub Package Registry",
    "maven.pkg.github.com",
    "GITHUB USERNAME",
    "GITHUB TOKEN")
```
- Add SBTplugin to `project/plugins.sbt`, [dijspiewak/sbt-github-packages](https://github.com/djspiewak/sbt-github-packages)
```
addSbtPlugin("com.codecommit" % "sbt-github-packages" % "0.5.3")
```

<br><hr><br>

## Commands to publish

- `sbtn publish`

<br><hr><br>

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

<br><hr><br>

## Resources
- Tutorial: https://medium.com/@supermanue/how-to-publish-a-scala-library-in-github-bfb0fa39c1e4

<!-- MARKDOWN LINKS & IMAGES -->
[github-token]: docs/assets/github-token.png
