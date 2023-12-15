# Table of Contents

- [Table of Contents](#table-of-contents)
  - [openssl](#openssl)
    - [Sign and verify](#sign-and-verify)
    - [Generate keys and CSR](#generate-keys-and-csr)
    - [Get information of CSR](#get-information-of-csr)

## openssl

### Sign and verify

Useful info at [Link](https://raymii.org/s/tutorials/Sign_and_verify_text_files_to_public_keys_via_the_OpenSSL_Command_Line.html)

Generate a keypair:

```shell
openssl req -nodes -x509 -sha256 -newkey rsa:4096 -keyout "$(whoami)s Sign Key.key" -out "$(whoami)s Sign Key.crt" -days 365 -subj "/C=NL/ST=Zuid Holland/L=Rotterdam/O=Sparkling Network/OU=IT Dept/CN=$(whoami)s Sign Key"
```

Sign the file

```shell
openssl dgst -sha256 -sign "$(whoami)s Sign Key.key" -out sign.txt.sha256 sign.txt
```

Getting public key from certificate

```shell
openssl x509 -in "$(whoami)s Sign Key.crt"
```

Verify the signature

```shell
openssl dgst -sha256 -verify  <(openssl x509 -in "$(whoami)s Sign Key.crt"  -pubkey -noout) -signature sign.txt.sha256 sign.txt
```

### Generate keys and CSR

```shell
openssl ecparam -name secp521r1 -genkey -noout -out ./key.private
openssl ec -in ./key.private -pubout -out ./key.public
openssl req -verbose -config csr.config -newkey ./key.private -out csr.request
```

### Get information of CSR

```shell
openssl req -in csr.request -text
```
