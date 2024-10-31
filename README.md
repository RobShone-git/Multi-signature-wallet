# Multi-Signature Wallet Contract

## Overview

This project implements a Multi-Signature Wallet contract in Solidity, enabling multiple owners to collectively manage and authorize transactions. The wallet requires a predefined number of confirmations from the owners before executing any transaction, enhancing security and accountability.

## Features

- Multiple owners can submit and confirm transactions.
- A transaction requires a minimum number of confirmations from owners to execute.
- Supports fund deposits and keeps track of the contract's balance.

## Smart Contract Details

### Contract Name: `Wallet`

#### State Variables:
- `address owner1, owner2, owner3`: Addresses of the wallet owners.
- `uint numConfirmationsNeeded`: Number of confirmations required to execute a transaction.
- `Transaction[] transactions`: Array to store transaction details.
- `mapping(uint => mapping(address => bool)) isConfirmed`: Mapping to track confirmations for each transaction.

#### Struct:
- `Transaction`: Represents a transaction, including:
  - `address to`: Recipient address.
  - `uint amount`: Amount to be transferred.
  - `bool executed`: Status of the transaction (executed or not).
  - `uint numConfirmations`: Number of confirmations received.

#### Functions:
- `Deposit`: Allows users to deposit funds into the wallet.
- `receive()`: Fallback function to receive Ether.
- `submitTransaction(address to, uint amount)`: Allows an owner to propose a transaction.
- `confirmTransactions(uint index)`: Allows an owner to confirm a transaction.
- `executeTransaction(uint index)`: Executes a transaction if the required confirmations are met.
- `getBalance()`: Returns the current balance of the wallet.

