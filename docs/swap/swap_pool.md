# Swap Pool (swap_pool)

> :warning: **All function from `swap_pool` must be performed type-sorting (using `pool_library` and `comparator`) before calling**

## Mutative functions

### `create_pool`

```rust
public fun create_pool<F, S>(
    registry: &mut PoolRegistry,
    first_token: &mut Coin<F>,
    second_token: &mut Coin<S>,
    first_amount: u64,
    second_amount: u64,
    ctx: &mut TxContext
): Coin<LSP<F, S>>
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: address of `PoolRegistry` shared object
-   `first_token`: mutable reference of token F to add to new pool
-   `second_token`: mutable reference of token S to add to new pool
-   `first_amount`: amount of token F out of `first_token` to add to new pool
-   `second_amount`: amount of token F out of `second_token` to add to new pool

Create new pool for token F and S using balance from `first_token` and `second_token`.

Returns:

-   Liquidity Coin object of created pool
### add_liquidity

```rust
public fun add_liquidity<F, S>(
    registry: &mut PoolRegistry,
    first_token: &mut Coin<F>,
    second_token: &mut Coin<S>,
    amount_F_desired: u64,
    amount_S_desired: u64,
    amount_F_min: u64,
    amount_S_min: u64,
    ctx: &mut TxContext
): Coin<LSP<F, S>>
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: address of `PoolRegistry` shared object
-   `first_token`: mutable reference of token F to add to pool
-   `second_token`: mutable reference of token S to add to pool
-   `amount_F_desired`: expected/maximum amount of token F to add to pool
-   `amount_S_desired`: expected/maximum amount of token S to add to pool
-   `amount_F_min`: minimum amount of token F to add to pool
-   `amount_S_min`: minimum amount of token S to add to pool

Add liquidity into pool of token F and S using balance from `first_token` and `second_token`.

Returns:

-   Liquidity Coin object of created pool

### add_liquidity

```rust
public fun remove_liquidity<F, S>(
    registry: &mut PoolRegistry,
    lsp: &mut Coin<LSP<F, S>>,
    lsp_amount: u64,
    amount_F_min: u64,
    amount_S_min: u64,
    ctx: &mut TxContext
): (Coin<F>, Coin<S>)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: address of `PoolRegistry` shared object
-   `lsp`: mutable reference of liqudity token to redeem
-   `lsp_amount`: liquidity token amount to redeem
-   `amount_F_min`: minimum acceptable amount of token F to get
-   `amount_S_min`: minimum acceptable amount of token S to get

Redeem liquidity token to get back token F and S

Returns:

-   Token F Coin object and Token S Coin object

### swap_exact_first_to_second

```rust
public fun swap_exact_first_to_second<F, S>(
    registry: &mut PoolRegistry,
    first_token: &mut Coin<F>,
    input_amount: u64,
    min_output_amount: u64,
    ctx: &mut TxContext
): (Coin<S>)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: address of `PoolRegistry` shared object
-   `first_token`: mutable reference of token F to swap
-   `input_amount`: amount of token F out of `first_token` to swap
-   `min_output_amount`: minimum acceptable amount of token S to get

Swap an exact amount of token F to get token S out of pool

Returns:

-   Token S Coin object

### swap_exact_second_to_first

```rust
public fun swap_exact_second_to_first<F, S>(
    registry: &mut PoolRegistry,
    second_token: &mut Coin<S>,
    input_amount: u64,
    min_output_amount: u64,
    ctx: &mut TxContext
): (Coin<F>)
```

Same as `swap_exact_first_to_second`

### swap_first_to_exact_second

```rust
public fun swap_first_to_exact_second<F, S>(
    registry: &mut PoolRegistry,
    first_token: &mut Coin<F>,
    output_amount: u64,
    max_input_amount: u64,
    ctx: &mut TxContext
): (Coin<S>)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: address of `PoolRegistry` shared object
-   `first_token`: mutable reference of token F to swap
-   `output_amount`: exact output amount of token S to get
-   `max_input_amount`: maximum acceptable amount out of `first_token` to swap

Swap token F to get an exact amount of token S out of pool

Returns:

-   Token S Coin object

### swap_second_to_exact_first

```rust
public fun swap_second_to_exact_first<F, S>(
    registry: &mut PoolRegistry,
    second_token: &mut Coin<S>,
    output_amount: u64,
    max_input_amount: u64,
    ctx: &mut TxContext
): (Coin<F>)
```

Same as `swap_first_to_exact_second`

### zap_in_first

```rust
public fun zap_in_first<F, S> (
    registry: &mut PoolRegistry,
    first_token: &mut Coin<F>,
    first_amount: u64,
    ctx: &mut TxContext
): (Coin<LSP<F, S>>, Coin<S>)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: address of `PoolRegistry` shared object
-   `first_token`: mutable reference of token F to add to pool
-   `first_amount`: amount of token F out of `first_token` to add

Add liquidity into pool of token F and S using balance just from `first_token`.

Returns:

-   Liquidity Coin object
-   Token S Coin object if left

### zap_in_second

```rust
public fun zap_in_second<F, S> (
    registry: &mut PoolRegistry,
    second_token: &mut Coin<S>,
    second_amount: u64,
    ctx: &mut TxContext
): (Coin<LSP<F, S>>, Coin<F>)
```

Same as `zap_in_first`

### process_swap_exact_input

```rust
public fun process_swap_exact_input<F, S>(
    pool: &mut Pool<F, S>,
    first_token: &mut Coin<F>,
    second_token: &mut Coin<S>,
    input_amount: u64,
    is_reverse: bool,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: address of `PoolRegistry` shared object
-   `first_token`: mutable reference of token F to swap
-   `second_token`: mutable reference of token S to swap
-   `input_amount`: exact amount of token to swap
-   `is_reverse`: `true` if swap F to S | `false` if swap S to F

Swap an exact amount of input token to output token. Should perform type-checking and numeric-checking before call.

### process_swap_exact_output

```rust
public fun process_swap_exact_output<F, S>(
    pool: &mut Pool<F, S>,
    first_token: &mut Coin<F>,
    second_token: &mut Coin<S>,
    output_amount: u64,
    is_reverse: bool,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: address of `PoolRegistry` shared object
-   `first_token`: mutable reference of token F to swap
-   `second_token`: mutable reference of token S to swap
-   `output_amount`: exact amount of token to receive
-   `is_reverse`: `true` if swap F to S | `false` if swap S to F

Swap input token to an exact amount of output token. Should perform type-checking and numeric-checking before call.

## View functions

### get_output_amount

```rust
public fun get_output_amount<F, S>(
    pool: &Pool<F, S>,
    input_amount: u64,
    is_reverse: bool
): u64
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `pool`: immutable reference to Pool object of token F and S
-   `input_amount`: exact amount of token to swap
-   `is_reverse`: `true` if swap F to S | `false` if swap S to F

Get output amount corresponding to the `input_amount` when swapping in pool of token F and S

### get_input_amount

```rust
public fun get_input_amount<F, S>(
    pool: &Pool<F, S>,
    output_amount: u64,
    is_reverse: bool
): u64
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `pool`: immutable reference to Pool object of token F and S
-   `output_amount`: exact amount of token to receive
-   `is_reverse`: `true` if swap F to S | `false` if swap S to F

Get input amount corresponding to the `output_amount` when swapping in pool of token F and S

### is_pool_created

```rust
public fun is_pool_created<F, S>(
    registry: &PoolRegistry
): bool
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: immutable reference to PoolRegistry object

Check of pool of token F and S is created

### is_pool_created_sorted

```rust
public fun is_pool_created_sorted<F, S>(
    registry: &PoolRegistry
): bool
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: immutable reference to PoolRegistry object

Check if pool of token F and S is created. Must perform type-sorting before calling this function.

### borrow_pool

```rust
public fun borrow_pool<F, S>(
    registry: &PoolRegistry
): &Pool<F, S>
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: immutable reference to PoolRegistry object

Get immutable reference of pool of token F and S. Must perform type-sorting before calling this function.

Returns:

-   Immutable reference of Pool F - S

### borrow_mut_pool

```rust
public fun borrow_mut_pool<F, S>(
    registry: &PoolRegistry
): &mut Pool<F, S>
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `registry`: mutable reference to PoolRegistry object

Get mutable reference of pool of token F and S. Must perform type-sorting before calling this function.

Returns:

-   Mutable reference of Pool F - S

### get_amounts

```rust
public fun get_amounts<F, S>(
    pool: &Pool<F, S>
): (u64, u64, u64)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `pool`: immutable reference to Pool object of token F and S

Get most used values in a handy way.

Returns:

-   Amount of token F
-   Amount of token S
-   Total supply of liquidity token LSP

### get_pool_data

```rust
public fun get_pool_data<F, S>(
    pool: &Pool<F, S>
): (u64, u64, u64, u64, u128)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `pool`: immutable reference to Pool object of token F and S

Get most used values in a handy way. Extend version of `get_amounts`

Returns:

-   Amount of token F
-   Amount of token S
-   Total supply of liquidity token LSP
-   Protocol fee (Basis point = 10000)
-   Last value of K (= x \* y)