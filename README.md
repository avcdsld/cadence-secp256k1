# cadence-secp256k1

## What is this?

This is Cadence code for deriving the public key from the private key of secp256k1, an elliptic curve cipher supported by Flow, which I wrote while thinking about artwork using smart contracts.

\*\* Note: If you use your private key in a transaction or script, that information can be seen by anyone. Please note that this is experimental code.

## How to execute

```bash
# Start Flow emulator with a large number of script-gas-limit
$ flow emulator --script-gas-limit 50000000 -v

# Run Script
$ flow scripts execute derive_pubkey.cdc

Result: [38208218050791198729387617835299853067161242025442387890993127275107396836275, 56329139950494731794597997330565495437565330265019475362592518784333160021470]

INFO[0016] ⭐  Script executed                            computationUsed=17606218 scriptID=2bab5f0281ced63b7cc7c57a3e5df0f019ef45ff7e65a0121d1883e81fd1c747
```

## Issue

The Cadence language does not have the addmod and mulmod built-in functions, so you have to write these yourself. However, Cadence does not allow overflows to occur, so the amount of these calculations is enormous. Therefore, due to the computational limitations, this Cadence code cannot actually be executed on the Flow mainnet/testnet.

Adding addmod and mulmod as built-in functions for Cadence is the easiest way around this problem, but how much use case and value there is in this is open to consideration.

## Acknowledgements

- [`elliptic-curve-solidity`](https://github.com/witnet/elliptic-curve-solidity) by The Witnet Project
- [`mulmod` and `addmod` logics without overflow](https://gist.github.com/camlspotter/5ea3c95e89920072667b766a2aba7a57) by camlspotter
