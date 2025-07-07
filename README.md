# nix-arcdps-rs-example

Zerthox's arcdps_example_addon, but with Nix!

## Usage

```shell
# Build addon
nix build .#example

# Development shell
nix develop .#
# Build inside development shell
cargo build

# Regenerate GitHub actions from changed ci.nix
CI_PLATFORM=impure nix run -f https://github.com/arcnmx/ci/archive/v0.7.tar.gz run.gh-actions-generate --arg config ./ci.nix
```

## Package variants (e.g. features)

package.nix supports a `features` parameter. If you define a package with features, you can use the variant in both the outputs and within CI to provide builds with certain features.
```nix
exampleWithFeatures = pkgs.callPackage ./package.nix {
  craneLib = packageCraneLib;
  features = [ "lots-of-spaghetti" ];
};
```
