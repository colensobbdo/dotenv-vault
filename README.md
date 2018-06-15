# dotenv-vault

simple dotenv encrypt tool inspired by yaml_vault

Default cipher is aes-256-cbc. Default sign digest is SHA256.

# Install

```
git clone https://github.com/acro5piano/dotenv-vault ~/.dotenv-vault
sudo ln -sfnv ~/.dotenv-vault/bin/dotenv-vault /usr/bin/dotenv-vault
```

dotenv-vault requires the following:

- Bash > 2
- Openssl > 2
- Perl > 5

Almost all machine does not need any installation process.

# Usage

## Encrypt

Input file (.env):

```
NODE_ENV=development
API_KEY=123456789 # encrypt-me
```

where `# encrypt-me` is the mark of the line dotenv-vault encrypt.

Command:

```
env DOTENV_VAULT_PASSPHRASE=foobarbaz dotenv-vault encrypt .env
```

Output:

```
NODE_ENV=development
API_KEY=U2FsdGVkX186T6zdupR27pXHO0Hdnz9rqZfVdgqBEqk= # decrypt-me
```

`# decrypt-me` will be used when decrypt the file.

## Decrypt

Input file (.env.encrypted):

```
NODE_ENV=development
API_KEY=U2FsdGVkX186T6zdupR27pXHO0Hdnz9rqZfVdgqBEqk= # decrypt-me
```

`# decrypt-me` is the mark of the line dotenv-vault decrypt.

Command:

```
env DOTENV_VAULT_PASSPHRASE=foobarbaz dotenv-vault decrypt .env.encrypted
```

Output:

```
NODE_ENV=development
API_KEY=123456789 # encrypt-me
```

# TODO

- [ ] Add auth methods
  - [ ] AWS KMS
  - [ ] GCP KMS
