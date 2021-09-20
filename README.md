# example-container-image-supply-chain-security

Example repository that demonstrates a supply chain security workflow using Syft, Grype, Cosign

If you want to try this out yourself you need to do the following:

1) Fork https://github.com/pvnovarese/example-ci and build it.  This will create an image with cosign, syft and grype.
2) take the image you just built and `docker run --rm $EXAMPLE-CI-IMAGE cosign generate-key-pair` then add the private key and password as secrets in your forked repo (as `COSIGN_KEY` and `COSIGN_PASSWORD`) and save the public key in the root of your forked repo as `cosign.pub` (overwrite my public key).
3) Fork this repo and edit the .github/workflows/build-and-publish.yaml file - change the `image:` lines to your new example-ci image location.
4) There is no step 4.
