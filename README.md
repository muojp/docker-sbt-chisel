# Handy Docker image: SBT + Chisel workspace

## Packages

 - Ubuntu 14.04 based
 - OpenJDK 7
 - SBT 0.13.12
 - Scala 2.11.8
 - Chisel latest + ScalaTest 2.2.6

## Usage

```
docker run -it --rm -v [Your SBT root directory]:/data muojp/sbt-chisel:latest
```

This command launches sbt console. Then you can instantly (w/ super-little overhead) run `compile`, `~compile`, `test`, `run` or whatever sbt sub-commands you like.

## License

MIT

