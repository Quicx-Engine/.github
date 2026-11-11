<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/anastassow/Quicx/main/docs/assets/banner-dark.png">
    <img src="https://raw.githubusercontent.com/anastassow/Quicx/main/docs/assets/banner-light.png" alt="Quicx, a task queue with a hard memory limit" width="100%">
  </picture>
</p>

<p align="center">
  <b>A task queue that never goes past its memory budget, and keeps the most valuable work when it is full.</b><br>
  <a href="https://quicx.dev">quicx.dev</a> ·
  <a href="https://quicx.dev/docs/installation">Docs</a> ·
  <a href="https://github.com/anastassow/Quicx">Source</a> ·
  <a href="https://central.sonatype.com/artifact/dev.quicx/quicx-client">Java client</a>
</p>

Quicx is a task queue daemon written in C for devices and servers with little memory: robots, cameras and other edge-AI hardware, small VMs, and one server shared by many customers. It is given one memory budget when it starts and never goes past it. When the budget is full, a more valuable task can push out a less valuable one that is waiting, but only when Quicx's own allocator proves that the freed memory fits it. Capacity is worked out before deployment, and one daemon per core gives isolation and adds throughput.

```sh
curl -fsSL https://quicx.dev/install.sh | sh     # Linux and macOS, x86-64 and arm64
quicx start
```

### Measured

| | |
|---|---|
| Valuable tasks done under overload | **100 %**, against 31.6 % for a queue that refuses new tasks |
| Tasks of 100 B in an 8 MiB budget | **46,593**, exactly what the capacity formula gives |
| Two daemons on two cores | **1.92 times** the work of one |
| Throughput and median latency | **81,900 tasks/s**, **49 µs** (Apple M4 Pro) |
| The whole program on a Raspberry Pi | **36 KB**, no dependencies |

Every number comes from a script in the source repository, which also has the raw output.

### Repositories

| | |
|---|---|
| [**anastassow/Quicx**](https://github.com/anastassow/Quicx) | the daemon in C, its allocator apool, tests, the technical report and the research on learned task values |
| [**Quicx-Java**](https://github.com/Quicx-Engine/Quicx-Java) | the Java client, `dev.quicx:quicx-client` on Maven Central |
| [**Quicx-Releases**](https://github.com/Quicx-Engine/Quicx-Releases) | release binaries for Linux and macOS with SHA-256 checksums |
| [**quicx-website**](https://github.com/Quicx-Engine/quicx-website) | [quicx.dev](https://quicx.dev): the site and the documentation |

Quicx is open source under the MIT licence. It was started on 2 April 2026 by [Dimitar Anastasov](https://www.linkedin.com/in/dimitar-anastasov-339a94310/). Issues and pull requests are welcome; see [CONTRIBUTING](https://github.com/Quicx-Engine/.github/blob/main/CONTRIBUTING.md).
