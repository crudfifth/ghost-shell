# GhostShell

GhostShell is a highly extensible, hacker-style TUI workspace that integrates a **system monitor**, **text editor**, and **TUI browser**. Designed for power users, it offers seamless keyboard-driven navigation with a modular, multi-screen layout.

## Features

- **System Monitoring** - Real-time CPU, RAM, and network tracking with a btop++-inspired interface.
- **Text Editing** - A fully integrated TUI editor based on Helix, optimized for speed and usability.
- **TUI Web Browsing** - Support for Carbonyl, w3m, and Lynx for in-terminal browsing.
- **Tiling UI** - A tmux-like layout manager for seamless workspace control.
- **Multi-Screen Expansion** - Extend your workflow across multiple monitors.
- **Keyboard-First Workflow** - Completely CLI-driven with no mouse interaction required.

## Interface Layout

```
+---------------------+---------------------+
|    System Monitor   |     Text Editor     |
|  (CPU, RAM, NET)    |  (Code, Notes)      |
+---------------------+---------------------+
|        TUI Browser (News, API Data)       |
+-------------------------------------------+
```

## Navigation

- `Ctrl+1` - Focus on system monitor
- `Ctrl+2` - Switch to text editor
- `Ctrl+3` - Open TUI browser
- `Ctrl+T` - Create a new workspace tab
- `Alt+→ / ←` - Move and resize panels
- `Alt+Shift+→ / ←` - Extend to additional monitors

## Installation

```sh
git clone https://github.com/your-repo/GhostShell.git
cd GhostShell
cargo build --release
```

## Technology Stack

GhostShell is built with a modern, efficient stack for high performance in terminal environments.

- **Rust** - Core framework and performance optimization.
- **ratatui + Crossterm** - TUI rendering and event handling.
- **Helix** - Integrated text editor with modal editing.
- **Carbonyl / w3m / Lynx** - TUI-based web browsing.
- **tmux-like manager** - Tiling window control for a flexible workspace.

## Roadmap

- **Plugin System** - Extend functionality with user-defined modules.
- **Multi-User Sessions** - Shared terminal sessions with real-time collaboration.
- **AI Assistant Integration** - Smart task automation within the TUI workspace.

## License

This project is licensed under the MIT License.
