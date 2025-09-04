# Decentralized Identity Protocol Experiment Suite

This folder contains the benchmarking scripts for evaluating and comparing the performance of four decentralized identity protocols:

- **Quadrata**
- **Verite**
- **Holonym**
- **Privado ID**

Each experiment uses a shared dataset (`transactions.json`) to run multiple identity-related operations such as credential issuance, verification, and proof lookups, while measuring the time and success rate of each process.


## 📂 Input File: `transactions.json`

All experiments require a shared input file in the following format:

```json
[
  {
    "id": "tx_001",
    "wallet_address": "0xAb5801a7D398351b8bE11C439e05C5B3259aeC9B",
    "holder_did": "did:polygonid:polygon:amoy:2qH1ZqV8ZgY5cSAMPLE",
    "birthday": "1991-05-20",
    "documentType": 1
  }
]
```

# How to Run Experiments
Make sure you have installed all dependencies listed in requirements.txt and have configured .env in the root directory.

## Quadrata
Query decentralized identity attributes from Quadrata for each wallet.

python quadrata_run.py transactions.json

## Verite
Issue and verify VC-JWT credentials locally for each entry (fully offline).


python verite_run.py transactions.json

## Holonym
Verify if each wallet in the list has a valid Holonym uniqueness or residency proof.

python holonym_run.py transactions.json

## Privado ID
Create a credential for each holder DID using your local or remote Privado Issuer Node.

python privado_run.py transactions.json

## Output

Number of successful operations

Number of failures

Total execution time

Per-record tracking

# Notes
Each protocol handles identity issuance and verification differently; 
the time costs and failure rates may vary significantly.

Network/API-based scripts (e.g. Quadrata, Holonym, Privado) require valid keys and server availability.
Verite runs fully locally and is useful as a reference benchmark.

