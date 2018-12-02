[![Build Status](https://travis-ci.com/mtumilowicz/java11-vavr-either.svg?branch=master)](https://travis-ci.com/mtumilowicz/java11-vavr-either)

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

**Note that** `Try<T> `is isomorphic to `Either<Throwable, T>`.

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

## instance methods
* `Either<X,Y>	bimap(Function<? super L,? extends X> leftMapper,
     Function<? super R,? extends Y> rightMapper)` - 
Maps either the left or the right side of this disjunction.
* `boolean	equals(Object o)`
* `Option<Either<L,R>>	filter(Predicate<? super R> predicate)`
    * if `Left` returns `Option.of(this)`
    * if `Right` and predicate is satisfied 
    returns `Option.of(this)`
    * if `Right` and predicate is not satisfied 
    returns `Option.none()`
* `Either<L,U>	flatMap(Function<? super R,? extends Either<L,? extends U>> mapper)`
    * if `Right` flatMaps
    * if `Left` returns this
* `U	fold(Function<? super L,? extends U> leftMapper,
    Function<? super R,? extends U> rightMapper)`
    * if `Right` maps right value with rightMapper
    * if `Left` maps left value with leftMapper
* `R	get()`
    * if `Right` returns value
    * if `Left` throws `NoSuchElementException`
* `L	getLeft()`
* `R	getOrElseGet(Function<? super L,? extends R> other)`
    * if `Right` returns value
    * if `Left` returns other
* `<X extends Throwable> R	getOrElseThrow(Function<? super L,X> exceptionFunction)`
    * if `Right` returns value
    * if `Left` throws exception
* `int	hashCode()`
* `boolean	isEmpty()`
    `
     @Override
     default boolean isEmpty() {
         return isLeft();
     }
    ```
* `boolean	isLeft()`
* `boolean	isRight()`
* `Either.LeftProjection<L,R>	left()`
* `Either.RightProjection<L,R>	right()`
* `Either<L,U>	map(Function<? super R,? extends U> mapper)`
    * if `Right` maps right value with mapper
    * if `Left` returns this
* `Either<U,R>	mapLeft(Function<? super L,? extends U> leftMapper)`
* `Either<L,R>	orElse(Either<? extends L,? extends R> other)` 
    * if `Right` returns this
    * if `Left` returns left mapped by `other`
* `Either<L,R>	orElse(Supplier<? extends Either<? extends L,? extends R>> supplier)` 
* `void	orElseRun(Consumer<? super L> action)` - 
if `Left` runs action
* `Either<L,R>	peek(Consumer<? super R> action)` - 
if `Right` runs action
* `Either<L,R>	peekLeft(Consumer<? super L> action)` 
if `Left` runs action
* `Either<R,L>	swap()`
Converts a `Left` to a `Right` and vice versa by wrapping the 
value in a new type.