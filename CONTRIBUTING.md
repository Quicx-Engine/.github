# Contributing to Quicx

Thank you for helping. This applies to every repository in Quicx-Engine and to [anastassow/Quicx](https://github.com/anastassow/Quicx).

## Reporting a bug

Open an issue in the repository the bug is in, with:

- the version (`quicx version`, or the client version from your build file) and the OS and CPU;
- what you did, what you expected and what happened, with the exact output;
- the smallest set of steps or a short program that shows it.

A security problem does not belong in a public issue; see [SECURITY](SECURITY.md).

## Proposing a change

For anything larger than a small fix, open an issue first so the approach can be agreed before you spend time on it. Then:

1. Fork the repository and create a branch.
2. Make the change, with a test that fails without it.
3. Run the tests: `make test` and `make e2e` for the daemon, `mvn test` for the Java client (add `QUICXD=/path/to/quicxd` to also test against a real daemon), `npm run build` for the website.
4. Open a pull request that says what changed and why, and how you checked it.

## Numbers

Quicx publishes only numbers that a script in the repository measured, with the raw output next to it. A pull request that changes a figure in a README or on quicx.dev should include the script and the result it comes from. A pull request that changes performance should include before-and-after numbers from the same machine.

## Style

- C: C17, no dependencies, the style of the file you are editing. The daemon is single-threaded and allocates task memory only through apool.
- Java: Java 11, no dependencies, the public API in `dev.quicx`, internals in `dev.quicx.internal`.
- Commit messages: a short summary line, then what changed and why.

By contributing you agree that your contribution is licensed under the MIT licence of the repository.
