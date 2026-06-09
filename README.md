# DeepSeek GUI Linux

DeepSeek GUI Linux is a personal Linux packaging fork of DeepSeek GUI. The goal of this repository is to make the desktop app easier to use on Linux by publishing `.deb`, `.AppImage`, and portable `.tar.gz` builds.

This project packages the existing DeepSeek GUI desktop application and its bundled Kun runtime. It is not affiliated with DeepSeek Inc. or the upstream DeepSeek GUI maintainers.

> [!IMPORTANT]
> This is a personal project. Review the source code, build scripts, and packaged artifacts before installing or running it on your machine. The app runs local runtime processes and can access local workspaces depending on the permissions you choose inside the GUI.

## Linux Packages

Release assets are published from the `v*` GitHub tags by the Ubuntu-based workflow in `.github/workflows/linux-packages.yml`.

| Package | Best For | Notes |
| --- | --- | --- |
| `.deb` | Debian, Ubuntu, Linux Mint, Pop!_OS, Zorin OS | Preferred package for Debian-based systems. Installs through the system package manager. |
| `.AppImage` | Most desktop Linux distributions | Portable executable. No system install required. |
| `.tar.gz` | Manual or custom installs | Portable archive. Extract it and run the bundled executable manually. |

Download packages from the [GitHub Releases](https://github.com/shabbir23ah/DeepSeek-GUI-Linux/releases) page.

## Install `.deb`

Use the `.deb` package on Debian-based systems.

```bash
sudo apt install ./DeepSeek-GUI-0.2.3-linux-amd64.deb
```

If your system does not support local `apt install`, use `dpkg` and then ask `apt` to fix missing dependencies:

```bash
sudo dpkg -i DeepSeek-GUI-0.2.3-linux-amd64.deb
sudo apt -f install
```

Launch the app from your desktop menu, or run:

```bash
deepseek-gui
```

Uninstall:

```bash
sudo apt remove deepseek-gui
```

## Run `.AppImage`

Use the AppImage when you want a portable build that does not install system files.

```bash
chmod +x DeepSeek-GUI-0.2.3-linux-x86_64.AppImage
./DeepSeek-GUI-0.2.3-linux-x86_64.AppImage
```

If your distribution requires FUSE support for AppImage files, install it through your package manager. On Ubuntu/Debian this is commonly:

```bash
sudo apt install libfuse2
```

To uninstall, delete the `.AppImage` file.

## Build From Source Tarball

Use this path if you want to inspect the code first or build your own Linux packages.

Requirements:

- Node.js 20+
- npm
- Git or a downloaded source `.tar.gz`
- Internet access for dependency installation
- A Linux build machine for `.deb`, `.AppImage`, and `.tar.gz` package output

Build from a GitHub source archive:

```bash
curl -L https://github.com/shabbir23ah/DeepSeek-GUI-Linux/archive/refs/tags/v0.2.3.tar.gz -o DeepSeek-GUI-Linux-v0.2.3.tar.gz
tar -xzf DeepSeek-GUI-Linux-v0.2.3.tar.gz
cd DeepSeek-GUI-Linux-0.2.3
npm ci
npm run typecheck
npm run test
npm run build
npm run dist:linux
```

Build only one Linux package type:

```bash
npm run dist:linux:deb
npm run dist:linux:appimage
npm run dist:linux:tar.gz
```

Generated packages are written to `dist/`.

## Development

Run the app locally:

```bash
npm ci
npm run dev
```

Validate changes:

```bash
npm run typecheck
npm run test
npm run build
```

Linux package scripts:

```bash
npm run dist:linux      # DEB + AppImage + portable tar.gz
npm run dist:linux:deb
npm run dist:linux:appimage
npm run dist:linux:tar.gz
```

## Runtime And Data

DeepSeek GUI uses the bundled Kun runtime. On first launch you will need your own DeepSeek API key or a compatible API endpoint.

Local app data is stored under:

```text
~/.config/DeepSeek GUI
```

Kun runtime data may also be stored under:

```text
~/.deepseekgui/kun
```

Removing the package does not automatically delete your local settings, sessions, runtime data, or workspace files.

## Upstream Project

This repository is based on DeepSeek GUI by XingYu-Zhong:

- Upstream repository: https://github.com/XingYu-Zhong/DeepSeek-GUI
- Upstream website: https://deepseek-gui.com

This Linux packaging fork keeps upstream functionality but focuses the release artifacts on Linux users.

## License

MIT. See [LICENSE](./LICENSE).
