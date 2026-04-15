# SOSCLOSE

SOSCLOSE is a macOS `zsh` helper for quick "pre-call" or "fresh start" cleanup. The original research and design notes are still in `deep-research-report.md`, and the runnable script now lives in `./SOSCLOSE`.

## Files

- `SOSCLOSE`: standalone executable script
- `deep-research-report.md`: original research and full rationale

## Quick Start

```sh
chmod +x ./SOSCLOSE
./SOSCLOSE --help
./SOSCLOSE -m 1
```

Modes:

- `1`: Call mode
- `2`: Dev cleanup
- `3`: Aggressive cleanup
- `4`: Custom cleanup

Useful examples:

```sh
./SOSCLOSE -m 1 --keep slack --keep teams
./SOSCLOSE -m 2 --keep "Google Chrome"
./SOSCLOSE -m 3 --dry-run
./SOSCLOSE -m 4
```

## Add Alias

If you want to run `SOSCLOSE` from anywhere on this system, add this alias to `~/.zshrc`:

```sh
echo "alias SOSCLOSE='/Users/samarth/Desktop/personal/SOSCLOSE/SOSCLOSE'" >> ~/.zshrc
source ~/.zshrc
```

After that, you can run:

```sh
SOSCLOSE -m 1
```

## macOS Permissions

The script may trigger macOS prompts the first time it tries to control apps.

- `Automation`: needed when Terminal or another shell app sends Apple events to other apps.
- `Accessibility`: needed for best-effort window minimising through `System Events`.

## Notes

- Desktop icon hiding is persistent until reverted.
- To restore desktop icons:

```sh
defaults write com.apple.finder CreateDesktop -bool true
killall Finder
```
