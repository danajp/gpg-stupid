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

Run without arguments for usage. Or just read this:

### add [DIR]

Adds all the keys in the directory specified by DIR to your gpg
keyring. If DIR is not passed, it's assumed to be the value of
`GPG_PUBLIC_KEYS_DIR`.

You need to run this before you can send/receive encrypted
messages.

Running this should always be safe. You'll automatically get new
people's keys and/or update keys that have changed.

### encrypt NAME

Encrypt STDIN for the person that matches NAME. NAME can be an
email address or someone's full name. GPG is smart about matching the
right user. Writes the encrypted message to STDOUT.

Example:

    echo "a secret message" | gpg-stupid encrypt

###  decrypt

Decrypts STDIN with your private key and outputs the decrypted
text to STDOUT.

Example:

    gpg-stupid decrypt < some-file-encrypted-with-my-public-key.txt
