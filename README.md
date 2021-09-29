# Open Source Summit 2021 Demo: Supply Chain Security Workflow

[![.github/workflows/build-and-publish.yaml](https://github.com/pvnovarese/oss-2021-sbom-complete-workflow-demo/actions/workflows/build-and-publish.yaml/badge.svg)](https://github.com/pvnovarese/oss-2021-sbom-complete-workflow-demo/actions/workflows/build-and-publish.yaml) [![.github/workflows/nightly.yaml](https://github.com/pvnovarese/oss-2021-sbom-complete-workflow-demo/actions/workflows/nightly.yaml/badge.svg)](https://github.com/pvnovarese/oss-2021-sbom-complete-workflow-demo/actions/workflows/nightly.yaml) [![Anchore Container Scan](https://github.com/pvnovarese/oss-2021-sbom-complete-workflow-demo/actions/workflows/anchore-analysis.yml/badge.svg)](https://github.com/pvnovarese/oss-2021-sbom-complete-workflow-demo/actions/workflows/anchore-analysis.yml)

Example repository that demonstrates a supply chain security workflow using Syft, Grype, Cosign

If you want to try this out yourself you need to do the following: 

1) Fork https://github.com/pvnovarese/example-ci and build it.  This will create an image with cosign, syft and grype.
2) take the image you just built and `docker run --rm -it pvnovarese/example-ci:latest sh -c "cosign generate-key-pair; cat cosign.*"` then add the private key and password as secrets in your forked repo (as `COSIGN_KEY` and `COSIGN_PASSWORD`) and save the public key in the root of your forked repo as `cosign.pub` (overwrite my public key).
3) Fork this repo and edit the .github/workflows/build-and-publish.yaml file - change the `image:` lines to your new example-ci image location and change the `docker login` line to use your username instead of mine.  Make the corresponding changes in the nightly.yaml action file, if desired.
4) There is no step 4.
