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

## instance methods
* `Either<X,Y>	bimap(Function<? super L,? extends X> leftMapper,
     Function<? super R,? extends Y> rightMapper)` - 
Maps either the left or the right side of this disjunction.
* `boolean	equals(Object o)`
* `Option<Either<L,R>>	filter(Predicate<? super R> predicate)` - 
Filters this right-biased Either by testing a predicate.
* `Either<L,U>	flatMap(Function<? super R,? extends Either<L,? extends U>> mapper)` - 
`FlatMaps` this right-biased `Either`.
* `U	fold(Function<? super L,? extends U> leftMapper,
    Function<? super R,? extends U> rightMapper)` - 
Folds either the left or the right side of this disjunction.
* `R	get()` - 
Gets the right value if this is a 
`Right` or throws if this is a `Left`.
* `L	getLeft()`
* `R	getOrElseGet(Function<? super L,? extends R> other)`
Gets the Right value or an alternate value, 
if the projected Either is a Left.
* `<X extends Throwable> R	getOrElseThrow(Function<? super L,X> exceptionFunction)`
Gets the Right value or throws, if the projected Either is a Left.
* `int	hashCode()`
* `boolean	isEmpty()`
* `boolean	isLeft()`
* `boolean	isRight()`
* `Either.LeftProjection<L,R>	left()` - 
Returns a `LeftProjection` of this `Either`.
* `Either<L,U>	map(Function<? super R,? extends U> mapper)` - 
Maps the value of this `Either` if it is a `Right`, 
performs no operation if this is a `Left`.
* `Either<U,R>	mapLeft(Function<? super L,? extends U> leftMapper)` - 
Maps the value of this `Either` if it is a `Left`, 
performs no operation if this is a `Right`.
* `Either<L,R>	orElse(Either<? extends L,? extends R> other)` 
* `Either<L,R>	orElse(Supplier<? extends Either<? extends L,? extends R>> supplier)` 
* `void	orElseRun(Consumer<? super L> action)`
Runs an action in the case this is a projection on a Left value.
* `Either<L,R>	peek(Consumer<? super R> action)`
* `Either<L,R>	peekLeft(Consumer<? super L> action)` 
* `Either.RightProjection<L,R>	right()` - 
Returns a `RightProjection` of this `Either`.
* `Either<R,L>	swap()`
Converts a `Left` to a `Right` vice versa by wrapping the 
value in a new type.