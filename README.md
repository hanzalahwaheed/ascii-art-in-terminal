# ASCII Art in Terminal

A collection of ASCII art for terminal customization.

## Setup Instructions

### 1. Create directory
Create a dedicated folder for your ASCII art:
```bash
mkdir -p ~/.config/zsh/art
```

### 2. Add art file
Save your ASCII art (e.g., `luffy.txt`) into the created directory.

### 3. Update configuration
- Add the following function and configuration to the top of your `.zshrc` file.
- Also make sure you enter the file path in the function correctly.

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

Contributions are welcome. You can add more ASCII artworks to this repository.
