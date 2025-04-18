#hello_world — Solana Smart Contract
A simple smart contract on the Solana blockchain demonstrating basic program interaction.

Description
This project provides a minimal "Hello World" program written in Rust for Solana. It can be compiled, tested, and deployed to a local solana-test-validator.

Requirements
Make sure you have the following installed:

Rust

Solana CLI tools

cargo-build-bpf: Install it using: cargo install --locked --git https://github.com/solana-labs/solana --tag v1.18.26 cargo-build-bpf

Project Setup
Create a .cargo/config.toml file in the root directory of the project with the following content:

[build]
target = "bpfel-unknown-unknown"

[profile.release]
opt-level = "z"
lto = true
codegen-units = 1
debug = false
overflow-checks = true
strip = true

Build the Program
Run the following command to build the smart contract:

cargo build-bpf

This will generate a .so file in target/deploy/.

Run Local Validator
To test the program locally, start the test validator:

solana-test-validator

Make sure it runs on http://127.0.0.1:8899.

Deploy the Program
Set your Solana CLI to use the local validator:

solana config set --url http://127.0.0.1:8899

Deploy the program:

solana program deploy ./target/deploy/hello_world.so

Project Structure
src/lib.rs: main program logic

Cargo.toml: project dependencies and metadata

.cargo/config.toml: custom build settings for Solana BPF

Useful Commands
solana address – show wallet address

solana airdrop 2 – request SOL tokens for testing

solana program show <PROGRAM_ID> – show program details

solana logs – view transaction logs from local validator

Author
Adilet, AITU

License
MIT License
