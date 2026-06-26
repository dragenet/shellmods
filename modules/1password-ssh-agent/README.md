# 1password-ssh-agent

Configures the SSH agent socket to use 1Password's built-in SSH agent.

## Prerequisites

- 1Password 8 or later
- SSH agent enabled in 1Password Settings → Developer → Use the SSH agent

## What it does

Sets `SSH_AUTH_SOCK` to the 1Password agent socket, so SSH clients use 1Password to serve keys and handle authentication prompts.
