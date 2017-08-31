# Handy Docker image: SBT + Chisel 3 workspace

## Packages

 - Ubuntu 16.04
 - OpenJDK 8
 - SBT 0.13.15
 - Scala 2.11.11
 - Chisel3 latest + ScalaTest 2.2.6
 - Verilator 3.886

## Usage

```
docker run -it --rm -v [Your SBT root directory]:/data muojp/sbt-chisel:latest
```

This command launches sbt console. Then you can instantly (w/ super-little overhead) run `compile`, `~compile`, `test`, `run` or whatever sbt sub-commands you like.

## License

MIT

