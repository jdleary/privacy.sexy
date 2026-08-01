# TESLA-privacy — privacy.sexy fork for Windows 11 Pro

> Enforce privacy & security best-practices on Windows, macOS and Linux, because privacy is sexy.

## About this fork

This is a maintained fork of [privacy.sexy](https://github.com/undergroundwires/privacy.sexy) (via [Angry-Joe/privacy.sexy](https://github.com/Angry-Joe/privacy.sexy)), focused on **debloating and privacy-hardening Windows 11 Pro** machines. Upstream development stalled in April 2025; this fork updates the Windows script collection for current Windows 11 builds (24H2+).

### Fork changes (2026-07)

- **Fixed "Disable Recall"** — upstream wrote the `DisableAIDataAnalysis` policy to the pre-release `WindowsCopilot` registry key, which shipping Windows 11 24H2+ builds ignore. The script now writes the current `WindowsAI` policy key (keeping the legacy key for compatibility) and additionally sets `AllowRecallEnablement = 0`, the supported 24H2+ policy that blocks Recall entirely.
- **New script: "Disable Click to Do"** — disables the Copilot+ screen-capture/AI-analysis feature via the supported `DisableClickToDo` policy.
- **New Windows 11 app-removal scripts** (none existed upstream):
  - Microsoft Teams (`MSTeams`, the unified client — documented warning that work/school Teams uses the same package)
  - Microsoft Teams (personal) chat app (`MicrosoftTeams`, the legacy Windows 11 "Chat" app)
  - Clipchamp video editor
  - Dev Home (deprecated by Microsoft in 2025)
  - LinkedIn
- Validated against the project's own collection-parsing test suite (1,330 integration tests passing).

### Using this fork

There is no hosted instance of this fork. Run it locally to generate your script:

```bash
git clone https://github.com/Digital-Reign/TESLA-privacy.git
cd TESLA-privacy
npm run install-deps
npm run dev
```

Then open the printed localhost URL, choose **Standard** (safe debloat + privacy) or cherry-pick scripts, and download/run the generated `.bat` file **as administrator**. Review the generated script before running it — every entry documents what it does and how to revert it. The original project documentation below still applies.

---

<!-- markdownlint-disable MD033 -->
<p align="center">
  <a href="https://undergroundwires.dev/donate?project=privacy.sexy" target="_blank" rel="noopener noreferrer">
    <img
      alt="donation badge"
      src="https://undergroundwires.dev/img/badges/donate/flat.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/blob/master/CONTRIBUTING.md" target="_blank" rel="noopener noreferrer">
    <img
      alt="contributions are welcome"
      src="https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat"
    />
  </a>
  <a href="https://codeclimate.com/github/undergroundwires/privacy.sexy/maintainability" target="_blank" rel="noopener noreferrer">
    <img
      alt="Maintainability"
      src="https://api.codeclimate.com/v1/badges/3a70b7ef602e2264342c/maintainability"
    />
  </a>
  <!-- Tests -->
  <br />
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/tests.unit.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Unit tests status"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/unit-tests/badge.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/tests.integration.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Integration tests status"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/integration-tests/badge.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/tests.e2e.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="E2E tests status"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/e2e-tests/badge.svg"
    />
  </a>
  <!-- Security checks -->
  <br />
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/checks.security.sast.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Status of dependency security checks"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/checks.security.sast/badge.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/checks.security.dependencies.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Status of Static Analysis Security Testing (SAST)"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/checks.security.dependencies/badge.svg"
    />
  </a>
  <!-- Checks -->
  <br />
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/checks.quality.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Status of quality checks"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/checks.quality/badge.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/checks.build.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Status of build checks"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/checks.build/badge.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/checks.desktop-runtime-errors.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Status of runtime error checks for the desktop application"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/checks.desktop-runtime-errors/badge.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/checks.scripts.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Status of script checks"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/checks.scripts/badge.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/checks.external-urls.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Status of external URL checks"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/checks.external-urls/badge.svg"
    />
  </a>
  <!-- Release -->
  <br />
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/release.git.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Git release status"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/release-git/badge.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/release.site.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Site release status"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/release-site/badge.svg"
    />
  </a>
  <a href="https://github.com/undergroundwires/privacy.sexy/actions/workflows/release.desktop.yaml" target="_blank" rel="noopener noreferrer">
    <img
      alt="Desktop application release status"
      src="https://github.com/undergroundwires/privacy.sexy/workflows/release-desktop/badge.svg"
    />
  </a>
  <!-- Others -->
  <br />
  <a href="https://github.com/undergroundwires/bump-everywhere" target="_blank" rel="noopener noreferrer">
    <img
      alt="Auto-versioned by bump-everywhere"
      src="https://github.com/undergroundwires/bump-everywhere/blob/master/badge.svg?raw=true"
    />
  </a>
</p>
<!-- markdownlint-restore -->

## Get started

- 🌍️ **Online**: [https://privacy.sexy](https://privacy.sexy).
- 🖥️ **Offline**: Download directly for: [Windows](https://github.com/undergroundwires/privacy.sexy/releases/download/0.13.8/privacy.sexy-Setup-0.13.8.exe), [macOS](https://github.com/undergroundwires/privacy.sexy/releases/download/0.13.8/privacy.sexy-0.13.8.dmg), [Linux](https://github.com/undergroundwires/privacy.sexy/releases/download/0.13.8/privacy.sexy-0.13.8.AppImage). For more options, see [here](#additional-install-options).

See also:

- [Desktop vs. Web Features](./docs/desktop/desktop-vs-web-features.md): Differences and unique aspects of desktop and web versions.
- [System Requirements](./docs/desktop/system-requirements.md): Hardware and software requirements for the desktop version.

💡 Regularly applying your configuration with privacy.sexy is recommended, especially after each new release and major operating system updates. Each version updates scripts to enhance stability, privacy, and security.

[![privacy.sexy application](img/screenshot.png?raw=true )](https://privacy.sexy)

## Features

- **Rich**: Hundreds of scripts that aims to give you control of your data.
- **Free**: Both free as in "beer" and free as in "speech".
- **Transparent**. Have full visibility into what the tweaks do as you enable them.
- **Reversible**. Revert if something feels wrong.
- **Accessible**. No need to run any compiled software on your computer with web version.
- **Secure**: Security is a top priority at privacy.sexy with [comprehensive safeguards](./SECURITY.md#security-practices) in place.
- **Open**. What you see as code in this repository is what you get. The application itself, its infrastructure and deployments are open-source and automated thanks to [bump-everywhere](https://github.com/undergroundwires/bump-everywhere).
- **Tested**. A lot of tests. Automated and manual. Community-testing and verification. Stability improvements comes before new features.
- **Extensible**. Effortlessly [extend scripts](./CONTRIBUTING.md#extend-scripts) with a custom designed [templating language](./docs/templating.md).
- **Portable and simple**. Every script is independently executable without cross-dependencies.

## Support

**Sponsor 💕**. Consider sponsoring on [GitHub Sponsors](https://github.com/sponsors/undergroundwires), or you can donate using [other ways such as crypto or a coffee](https://undergroundwires.dev/donate).

**Star 🤩**. Feel free to give it a star ⭐ .

**Contribute 👷**. Contributions of any type are welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md) as the starting point. It includes useful information like [how to add new scripts](./CONTRIBUTING.md#extend-scripts).

## Additional Install Options

- Check the [releases page](https://github.com/undergroundwires/privacy.sexy/releases) for all available versions.
- Other unofficial channels (not maintained by privacy.sexy) for Windows include:
  - [Scoop 🥄](https://scoop.sh/#/apps?q=privacy.sexy&s=2&d=1&o=true) (latest version):

    ```powershell
      scoop bucket add extras
      scoop install privacy.sexy
    ```

  - [winget 🪟](https://winget.run/pkg/undergroundwires/privacy.sexy) (may be outdated):

    ```powershell
      winget install -e --id undergroundwires.privacy.sexy
    ```

    With winget, updates require manual submission; the auto-update feature within privacy.sexy will notify you of new releases post-installation.

## Development

Refer to [development.md](./docs/development.md) for Docker usage and reading more about setting up your development environment.

Check [architecture.md](./docs/architecture.md) for an overview of design and how different parts and layers work together. You can refer to [application.md](./docs/application.md) for a closer look at application layer codebase and [presentation.md](./docs/presentation.md) for code related to GUI layer. [collection-files.md](./docs/collection-files.md) explains the YAML files that are the core of the application and [templating.md](./docs/templating.md) documents how to use templating language in those files. In [ci-cd.md](./docs/ci-cd.md), you can read more about the pipelines that automates maintenance tasks and ensures you get what see.

[docs/](./docs/) folder includes all other documentation.

## Security

Security is a top priority at privacy.sexy.
An extensive commitment to security verification ensures this priority.
For any security concerns or vulnerabilities, please consult the [Security Policy](./SECURITY.md).

## Supporters

[![Supporters appreciation banner showing the supporters](https://undergroundwires.dev/img/supporters.jpg)](https://undergroundwires.dev/supporters)
