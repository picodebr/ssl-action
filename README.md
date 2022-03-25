# PiCode SSL generator

Issuance and renewal of SSL certificates.

_Note: This is meant to be used on an Ubuntu machine version 20.04.03 or newer._

## Usage

```yml
- uses: picodebr/ssl-action@v1
  with:
    # remote server private ssh key (required)
    ssh_key: ""

    # remote server username (required)
    ssh_user: ""

    # remote server address (required)
    ssh_host: ""

    # URL address to emit ssl certificate
    certificate_address: ""

    # email from address owner
    email: ""
```

## Example

The following example shows how to emit a ssl certificate in remote machine with.

```yml
name: Generate SSL certificate

on:
  push:
    branches: [master]

jobs:
  main:
    runs-on: ubuntu-latest
    steps:
      - name: Emit certificate in remote machine
        uses: picodebr/ssl-action@v1
        with:
          ssh_key: ${{ secrets.SSH_KEY }}
          ssh_user: ${{ secrets.SSH_USER }}
          ssh_host: ${{ secrets.SSH_HOST }}
          certificate_address: ${{ secrets.SSL_CERTIFICATE_ADDRESS }}
          email: ${{ secrets.SSL_CERTIFICATE_EMAIL }}
```
