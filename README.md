# Zsy: A Dataflow Synchronous Programs with Timers

This distribution includes the Zélus compiler extended to compile Zsy
programs, runtime libraries, and example source code. The OCaml
runtime (ocamlrun) is required to transform Zélus programs into
imperative code. The OCaml compiler is required to compile imperative
code into executables.

## Dependencies

| Dependency | Version | Reason |
|------------|---------|--------|
| [OCaml](http://ocaml.org/) | Required == 4.04.0  | Run the Zélus compiler and compile the examples |
| [XQuartz](http://www.xquartz.org/) | Optional >= 2.7.9 | Required on MacOS to run the examples using OCaml Graphics |


## Installing the compiler

Run the configure script (optionally setting an installation prefix):

```
./configure --prefix=/usr/local
```

Zélus can then be installed by running:

```
sudo make install
```

An option `-symb <main_node>` allows to compile Zsy programs.
An example of a Zsy program is given in `examples/symb_qpa`.

## Example

An example of a Zsy program simulating a simple two-node architecture
can be found in `example/qpa.zls`. To build the example run:

```
make example
./example/qpa.byte
```
