# A stupid wrapper around GPG

This thing can

1. Add public keys to your keyring from a directory
1. Encrypt plaintext on STDIN with someone's public key and write the encrypted message to STDOUT
1. Decrypt a message encrypted with your public key on STDIN and write the plaintext to STDOUT

# Setup

We share everyone's public keys in a Dropbox folder. Set the
environment variable `GPG_PUBLIC_KEYS_DIR` to this directory and the
`add` command will load all keys found in that directory.

# Usage

Run without arguments for usage.
