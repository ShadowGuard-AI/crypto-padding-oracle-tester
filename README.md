![Banner](banner.png)

# crypto-padding-oracle-tester
A tool to test a web server or cryptographic implementation for padding oracle vulnerabilities in CBC mode encryption. Sends crafted ciphertext to the server and analyzes the response to identify vulnerabilities. Relies on the `requests` library for HTTP interaction. - Focused on Basic cryptographic operations

## Install
`git clone https://github.com/ShadowStrikeHQ/crypto-padding-oracle-tester`

## Usage
```bash
python3 main.py -u <url> [--test_mode]
```

`--test_mode` is a dry run: it builds the ciphertext and walks the byte positions without sending any request, so it cannot produce a vulnerability verdict and the run ends by saying so. A live run first sends a baseline request with the unmodified ciphertext and records the response. It reports "likely found" only when at least one byte position shows distinguishing evidence: at that position, at least one byte value answered without the error string while other byte values at the same position answered with it. A server whose answers never vary with the ciphertext cannot be reported as likely found. An HTTP error status is read as a response and checked for the error string like any other answer. Invalid keys, IVs, ciphertext, or block sizes exit 1. A run also exits 1 when the ciphertext length is not a multiple of the block size, when the ciphertext holds fewer than two blocks, or when a request fails at the transport level (connection error or timeout). The "not detected" line and exit 0 are reserved for runs that completed the byte loop without oracle evidence.

## Parameters
- `-h`: Show help message and exit
- `-u`: The URL to test for the padding oracle vulnerability.
- `-d`: No description provided
- `-c`: No description provided
- `-k`: No description provided
- `-iv`: No description provided
- `-p`: No description provided
- `-e`: No description provided
- `--block_size`: No description provided
- `--get`: Use GET request instead of POST.
- `--test_mode`: Enable test mode to not send any requests to the server

## License
Copyright (c) ShadowStrikeHQ
