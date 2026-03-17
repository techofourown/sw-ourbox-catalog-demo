# sw-ourbox-catalog-demo

`sw-ourbox-catalog-demo` is the first concrete multi-source OurBox application
catalog repo.

It consumes published images from more than one `sw-ourbox-apps-*` repo and
combines them with pinned third-party images into one installer-selectable
catalog bundle.

The authoring surface is:

- `catalog/catalog.json`
- `catalog/image-sources.json`
- `catalog/profile.env`

`images.lock.json` is generated at publish time into `dist/images.lock.json`
and packed into the published catalog bundle. It is not the checked-in source
of truth.

## Consumed application images

From `sw-ourbox-apps-demo`:

- `ghcr.io/techofourown/sw-ourbox-apps-demo/landing:latest`
- `ghcr.io/techofourown/sw-ourbox-apps-demo/todo-bloom:latest`

From `sw-ourbox-apps-hello-world`:

- `ghcr.io/techofourown/sw-ourbox-apps-hello-world/hello-world:latest`

Pinned third-party images:

- `docker.io/sigoden/dufs@sha256:2d1070cab68881111caf367136a6a10fc9c8353b548d4429c0b2e250d45a0b0b`
- `docker.io/dullage/flatnotes@sha256:abb3dd864a06aaca3a900d9c43be608765ce42a562c7b2592b637eda155bb0bc`

## Platform contract binding

Published bundles carry `OURBOX_PLATFORM_CONTRACT_DIGEST` in `manifest.env`.
That lets host-side installers reject catalog bundles that do not match the
selected OS payload contract.

This repo also publishes installer-browsable catalog rows at
`ghcr.io/techofourown/sw-ourbox-catalog-demo:catalog-amd64`. Those rows let
host-side installers resolve the newest stable bundle whose
`OURBOX_PLATFORM_CONTRACT_DIGEST` matches the selected OS payload contract,
without hardcoding a floating bundle ref in downstream consumers.

## What this proves

- one application catalog can consume published images from multiple apps repos
- the catalog repo is distinct from the apps repos
- the catalog bundle can carry both first-party and third-party application
  image selections
