# Scala Library
> com.kyledinh.scala-library.*
Example library to be published in GitHub.

## Setting GitHub Token
- https://github.com/settings/tokens
- Settings > Developer Settings > Personal access token > Token (classic) > "Generate new token" button 
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

In SBT
- `publish`


## Resources
- Tutorial: https://medium.com/@supermanue/how-to-publish-a-scala-library-in-github-bfb0fa39c1e4


