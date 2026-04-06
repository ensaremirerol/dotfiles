# dotfiles

Personal zsh configuration and shell scripts.

## Setup

Clone the repo and source `entry` from your `~/.zshrc`:

```zsh
source /path/to/dotfiles/entry
```

`entry` will:
- Set locale (`LANG`/`LC_ALL` to `C.UTF-8`)
- Symlink `~/.gitconfig` → `dotfiles/gitconfig` (if not already linked)
- Initialize [oh-my-zsh](https://ohmyz.sh/) (`robbyrussell` theme)
- Conditionally initialize [zoxide](https://github.com/ajeetdsouza/zoxide) and [yazi](https://github.com/sxyazi/yazi)
- Source all config files below

### Prerequisites

Required:
- [oh-my-zsh](https://ohmyz.sh/)

Optional (features activate when installed):
- `fzf` - fuzzy finder, used by aliases and docker aliases
- `zoxide` - smarter `cd`
- `yazi` - terminal file manager (adds `y` wrapper)
- `docker` - enables docker aliases
- `bw` (Bitwarden CLI) - enables shell completion and `um_vpn`
- `uv` - enables shell completion


## bin/

Scripts are added to `$PATH` via `path`.

### `split_csv`

Splits a CSV file into N roughly equal parts, preserving the header in each part.

```sh
split_csv <csv_file> <split_count>
```

Output files are written to `<csv_file_basename>_parts/part_01.csv`, `part_02.csv`, etc.

### `um_vpn`

Toggles a Maastricht University VPN connection via `openconnect`, fetching credentials from Bitwarden.

**Dependencies:** `openconnect`, `bw` (Bitwarden CLI), `jq`, `sudo`

Configure via `~/.vpnrc`:

```sh
VPN_USER="your-university-id"
AUTH_GROUP="your-auth-group"
```
