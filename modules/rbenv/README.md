# rbenv

Initializes rbenv for Ruby version management using lazy loading.

## What It Does

- Defines lightweight wrapper functions for `rbenv`, `ruby`, `gem`, `bundle`, and `irb`.
- On first invocation of any of these commands, runs `rbenv init` to set up shims and autocompletion, then runs the original command.
- This lazy-loading approach avoids the startup cost of `rbenv init` on every shell launch.

## Prerequisites

- rbenv installed and available in `$PATH`. Install via `brew install rbenv`.
