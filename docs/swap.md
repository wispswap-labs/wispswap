# Swap router (swap_router)

## create_pool\_

```rust
public entry fun create_pool_<F, S>(
    setting: &mut Setting,
    first_tokens: vector<Coin<F>>,
    second_tokens: vector<Coin<S>>,
    first_amount: u64,
    second_amount: u64,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `setting`: address of `Setting` shared object
-   `first_tokens`: vector of mutable references of token F to add into new pool
-   `second_tokens`: vector of mutable references of token S to add into new pool
-   `first_amount`: amount of token F out of `first_tokens` to add into new pool
-   `second_amount`: amount of token F out of `second_tokens` to add into new pool

Create new pool for token F and S using balance from `first_token` and `second_token`.

## add_liquidity\_

```rust
public entry fun add_liquidity_<F, S>(
    setting: &mut Setting,
    first_tokens: vector<Coin<F>>,
    second_tokens: vector<Coin<S>>,
    amount_first_desired: u64,
    amount_second_desired: u64,
    amount_first_min: u64,
    amount_second_min: u64,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `setting`: address of `Setting` shared object
-   `first_tokens`: vector of mutable references of token F to add into pool
-   `second_tokens`: vector of mutable references of token S to add into pool
-   `amount_F_desired`: expected/maximum amount of token F to add into pool
-   `amount_S_desired`: expected/maximum amount of token S to add into pool
-   `amount_F_min`: minimum amount of token F to add into pool
-   `amount_S_min`: minimum amount of token S to add into pool

Add liquidity into pool of token F and S using balance from `first_token` and `second_token`.

## remove_liquidity\_

```rust
public entry fun remove_liquidity_<F, S>(
    setting: &mut Setting,
    lsps: vector<Coin<LSP<F, S>>>,
    lsp_amount: u64,
    amount_first_min: u64,
    amount_second_min: u64,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `setting`: address of `Setting` shared object
-   `lsp`: mutable reference of liqudity token to redeem
-   `lsp_amount`: liquidity token amount to redeem
-   `amount_F_min`: minimum acceptable amount of token F to get
-   `amount_S_min`: minimum acceptable amount of token S to get

Redeem liquidity token to get back token F and S

## zap_in\_

```rust
public entry fun zap_in_<F, S>(
    setting: &mut Setting,
    input_tokens: vector<Coin<F>>,
    input_amount: u64,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `setting`: address of `Setting` shared object
-   `input_tokens`: vector of mutable references of token F to add into pool
-   `input_amount`: amount of token F out of `first_tokens` to add

Add liquidity into pool of token F and S using balance just from `first_tokens`.

## swap_exact_input\_

```rust
public entry fun swap_exact_input_<F, S>(
    setting: &mut Setting,
    input_tokens: vector<Coin<F>>,
    input_amount: u64,
    min_output_amount: u64,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `setting`: address of `Setting` shared object
-   `input_tokens`: vector of mutable references of token F to swap
-   `input_amount`: amount of token F out of `input_tokens` to swap
-   `min_output_amount`: minimum acceptable amount of token S to get

Swap an exact amount of token F to get token S out of pool

## swap_exact_output\_

```rust
public entry fun swap_exact_output_<F, S>(
    setting: &mut Setting,
    input_tokens: vector<Coin<F>>,
    output_amount: u64,
    max_input_amount: u64,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type

Parameters:

-   `setting`: address of `Setting` shared object
-   `input_tokens`: vector of mutable references of token F to swap
-   `output_amount`: exact output amount of token S to get
-   `max_input_amount`: maximum acceptable amount out of `input_tokens` to swap

Swap token F to get an exact amount of token S out of pool

## swap_exact_input_doublehop\_

```rust
public entry fun swap_exact_input_doublehop_<F, S, T>(
    setting: &mut Setting,
    input_tokens: vector<Coin<F>>,
    input_amount: u64,
    min_output_amount: u64,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type
-   `S`: third token type

Parameters:

-   `setting`: address of `Setting` shared object
-   `input_tokens`: vector of mutable references of token F to swap
-   `input_amount`: amount of token F out of `input_tokens` to swap
-   `min_output_amount`: minimum acceptable amount of token T to get

Swap an exact amount of token F to get token T out of pool with S as an intermediary token

## swap_exact_output_doublehop\_

```rust
public entry fun swap_exact_output_doublehop_<F, S, T>(
    setting: &mut Setting,
    input_tokens: vector<Coin<F>>,
    output_amount: u64,
    max_input_amount: u64,
    ctx: &mut TxContext
)
```

Type parameters:

-   `F`: first token type
-   `S`: second token type
-   `S`: third token type

Parameters:

-   `setting`: address of `Setting` shared object
-   `input_tokens`: vector of mutable references of token F to swap
-   `output_amount`: exact output amount of token T to get
-   `max_input_amount`: maximum acceptable amount out of `input_tokens` to swap

Swap token F to get an exact amount of token T out of pool with S as an intermediary token