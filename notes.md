# Local Development Setup

Commands to build on a new machine:

## Prerequisites (Arch Linux)

```bash
paru -S pnpm hugo go
```

## Install Dependencies

```bash
pnpm install
```

This installs:
- Tailwind CSS and typography plugin
- `hugoblox` CLI (provides `hbx` command)

## Build Site

```bash
pnpm hbx build   # or: pnpm build
```

## Development Server

```bash
pnpm dev
```

## Full Production Build (with search index)

```bash
./deploy
```
