# Comparator (comparator)

## compare

```rust
public fun compare<T>(
    left: &T,
    right: &T
): Result
```

Type parameters:

-   `T`: type of comparing data

Parameters:

-   `left`: object is compared on the left side
-   `right`: object is compared on the right side

Performs a comparison of two types after BCS serialization.

Returns:

-   `Result` object of comparating process

## compare_u8_vector

```rust
public fun compare_u8_vector(
    left: vector<u8>,
    right: vector<u8>
): Result
```

Parameters:

-   `left`: vector is compared on the left side
-   `right`: vector is compared on the right side

Performs a comparison of two types after BCS serialization.

Returns:

-   `Result` object of comparating process

## is_equal

```rust
public fun is_equal(result: &Result): bool
```

Parameters:

-   `result`: immutable reference to `Result` object of a comparision

Check whether given `Result` is equal.

## is_greater_than

```rust
public fun is_greater_than(result: &Result): bool
```

Parameters:

-   `result`: immutable reference to `Result` object of a comparision

Check whether given `Result` is greater than.

## is_smaller_than

```rust
public fun is_smaller_than(result: &Result): bool
```

Parameters:

-   `result`: immutable reference to `Result` object of a comparision

Check whether given `Result` is smaller than.