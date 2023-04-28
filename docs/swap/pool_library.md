# Pool library (pool_library)

## sort_token_type

```rust
public fun sort_token_type(
    type_F: &TypeName,
    type_S: &TypeName
): Result
```

Parameters:

-   `left`: `TypeName` object of token F
-   `right`: `TypeName` object of token S

Performs a comparison of two `TypeName`.

Returns:

-   `Result` object of comparating process

## get_type

```rust
public fun get_type<F, S>(): (TypeName, TypeName)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Get `TypeName` object of token F and token S.

Returns:

-   `TypeName` object of token F
-   `TypeName` object of token S

## get_triple_type

```rust
public fun get_triple_type<F, S, T>(): (TypeName, TypeName, TypeName)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type
-   `T`: third token type

Get `TypeName` object of token F, token S and token T.

Returns:

-   `TypeName` object of token F
-   `TypeName` object of token S
-   `TypeName` object of token T