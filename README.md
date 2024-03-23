# edelweiss

edelweiss, `/ˈeɪdəlvaɪs/`. A de**light**ful color scheme for my personal terminal stack.
<br>

<img align="right" width="50%" src="assets/logo_v1.png" />

edelweiss currently supports:

- [kitty](https://sw.kovidgoyal.net/kitty/) - *The fast, feature-rich, CPU based terminal emulator.*
- [neovim](https://neovim.io/) - *Hyperextensible Vim-based text editor.*
- [tmux](https://github.com/tmux/tmux) - *terminal multiplexer*.
- [k9s](https://k9scli.io/) - *Kubernetes CLI to manage your clusters in style.*

▶️  Have a look at the [Installation](#installation) instructions!

<br><br><br><br><br><br>

***

Oh, and that's how it may look like:

![edelweiss](assets/screenshot.png "edelweiss")

## Installation

The different terminal tools use different package managers or none.
Thus, you have to follow the instructions below to install the color schemes
for the tools you want.

The sections below assume that you have cloned this repository into
`~/.config/edelweiss`:

```shell
git clone https://github.com/timofurrer/edelweiss ~/.config/edelweiss
```

### kitty

In your kitty config at `~/.config/kitty/kitty.conf` place an `include` statement
to include the theme located in this repository at `./kitty/edelweiss.conf`.

```shell
echo 'include ~/.config/edelweiss/kitty/edelweiss.conf' >> ~/.config/kitty/kitty.conf
```

### neovim

You may use any neovim-compatible package manager to point to this repository and the
`nvim` subdirectory, where the nvim *plugin* is located.
Using [Lazy](https://github.com/folke/lazy.nvim#-plugin-spec) this may look like this:

```lua
{
  "timofurrer/edelweiss",
  lazy = false, -- make sure we load this during startup, because it's the main colorscheme
  priority = 1000, -- make sure to load this before all the other start plugins
  config = function(plugin)
    vim.opt.rtp:append(plugin.dir .. "/nvim")
    vim.cmd([[colorscheme edelweiss]])
  end
}
```

### tmux

*I'm still trying to figure out how to use TPM with subdirectories,
see https://github.com/tmux-plugins/tpm/issues/279*.

For the time being, you may just `source-file` the `edelweiss.tmux`
from your `tmux.conf`.

### k9s

Put the `./k9s/edelweiss.yaml` file into `$XDG_CONFIG_HOME/k9s/skins/edelweiss.yaml`.
One macOS the `k9s` directory is located at `~/Library/Application Support/k9s`.

The from your `config.yaml` put a reference to `edelweiss` in `k9s.ui.skin`, like so:

```yaml
k9s:
  ui:
    skin: edelweiss
```
