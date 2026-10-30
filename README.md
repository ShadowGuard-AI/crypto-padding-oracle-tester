![Banner](banner.png)

# crypto-padding-oracle-tester
A tool to test a web server or cryptographic implementation for padding oracle vulnerabilities in CBC mode encryption. Sends crafted ciphertext to the server and analyzes the response to identify vulnerabilities. Relies on the `requests` library for HTTP interaction. - Focused on Basic cryptographic operations

## Install
`git clone https://github.com/ShadowStrikeHQ/crypto-padding-oracle-tester`

## Usage
```bash
python3 main.py -u <url> [--test_mode]
```

`--test_mode` is a dry run: it builds the ciphertext and walks the byte positions without sending any request, so it cannot produce a vulnerability verdict and the run ends by saying so. A live run reports "likely found" only when at least one byte position actually answered like a padding oracle. Invalid keys, IVs, ciphertext, or block sizes exit 1.

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
