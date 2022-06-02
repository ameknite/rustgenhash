# rustgenhash

rustgenhash is a tool to generate hashes on the commandline from stdio.

It can be used to generate single or multiple hashes for usage in password databases or even in penetration testing scenarios where you want to test password cracking tools.

## Install

rustgenhash is written in Rust. You can install the tool with your Rust installation using following command:

```bash
cargo install rustgenhash
```

## Usage

Rustgenhash has a command line interface which allows you to set the utility into a specific operating mode. The current
modes are

- stdio
- string
- file

After selecting the mode you will need to provide the -a switch for selecting a suitable hashing algorithm and a string
or file to be hashed. The stdio mode allows you to pipe to the `rustgenhash` command. The tool will hash the passed
lines from the stdio (useful for hashing password lists).

The file mode supports hashing of multiple files in a directory and currently works non-recursive.

Scheme for string hashing:

```bash
rustgenhash string -a <algorithm> <string>
```

Scheme for file hashing:

```bash
rustgenhash file -a <algorithm> <filename or directory>
```

Scheme for string hashing from stdio:

```bash
cat myfile | rustgenhash stdio -a <algorithm>
```

```bash
echo "mypassword" | rustgenhash stdio -a <algorithm>
```

You can list all algorithms over the help function.

Supported are:

- Argon2 (Only String and stdio)
- BLAKE2b
- BLAKE2s
- GOST R 34.11-94
- GOST 34.311-95 UA
- Grøstl
- MD2 hash
- MD4 hash
- MD5 hash
- PBKDF2-SHA256 (Only String and stdio)
- PBKDF2-SHA512 (Only String and stdio)
- RipeMD160
- RipeMD320
- Scrypt (Only String and stdio)
- SHA-1 hash
- SHA2-224 hash
- SHA2-256 hash
- SHA2-384 hash
- SHA2-512 hash
- SHA3-224 hash
- SHA3-384 hash
- SHA3-256 hash
- SHA3-512 hash
- Shabal192
- Shabal224
- Shabal256
- Shabal384
- Shabal512
- Sm3
- Streebog256
- Streebog512
- Tiger (Only String and stdio)
- Whirlpool


Generate shell completions:

```bash
rustgenhash generate-completions <SHELL> > some_path
```

Supported shells: bash, elvish, fish, power-shell, zsh
