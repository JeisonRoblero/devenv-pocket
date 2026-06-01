# Contributing to devenv-pocket

Thanks for taking the time to contribute! Whether you are a beginner or an experienced developer, we are excited to have you join our open-source community.

---

## Branches

| Branch | Purpose |
| --- | --- |
| `main` | Stable, production-ready release code |
| `develop` | Active development branch - target your Pull Requests here |

**Always open Pull Requests against the `develop` branch, not `main`.**

---

## How to Contribute

1. **Fork** the repository on GitHub.

2. **Clone** your fork locally:

    ```bash
    git clone https://github.com/YOUR_USERNAME/devenv-pocket.git
    cd devenv-pocket
    ```

3. **Create a branch** for your modifications:

    ```bash
    git checkout -b feature/your-feature-name
    ```

4. **Make your changes** and test them inside a real `proot-distro` Ubuntu environment.
   * Verify syntax formatting by running `bash -n devenv-pocket`.
   * Verify that interactive wizard dashboard selectors load correctly.

5. **Commit** with a clear semantic message:

    ```bash
    git commit -m "feat: short description of what you did"
    ```

6. **Push** to your fork:

    ```bash
    git push origin feature/your-feature-name
    ```

7. **Open a Pull Request** from your branch (`feature/your-feature-name`) to the `develop` branch on the original repository.

---

## Commit Message Conventions

We use simple Semantic Commits tags to organize repository history:

| Prefix | Description |
| --- | --- |
| `feat:` | A new user-facing feature |
| `fix:` | A bug fix |
| `docs:` | Documentation edits (README, CONTRIBUTING) |
| `refactor:` | Code structural cleanups without changing behavior |
| `chore:` | Maintenance tasks (dependency updates, configurations) |

---

## Bug Reports & Feature Requests

Open a new [Issue](https://github.com/JeisonRoblero/devenv-pocket/issues) and describe:

- The expected behavior vs. what actually happened.
- Steps to reproduce the bug.
- System details: Android version, Termux version, and distro details.

---

## Questions

Feel free to open an Issue if anything is unclear. All skill levels are welcome!
