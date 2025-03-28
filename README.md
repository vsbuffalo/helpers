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


### Azure CLI Helpers

 - `az-list-vms`: Lists available Azure VM sizes in a given region with pretty
   table output. Supports sorting and slicing. 


#### 🔧 Usage

```
az-list-vms                            # Defaults to westus, all sizes
az-list-vms --location eastus2
az-list-vms --sort MemoryGB            # Sorts by MemoryGB
az-list-vms --sort Cores --head 5      # Fewest core machines
az-list-vms --sort DiskGB --tail 10    # Machines with largest disk space
```

An example: find the VMs with the most cores:


```
$ az-list-vms --sort MemoryGB --tail 5
Name              Cores  MemoryGB  DiskGB
Standard_E96_v5   96     672       0
Standard_E104i_v5 104    672       0
Standard_M208ms   208    5700      4096
```

Perfect for quickly exploring what VM types are available in a region before
creating analysis infrastructure or spinning up experiments.
