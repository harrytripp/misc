| APT command | DNF command | Notes |
|-------------|------------|-------|
| `apt install` / `apt-get install` | `dnf install` | Of course, actual package names may vary. For example, `libc6-dev` on Debian maps to `glibc-devel` in the Fedora universe. |
| `apt install --only-upgrade package` | `dnf update package` | Updates only already installed package and its dependencies. The `apt install` works for both install and upgrade of a single package if already installed. |
| `apt update` / `apt-get update` | `dnf check-update` | This command is rarely needed, as `dnf` updates its package cache automatically when it is stale. A cache update can be forced by appending `--refresh` to other commands, e.g., `dnf upgrade --refresh`. |
| `apt upgrade` / `apt-get upgrade` | `dnf upgrade` | Note that while `apt update` does something different, `dnf update` and `dnf upgrade` are synonyms. You can also use the shorter `dnf up`. |
| `apt full-upgrade` / `apt-get dist-upgrade` | `dnf distro-sync` or `dnf system-upgrade` (see note) | While `distro-sync` is the most direct functional equivalent, `dnf system-upgrade` should be used to upgrade from one release to another, e.g., from Fedora Linux 34 to 35. This is a multi-step process as described in Fedora documentation. |
| `apt remove` / `apt-get remove` | `dnf remove` |  |
| `apt purge` / `apt-get purge` | --- | Fedora packages don’t treat configuration files in the same way as Debian packages, so there is no direct equivalent. |
| `apt autoremove` / `apt-get autoremove` | `dnf autoremove` | Note that this can occasionally remove packages that you might actually want. Use `dnf mark` to flag packages to keep. |
| `apt search` / `apt-cache search` | `dnf search` | `dnf repoquery` is useful for advanced searches. |

## Additional Resources
- [DNF vs APT Comparison](https://docs.fedoraproject.org/en-US/quick-docs/dnf-vs-apt/)
- [Fedora DNF Documentation](https://docs.fedoraproject.org/en-US/quick-docs/dnf/)
- [DNF Command Reference](https://dnf.readthedocs.io/en/latest/command_ref.html#dnf-command-reference)
