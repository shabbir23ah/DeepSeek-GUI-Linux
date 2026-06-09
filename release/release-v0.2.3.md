# DeepSeek GUI Linux v0.2.3

This release adds Linux-focused packaging for the personal DeepSeek GUI Linux fork.

> [!IMPORTANT]
> This is a personal project. Review the source code, build scripts, and packaged artifacts before installing or running it. The app can run local runtime processes and can access local workspaces depending on the permissions selected in the GUI.

## Linux Packages

- Added a `.deb` package for Debian-based distributions such as Debian, Ubuntu, Linux Mint, Pop!_OS, and Zorin OS.
- Kept the existing `.AppImage` format for portable use across Linux distributions.
- Added a portable `.tar.gz` archive for manual installs and custom distribution workflows.
- Updated the Linux release workflow so packages are built on Ubuntu and attached to GitHub Releases.
- Updated release publishing metadata so Linux release manifests can list `.deb`, `.AppImage`, and `.tar.gz` downloads.

## Install `.deb`

```bash
sudo apt install ./DeepSeek-GUI-0.2.3-linux-amd64.deb
```

Fallback:

```bash
sudo dpkg -i DeepSeek-GUI-0.2.3-linux-amd64.deb
sudo apt -f install
```

Uninstall:

```bash
sudo apt remove deepseek-gui
```

## Run `.AppImage`

```bash
chmod +x DeepSeek-GUI-0.2.3-linux-x86_64.AppImage
./DeepSeek-GUI-0.2.3-linux-x86_64.AppImage
```

Some distributions require FUSE support for AppImage files. On Debian/Ubuntu, install it with:

```bash
sudo apt install libfuse2
```

## Build From Source Tarball

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

Build individual package formats:

```bash
npm run dist:linux:deb
npm run dist:linux:appimage
npm run dist:linux:tar.gz
```

Generated packages are written to `dist/`.

## Notes

- This fork is not affiliated with DeepSeek Inc. or the upstream DeepSeek GUI maintainers.
- You need your own DeepSeek API key or compatible API endpoint after first launch.
- Removing the app package does not remove local data under `~/.config/DeepSeek GUI` or Kun runtime data under `~/.deepseekgui/kun`.
