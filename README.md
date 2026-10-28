<div align="center">

<img src="snap/gui/llmfit.png" alt="llmfit logo" width="128" />

# llmfit

**Find language models that fit your hardware**

[![llmfit](https://snapcraft.io/llmfit/badge.svg)](https://snapcraft.io/llmfit)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [llmfit](https://github.com/AlexsJones/llmfit), a terminal tool for comparing language models against your CPU, RAM and GPU capacity.

</div>

---

## Getting Started

<a href="https://snapcraft.io/llmfit"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install llmfit
sudo snap connect llmfit:hardware-observe
sudo snap connect llmfit:system-observe
llmfit
```

Use `llmfit recommend --json` for scripting, or `llmfit serve` for the web dashboard at <http://localhost:8787>.

## Configure

There are no `snap set` options. Use `llmfit --help` and the [upstream documentation](https://github.com/AlexsJones/llmfit/blob/main/docs/cli.md) for application settings.

Settings are stored in `~/snap/llmfit/current/.config/llmfit`. Models and cached data persist under `~/snap/llmfit/common`. To access models on removable storage:

```bash
sudo snap connect llmfit:removable-media
```

## Limitations

- GPU detection uses PCI and kernel information. NVIDIA VRAM may be estimated, and vendor-specific accelerator detection is unavailable; use `--memory` or `--profile` when needed.
- Connect to inference servers over HTTP. Launching host tools such as `llama-server`, Docker and RamaLama is not supported; inference runtimes are not bundled.
- Hidden host folders such as `~/.cache/huggingface` and `~/.lmstudio` are not accessible. Use an accessible model directory or the provider's HTTP API.

## Build

```bash
git clone https://github.com/sidalit/llmfit-snap.git
cd llmfit-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/llmfit-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/AlexsJones/llmfit/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/llmfit-snap/blob/main/LICENSE).
