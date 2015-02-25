# Ssssh!

"ssssh" is a small tool that can be used to encrypt and decrypt secrets, using the AWS "Key Management Service" (KMS).

## Usage

Encrypt secrets like this:

    ssssh encrypt KEY-ID < secrets.txt > secrets.encrypted

Later, you can decrypt them:

    ssssh decrypt < secrets.encrypted > secrets.txt

KEY-ID must be the name or alias of an existing KMS key.

Naturally, suitable AWS credentials must be provided (via environment variables, command-line options, or EC2 instance profile).

## Limitations

"ssssh" can only encrypt small amounts of data; up to 4 KB.

## See also

If you'd rather install a Python interpreter than a Ruby one, secrets may also be decrypted using the AWS CLI.

    base64 -d < secrets.encrypted > /tmp/secrets.bin
    aws kms decrypt --ciphertext-blob fileb:///tmp/secrets.bin --output text --query Plaintext | base64 -d > secrets.txt
