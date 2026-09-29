# layer-omarchy-gpu-nvidia

The Omarchy NVIDIA GPU stack as a charly layer — **machine-only, opt-in**, not yet
populated.

## Status

This repo is a **scaffold**: it carries this `README.md` and the org-wide
`.github/workflows/tag-on-merge.yml` dispatcher, and **no `charly.yml` or candy yet**.
There is no `candy/omarchy-gpu-nvidia/` to pin, and no image composes it. The scope
below is the intended role, recorded so the first candy lands against it.

## Intended scope

Omarchy is vanilla Arch + Hyprland, so the NVIDIA stack here is the host-side
driver, kernel-module and container-runtime wiring a real GPU machine needs — the
machine-only counterpart to the generic, distro-agnostic
`/charly-distros:nvidia-layer` runtime candy. It is opt-in: a machine with no
NVIDIA GPU does not compose it, and no pod does.

## How it is meant to be consumed

Once populated, a machine image composes the candy by pinning its sub-path in the
nested `candy:` list:

```yaml
my-omarchy-machine:
  candy:
    base: omarchy
    candy:
      - '@github.com/opencharly/layer-omarchy-base/candy/omarchy-base:v2026.242.0701'
      - '@github.com/opencharly/layer-omarchy-gpu-nvidia/candy/omarchy-gpu-nvidia:<tag>'
```

## Layout

- `README.md` — this user overview.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.

## Related

- Owning skill: none yet — `/charly-distros:nvidia-layer` is the closest family
  owning procedure (NVIDIA runtime, driver libs, CDI device injection). The missing
  `skill:` entity is recorded against
  [opencharly/opencharly#291](https://github.com/opencharly/opencharly/issues/291).
- `/charly-distros:omarchy` — the Omarchy base image.
- `/charly-distros:omarchy-base` — the foundation layer.
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella.
