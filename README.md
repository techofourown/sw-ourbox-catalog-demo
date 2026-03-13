# sw-ourbox-catalog-demo

`sw-ourbox-catalog-demo` is the first concrete multi-source OurBox application
catalog repo.

It consumes published images from more than one `sw-ourbox-apps-*` repo and
combines them with pinned third-party images into one installer-selectable
catalog bundle.

## Consumed application images

From `sw-ourbox-apps-demo`:

- `ghcr.io/techofourown/sw-ourbox-apps-demo/landing@sha256:5f288e2a4158d2a6ba45b119c5ae2c059d8d2ab555d30ae3e0d51906679e2e3c`
- `ghcr.io/techofourown/sw-ourbox-apps-demo/todo-bloom@sha256:c67ad365ad1f880c42fac9a9cfe4375187b3b721a2be4768719f7782298ea20a`

From `sw-ourbox-apps-hello-world`:

- `ghcr.io/techofourown/sw-ourbox-apps-hello-world/hello-world@sha256:d29428789d671b9405ab202413f5eff4d2fb4870f80791050430bce24ccac2d6`

Pinned third-party images:

- `docker.io/sigoden/dufs@sha256:2d1070cab68881111caf367136a6a10fc9c8353b548d4429c0b2e250d45a0b0b`
- `docker.io/dullage/flatnotes@sha256:abb3dd864a06aaca3a900d9c43be608765ce42a562c7b2592b637eda155bb0bc`

## What this proves

- one application catalog can consume published images from multiple apps repos
- the catalog repo is distinct from the apps repos
- the catalog bundle can carry both first-party and third-party application
  image selections
