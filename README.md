## Usage
```shell
pip3 install -r requirements.txt
python3 update_verifier.py lineageos_pubkey /path/to/update.zip
```

## Verification process
1. Install dependencies:

```shell
pip3 install -r requirements.txt
```

2. Run verification with the public key and the full path to the OTA ZIP:

```shell
python3 update_verifier.py lineageos_pubkey "C:\path\to\lineage-ota.zip"
```

3. Check the result:
   - `verified successfully` with exit code `0` means the signature is valid.
   - `failed verification` with exit code `1` means signature verification or ZIP structure checks failed.

## Local self-test with bundled fixtures
Use the included fixtures in `test_zips` to validate both success and failure behavior.

1. Expected success (signed ZIP + matching key):

```shell
python3 update_verifier.py test_zips/key test_zips/base.zip
```

Expected output includes:
- `verified successfully`
- Exit code `0`

2. Expected failure (unsigned ZIP):

```shell
python3 update_verifier.py test_zips/key test_zips/unsigned.zip
```

Expected output includes a traceback and:
- `failed verification`
- Exit code `1`

## Troubleshooting
- `FileNotFoundError`: the ZIP path is not valid. Use an existing absolute path.
- `InvalidSignature`: file exists but does not match `lineageos_pubkey`.
