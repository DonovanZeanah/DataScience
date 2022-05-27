# How to Use

Choose Scala 2.12 or 2.13 on start.

Use 2.12 if you want to use Spark.

Otherwise, whichever.

## Install Dependencies

Generally, syntax complies with Ammonite script rules.

```scala
import $ivy.`org.typelevel::cats-core:2.3.0`,cats._,cats.syntax._
```

## Import modules from file

```scala
import $file.path.to.Example, Example._
```

For further information, see https://ammonite.io/

## Data Visualization

TODO: Setup Plotly support in `Dockerfile`