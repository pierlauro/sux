sux
===

Welcome to the C++ part of the [sux](http://sux.di.unimi.it/) project.

Available classes
-----------------

The classes we provide fall into three categories:

* Static structures for ranking and selection based on the paper "Broadword
Implementation of Rank/Select Queries". We provide also an implementation of
the Elias-Fano representation of monotone sequences that can be used as an
opportunistic bitvector representation.

* Fenwick trees with bounded leaf size, and associated dynamic structures for
ranking and selection based on the paper "Compact Fenwick Trees for Dynamic
Ranking and Selection" (with Stefano Marchini).

* Minimal perfect hashing functions based on the paper "RecSplit: Minimal
Perfect Hashing via Recursive Splitting" (with Emmanuel Esposito and Thomas
Mueller Graf).

All classes are heavily asserted. For testing speed, remember to use `-DNDEBUG`.

We do not provide libraries: you are invited to include the sources with your
code.

Benchmarks
----------

The commands `make ranksel` and `make recsplit` will generate binaries in `bin`
with which you can test the speed of RecSplit and rank/selection static
structures. Note that you can set the `make` variable `LEAF` to change the leaf
size of RecSplit, as in `make recsplit LEAF=4`.

For ranking and selection, we generate one binary for each type of structure,
with some variation on parameters (see the makefile for more details). Beside
the number of bits, you can provide one or two probabilities. Bits will be set
to one with the given probability in the first half of the test array, and with
the second probability in the second half (if no second probability is
specified, it is assumed to be equal to the first one). This setup is necessary
to show the slow behaviour of naive implementations on
half-almost-empty-half-almost-full arrays.

For RecSplit, we provide dump/load binaries which dump on disk a minimal
perfect hash function, and test it. The standard version uses a keys file for
the keys, whereas the “128” version uses 128-bit random keys. We suggest the
latter for benchmarking as in any case the first step in RecSplit construction
is mapping to 128-bit hashes.

seba (<mailto:sebastiano.vigna@unimi.it>)
