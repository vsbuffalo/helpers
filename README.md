# Helper Scripts

These are developer helper scripts I've created for various purposes.

## Installation

If you wish to install via cloning:

1. Clone the repository somewhere:

   ```bash
   git clone https://github.com/vsbuffalo/helpers.git
   ```

2. Then add the `bin/` directory to your `$PATH` in your shell profile (e.g.
   `.bashrc` or `.zshrc`):

   ```bash
   export PATH="$HOME/<path-to-cloned-helpers-repo>/bin:$PATH"
   ```

Alternatively, you can curl the helpers directly into Bash to run them ad hoc.
For example:

```bash
curl -s https://raw.githubusercontent.com/vsbuffalo/helpers/main/bin/enable-protect-main | bash -s <git-repo-dir>
```

## Scripts

All scripts live in the `bin/` directory.

### Git hooks

- `enable-protect-main`: Adds a Git hook to prevent accidental pushes to `main`
  or `master`. This is useful if your team collaborates by pushing feature
  branches directly to the shared repository (instead of using forks and PRs).

#### 🔧 Usage

From inside the repo you want to protect:

```bash
enable-protect-main .
```

This installs a `.git/hooks/pre-push` hook in the specified repo.

Example output:

```
⚙️  Installing pre-push hook in .
✅ pre-push hook installed successfully in .
```

