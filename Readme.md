---
title: Readme
project: LinuxPathManager
created: 2025-02-25
---

# Linux Path Manager
**LinuxPathManager** JavaFX-based Linux desktop application to easily manage and edit system environment variables like PATH, JAVA_HOME, etc.
using a simple GUI. Ideal for developers, sysadmins, or Linux users who prefer a visual alternative.

This is a fork of [djaquels/LinuxPathManager](https://github.com/djaquels/LinuxPathManager).

## Local Development
### Build
mvn clean package
### Execute
mvn javafx:run

## Installation
### From source
Run the package script in the root directory:
```bash
./package.sh
```
this will generate a linuxpathmanager.deb file in the root directory. Therefore you can install it with:
```bash
sudo apt install ./linuxpathmanager.deb
```

## Features

- View and edit system environment variables (user and system level)
- Add, remove, and modify PATH entries
- Automatic detection of existing environment variables
- '.deb' package for easy installation (other Linux package managers pending)
- Remote (ssh) management of environment variables, for GUI server management

## License

MIT — see [LICENSE](LICENSE).

## Maintenance

This fork is maintained by AI coding agents; agent/model attribution is recorded in every commit and in doc history footers.

---
## Doc History
| Date       | Agent/Model           | Harness      | Change                     |
|------------|------------------------|--------------|----------------------------|
| 2026-09-28 | jainii/unsloth-qwen38  | DSH          | Fixed Local Development instructions (mvn clean package / mvn javafx:run); added header and Doc History |
| 2026-09-28 | jainii/unsloth-qwen38  | DSH          | Added fork note, License and Maintenance sections; removed PPA and Feedback sections; fixed typos and heading hierarchy |
---

