# DeepSeek Harness — Installer and Source Preservation

**Repository Update: 13 October 2026**

This repository serves two purposes: **hosting and distributing installers for DeepSeek Harness**, and preserving an identifiable snapshot of the original DeepSeek Harness source code developed by DeepSeek AI.

## 🚀 DeepSeek Harness Installer — New Addition

A cross-platform **DeepSeek Harness Installer Kit (v1.0.2)** has been introduced to simplify downloading, installing, configuring, running, repairing, and uninstalling DeepSeek Harness without requiring users to perform the entire setup manually.

**📦 [Download DeepSeek Harness Installer Kit v1.0.2](https://github.com/AonzOG/deepseek-harness-d743267/blob/master/installers/DeepSeek-Harness-Installer-Kit-v1.0.2.zip)**

**Windows fix v1.0.2 (13 October 2026):** Corrects the Windows PowerShell 5.1 logging issue in which ordinary `git fetch` progress (such as `From https://github.com/...`) was treated as a terminating error. Native stdout/stderr is now logged while actual nonzero exit codes still fail the operation. **20 tests passed in the development environment; native Windows installation and application launch remain unverified.** [Previous installer v1.0.1](https://github.com/AonzOG/deepseek-harness-d743267/blob/master/installers/DeepSeek-Harness-Installer-Kit-v1.0.1.zip) is preserved for reference.

**Windows fix (13 October 2026):** Version 1.0.1 repairs `EPERM: operation not permitted, mkdir 'C:\\'` when installing to `C:\\deepseek-harness`. It avoids recreating an existing drive root and uses a user-writable, same-volume temporary staging directory where possible. The Node verification, source options, and build workflow are unchanged. [Installer v1.0](https://github.com/AonzOG/deepseek-harness-d743267/blob/master/installers/DeepSeek-Harness-Installer-Kit-v1.0.zip) remains available as the historical preview.

The installer provides three source-selection options:

1. **Official DeepSeek Repository:** https://github.com/deepseek-ai/deepseek-harness — Install from the original upstream project.
2. **Preserved Repository:** https://github.com/AonzOG/deepseek-harness-d743267 — Install from this repository, which preserves the identified upstream snapshot and hosts the installer.
3. **Custom Repository URL:** Paste the URL of another compatible public GitHub repository, including independent forks or imported copies of DeepSeek Harness.

The installer kit supports Windows, macOS, and Linux through platform-specific installation scripts and a shared installation engine. It provides source retrieval, dependency setup, application building, launching, and managed Repair and Uninstall operations.

**Development status:** The installer kit is an initial source-build preview. Native operating-system installation and application acceptance testing remain outstanding. It should not be confused with a signed, precompiled desktop installer.

## 📌 Preservation of the Original DeepSeek Harness Source Code

This repository also imports and preserves the original DeepSeek Harness source code at the following upstream Git commit:

**Original Repository:** https://github.com/deepseek-ai/deepseek-harness

**Preserved Commit ID:**
`d743267388641bc76f17c45ce8b4c231aed1d32c`

**Upstream Commit Date:** 9 October 2026, 09:31 UTC (9:31 PM Fiji Time)

**Upstream Version:** `v0.2.1-alpha.2`

**Original Commit:** https://github.com/deepseek-ai/deepseek-harness/commit/d743267388641bc76f17c45ce8b4c231aed1d32c

The preserved commit establishes a traceable historical baseline of the upstream project, allowing future development, modifications, bug fixes, security improvements, and installer updates to be distinguished from the original imported source.

The first installer package was subsequently added on 13 October 2026 under commit:

`7e5cc1e76402e21be1dd8916c32c46e7f719e4b7`

Consequently, this repository's current HEAD may differ from the preserved upstream commit while retaining that original commit in its Git history.

The original DeepSeek Harness source, attribution, and applicable licensing remain preserved. Installer development is maintained as an additional capability rather than a replacement of the upstream application.

---

**The original DeepSeek Harness README continues below, preserved for reference, technical documentation, and attribution.**

---

# DeepSeek Harness

English | [中文](README.zh.md)

DeepSeek Harness (`dsh`) is an open-source agent harness developed by [DeepSeek AI](https://deepseek.com).

It is built on an **everything-is-a-plugin** architecture and powered by [Cordis](https://github.com/cordiverse/cordis), whose design is described in [_A Programming Paradigm for Spatiotemporal Composability_](https://arxiv.org/abs/2608.25512).

Documentation: [https://deepseek-harness.github.io/deepseek-harness/](https://deepseek-harness.github.io/deepseek-harness/)

## Developer preview

DeepSeek Harness is in _developer preview_ and iterating rapidly. **THERE WILL BE COMPATIBILITY-BREAKING CHANGES.**

Review the [safety notice](SAFETY.md) before running the project.

## Run

### Run from `npm`

Install `Node.js`, then run:

```sh
npx @deepseek-ai/dsh web
```

The command starts the Web UI at `http://127.0.0.1:3080` by default and opens it in the default browser for a local launch. An SSH launch only prints the host URL because the SSH client or editor owns the local forwarded address. Pass `--no-open` to run the server without opening a browser. See [Web UI guide](docs/user/guide/index.md).

### Run from source

To run from a repository checkout:

```sh
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

`pnpm run build` prepares the repository artifacts. `pnpm dsh web` uses those built artifacts without rebuilding.

## Community and support

- Submit feedback or bug reports through [GitHub Discussions](https://github.com/deepseek-ai/deepseek-harness/discussions).
- Add the [`dsh-plugin`](https://github.com/topics/dsh-plugin) topic to your plugin repository for discoverability.
- Join <a href="https://discord.gg/4MrtZUhpxg">DeepSeek Harness Discord community</a>.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Development

Start with the [development guide](docs/development.md) and [architecture documentation](docs/architecture.md).

`pnpm run dev:web` builds, serves, and rebuilds client bundles on source edits in one terminal, and `make help` lists the matching Make targets for Web and Desktop; the guide's application commands section owns the full table.

For agents, follow [AGENTS.md](AGENTS.md).

## Citation

```bibtex
@misc{deepseek-harness2026,
  title={DeepSeek Harness: Everything is a Plugin},
  author={DeepSeek-AI},
  year={2026},
  publisher={GitHub},
  howpublished={\url{https://github.com/deepseek-ai/deepseek-harness}},
}
```

## License

[MIT](LICENSE)

Third-party dependencies and their licenses are disclosed in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
