# rpm-ostree-rechunker-test &nbsp; [![bluebuild build badge](https://github.com/synby/rpm-ostree-rechunker-test/actions/workflows/build.yml/badge.svg)](https://github.com/synby/rpm-ostree-rechunker-test/actions/workflows/build.yml)

this is a test image for using rpm-ostree build-chunked-oci as a replacement for hhd-dev/rechunk.
this is not meant for general use. it is just to make sure people can boot the system properly after switching rechunkers

## Testing

To test this image:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  sudo bootc switch ghcr.io/synby/rpm-ostree-rechunker-test:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Once you have confirmed whether or not the image boots properly, rollback to your previous image:
  ```
  sudo bootc rollback
  ```
- Reboot to complete the rollback:
  ```
  systemctl reboot
  ```

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/synby/rpm-ostree-rechunker-test
```
