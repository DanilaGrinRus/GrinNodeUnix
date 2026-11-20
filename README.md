# GrinNodeUnix

Prebuilt **Grin 5.5.2** node binaries for 17 Linux releases, built from PR
branch `header-proof-hist` (commit `cabfd8b5`). Each release archive contains:

```text
grin          node binary
run-node.sh   launcher that creates the config on first start
README.md     release-specific launch, build and hardware notes
```

## Recommendation: Debian

If you do not have a reason to choose another distribution, use
**Debian 12**. It has the widest package availability, predictable upgrades
and was the reference Linux build used for the node runs here. The other
releases are provided for compatibility with existing systems.

This is a practical recommendation, not a claim that Debian is fastest in
every benchmark. Glibc/distro compatibility matters: use the archive that
matches your release.

## Releases

| Release | GitHub release | Asset |
|---|---|---|
| `almalinux-10` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/almalinux-10) | `almalinux-10.tar.gz` |
| `almalinux-8` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/almalinux-8) | `almalinux-8.tar.gz` |
| `almalinux-9` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/almalinux-9) | `almalinux-9.tar.gz` |
| `centos-stream-10` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/centos-stream-10) | `centos-stream-10.tar.gz` |
| `centos-stream-9` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/centos-stream-9) | `centos-stream-9.tar.gz` |
| `debian-12` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/debian-12) | `debian-12.tar.gz` |
| `debian-13` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/debian-13) | `debian-13.tar.gz` |
| `opensuse-leap-15.6` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/opensuse-leap-15.6) | `opensuse-leap-15.6.tar.gz` |
| `opensuse-leap-16.0` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/opensuse-leap-16.0) | `opensuse-leap-16.0.tar.gz` |
| `oracle-linux-10` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/oracle-linux-10) | `oracle-linux-10.tar.gz` |
| `oracle-linux-9` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/oracle-linux-9) | `oracle-linux-9.tar.gz` |
| `rhel-ubi10` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/rhel-ubi10) | `rhel-ubi10.tar.gz` |
| `rhel-ubi9` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/rhel-ubi9) | `rhel-ubi9.tar.gz` |
| `rocky-linux-10` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/rocky-linux-10) | `rocky-linux-10.tar.gz` |
| `rocky-linux-8` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/rocky-linux-8) | `rocky-linux-8.tar.gz` |
| `rocky-linux-9` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/rocky-linux-9) | `rocky-linux-9.tar.gz` |
| `ubuntu-24.04` | [release](https://github.com/DanilaGrinRus/GrinNodeUnix/releases/tag/ubuntu-24.04) | `ubuntu-24.04.tar.gz` |

## Quick start

```sh
tar -xzf debian-12.tar.gz
cd debian-12
chmod +x grin run-node.sh
./run-node.sh
```

First start creates `grin-server.toml`:

```text
Mainnet, P2P 3414, API 127.0.0.1:3413
```

The API secret is stored locally as `.api_secret`; never publish it.

## Hardware

| Resource | Minimum | Comfortable |
|---|---:|---:|
| CPU | 2 vCPU | 4 vCPU |
| RAM | 8 GiB | 16 GiB |
| Disk | 20 GiB | 40 GiB |
| Network | 3414/tcp outbound | 3414/tcp + inbound |

Basis: 8 GiB was OOM-killed during FreeBSD sync; 16 GiB active used about
4.4 GiB RSS. Full `chain_data` was about 5 GiB at height 4.1M, and the
pruned/archive layout can differ.

## Verify downloads

```sh
sha256sum -c SHA256SUMS
```

## Status and limitations

- Builds were checked in their matching distro/container; this repository
  does not claim full sync on every release.
- The binaries are Linux glibc builds. Do not run a newer-release binary on
  an older glibc generation.
- This is not an official Grin release; it follows the PR branch above.
- No API secrets, seeds, chain data or host addresses are included.

## License

Grin is Apache-2.0; see `LICENSE`.
