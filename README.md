# julia-forge

Repackages official Julia binary releases as conda packages, built with
[rattler-build](https://github.com/prefix-dev/rattler-build) and published to
[prefix.dev](https://prefix.dev) channels.

Version tracking mirrors [juliaup](https://github.com/JuliaLang/juliaup)'s
channel model: `scripts/update_recipe.py` resolves a juliaup channel
(`release` or `lts`) to a concrete Julia version via juliaup's hosted
versiondb, and looks up the per-platform download URL/sha256 from the same
upstream `versions.json` juliaup's own version-db generator consumes.

The `julia/` recipe tracks juliaup's `release` channel and is published to
the `julia-forge` prefix.dev channel.

## Updating the recipe

```
pixi run update-recipe-release
```

This is a no-op if the recipe is already at the version the `release`
channel currently points to. `.github/workflows/update-recipe.yml` runs it
on a schedule and opens a PR when the channel has moved forward.
