# WBA Cohort 3 Enrollment Script

## Introduction

This is an Enrollment dApp (script) written in Rust, designed to help a student (me) enroll for the WBA Cohort 3 program.

The wba-wallet.json and dev-wallet.json contains the scret keys to the WBA registered wallet address and the Keypair generated address respectively.

## Test

The following guide includes what each function in lib.rs does;

- keygen: Generates a new Solana wallet and prints the public key and the wallet in byte format.

- Helper functions

  - base58_to_wallet takes a base58 encoded private key from the user, decodes it, and prints the corresponding wallet file
  - wallet_to_base58 takes a wallet file byte array from the user, encodes it into base58, and prints the corresponding private key respectively

- airdrop: Reads a keypair from the dev-wallet, connects to the Solana Devnet RPC client, and requests an airdrop of 2 SOL tokens.

- transfer: Reads a keypair from the dev-wallet, connects to the Solana Devnet RPC client, gets the recent blockhash and balance of the wallet, calculates the transaction fee, creates a transaction to transfer the balance minus the fee to a specific public key (WBA registered address), sends the transaction, and prints the transaction URL.

- enroll: Connects to the Solana Devnet RPC client, reads a keypair from a file, derives a program address, creates a transaction to invoke the "complete" function of the WbaPrereqProgram with a valid GitHub username as argument, sends the transaction, and prints the transaction URL.

- update_enrollment: Similar to enroll, but invokes the "update" function of the WbaPrereqProgram instead, to update enrollment information.

To test this enrollment script, follow these steps:

\*Ensure to have Rust and Cargo installed on your machine

1. Clone the repository:

   ```bash
   git clone https://github.com/Jonnie-Dev/WBA_Cohort-3_Enrollment-script__Typescript.git
   ```

2. Install the dependencies:

   ```bash
   cd WBA_Cohort-3_Enrollment-script__Typescript
   cargo build
   ```

3. Update the `wba-wallet.json` and `dev-wallet.json` files with your secret keys.

4. To test any of the functions:

   ```bash
   cargo test {fn name} -- --nocapture
   ```

5. Follow the prompts to test the enrollment script for the WBA Cohort 3 program.
