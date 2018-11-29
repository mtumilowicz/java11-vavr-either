# java11-vavr-either

_Reference_: https://www.vavr.io/vavr-docs/#_either  
_Reference_: https://static.javadoc.io/io.vavr/vavr/0.9.2/io/vavr/control/Either.html  

# preface
`Either` represents a value of two possible types. An 
`Either` is either a `Left` or a `Right`. If the given 
`Either` is a `Right` and projected to a `Left`, the `Left` 
operations have no effect on the `Right` value. If the 
given `Either` is a `Left` and projected to a `Right`, the 
`Right` operations have no effect on the `Left` value. If 
a `Left` is projected to a `Left` or a `Right` is projected 
to a `Right`, the operations have an effect.

**By convention the success case is `Right` and the 
failure is `Left`.**

# project description
We provide description and tests for `Either`'s methods.

Please refer my other github projects: 
* https://github.com/mtumilowicz/java11-vavr-option 
* https://github.com/mtumilowicz/java11-vavr-try
because we won't provide examples to the similar 
methods described in the projects mentioned above.

## static methods
* `<L,R> Either<L,R>	left(L left)` - 
Constructs a `Either.Left`
* `<L,R> Either<L,R>	right(R right)` - 
Constructs a `Either.Right`
* `<L,R> Either<L,R>	narrow(Either<? extends L,? extends R> either)` - 
Narrows a widened `Either<? extends L, ? extends R>` to 
`Either<L, R>` by performing a type-safe cast.
* `<L,R> Either<Seq<L>,Seq<R>>	sequence(Iterable<? extends Either<? extends L,? extends R>> eithers)` - 
Reduces many `Eithers` into a single `Either` by 
transforming an `Iterable<Either<L, R>>` into a 
`Either<Seq<L>, Seq<R>>`.
* `<L,R> Either<L,Seq<R>>	sequenceRight(Iterable<? extends Either<? extends L,? extends R>> eithers)` - 
Reduces many `Eithers` into a single `Either` by 
transforming an `Iterable<Either<L, R>>` into a 
`Either<L, Seq<R>>`.
