#!/usr/bin/env bash
# Summary: Configure the shell environment for projectrc
# Usage: eval "$(projectrc init - [--projects-path="$HOME/Projects"] [<shell>])"

# Exit on first failure
set -e
# Echo execution (for debugging)
if [ "$PROJECTRC_DEBUG" -ne 0 ] && set -x

# Init args
for args in "$@"; do
  if [ "$args" = "-" ]; then
    print=1
    shift
  fi

  if [ "$args" = "--projects-path"* ]; then
    no_rehash=1
    shift
  fi
done

if [ -z "$PROJECTS_DIR" ]; then
  PROJECTS_DIR="$HOME/Projects"
fi

# Make sure the projectrc paths exist
mkdir -p "$HOME/.projectrc/bash_history.d"

# Detect bash init file (if not specified)
detect_profile () {
  if [ -f "$PROFILE" ]; then
    echo "$PROFILE"
  elif [ -f "$HOME/.bashrc" ]; then
    echo "$HOME/.bashrc"
  elif [ -f "$HOME/.bash_profile" ]; then
    echo "$HOME/.bash_profile"
  elif [ -f "$HOME/.zshrc" ]; then
    echo "$HOME/.zshrc"
  elif [ -f "$HOME/.profile" ]; then
    echo "$HOME/.profile"
  fi
}

