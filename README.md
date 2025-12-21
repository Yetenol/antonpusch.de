# Anton's Digital Garden

A personal collection of interconnected notes on topics that interest me like LaTeX typesetting, PowerShell scripting, programming techniques, technical guides, and more.

## Content

Generated from Markdown source files like [Home](content/index.md).

## Static site generator

Built with [Quartz v4](https://quartz.jzhao.xyz/), a fast static-site generator for interconnected markdown files.

## Dependencies

Node.js (LTS)

```powershell
winget install -e OpenJS.NodeJS.LTS
```

- Update npm tool
  ```powershell
  npm audit fix
  ```

- Install node packages
  ```powershell
  npm i
  ```

### Build locally

```powershell
npx quartz build --serve
```

### Update

- See [instructions](https://quartz.jzhao.xyz/upgrading)

```powershell
npx quartz update
```