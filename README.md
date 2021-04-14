# SecretSwap

SecretSwap is the first front-running resistant, cross-chain and privacy first automated market-maker (AMM) protocol powered by Secret Contracts on the [Secret Network](https://scrt.network) blockchain.

Built on the principles of usability and privacy, SecretSwap provides a foundation for the open accessible financial system of the future. Our primary focus is to protect our users from value extracting players by focusing on privacy, a basic human right. SecretSwap is a liquidity hub that connects to other ecosystems for maximum user protection and access to assets.

## Contracts

| Name                                               | Description                                  |
| -------------------------------------------------- | -------------------------------------------- |
| [`secretswap_factory`](contracts/secretswap_factory) |                                              |
| [`secretswap_pair`](contracts/secretswap_pair)       |                                              |
| [`terraswap_token`](contracts/terraswap_token)     | CW20 (ERC20 equivalent) token implementation |

## Running this contract

You will need Rust 1.44.1+ with wasm32-unknown-unknown target installed.

You can run unit tests on this on each contracts directory via :

```
cargo unit-test
cargo integration-test
```

Once you are happy with the content, you can compile it to wasm on each contracts directory via:

```
RUSTFLAGS='-C link-arg=-s' cargo wasm
cp ../../target/wasm32-unknown-unknown/release/cw1_subkeys.wasm .
ls -l cw1_subkeys.wasm
sha256sum cw1_subkeys.wasm
```

Or for a production-ready (compressed) build, run the following from the repository root:

```
docker run --rm -v "$(pwd)":/code \
  --mount type=volume,source="$(basename "$(pwd)")_cache",target=/code/target \
  --mount type=volume,source=registry_cache,target=/usr/local/cargo/registry \
  cosmwasm/workspace-optimizer:0.10.2
```

The optimized contracts are generated in the artifacts/ directory.
