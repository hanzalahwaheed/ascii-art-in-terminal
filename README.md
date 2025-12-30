# Luffy Art in Zsh

## Steps:

1. Add this cofig your to the top of your `.zshrc` to show some ASCII art when you open a new terminal window.

```bash
center_file() {
  local cols
  cols=$(tput cols)

  while IFS= read -r line; do
    local len=${#line}
    if (( len < cols )); then
      printf "%*s%s\n" $(( (cols - len) / 2 )) "" "$line"
    else
      printf "%s\n" "$line"
    fi
  done
}

# Only run in interactive shells
[[ $- != *i* ]] && return
[[ -n "$SSH_CONNECTION" ]] && return

if [[ "$TERM_PROGRAM" == "iTerm.app" && -z "$ZSH_BANNER_SHOWN" ]]; then
  export ZSH_BANNER_SHOWN=1
  clear

  # Muted crimson red
  printf '\033[38;5;160m'
  center_file < ~/.config/zsh/art/luffy.txt
  printf '\033[0m'
fi
```

2. create a folder using `mkdir .config/zsh/art`

3. add a file called `luffy.txt`

> *Minimal yet aesthetic. You can add more such ASCII artworks to this repository*

Lastly, **the ONE PIECE is REAL!**