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

# GhostShell - 技術スタック

GhostShellは、**高速・拡張性・ハッカー風デザイン** を実現するために、以下の技術スタックを採用する。

---

## 1. コア技術
| **カテゴリ**       | **技術 / ライブラリ**       | **用途** |
|------------------|-------------------------|---------|
| 言語            | Rust                     | 高速・安全な並行処理 |
| フレームワーク  | `ratatui` + `crossterm`  | TUI描画とイベント処理 |
| プロセス管理    | `procfs`（Linux） / `sysinfo`（macOS, Windows） | CPU・メモリ・ネットワーク監視 |

---

## 2. TUIコンポーネント
| **コンポーネント**  | **技術 / ライブラリ**     | **用途** |
|------------------|-----------------------|---------|
| **システムモニター** | `sysinfo` + `ratatui`  | CPU / RAM / Disk / Networkのリアルタイム監視 |
| **テキストエディタ** | `Helix`（組み込み）   | モダンなTUIエディタ |
| **ウェブブラウザ**   | `Carbonyl` / `w3m` / `Lynx` | TUIブラウザ機能 |
| **ファイルブラウザ** | `tui-file-manager`    | ターミナル上でのファイル管理 |

---

## 3. タイル型ウィンドウ管理
| **機能**          | **技術 / ライブラリ** | **用途** |
|----------------|----------------|---------|
| ウィンドウ分割 | `zellij`（参考） / `ratatui` | `tmux` のようなタイル型レイアウト |
| マルチスクリーン対応 | `winit` + `xrandr-rs` | 追加モニターへウィンドウ拡張 |
| キーボード制御 | `crossterm` | 完全キーボード操作 |

---

## 4. ネットワーク・外部連携
| **機能**       | **技術 / ライブラリ** | **用途** |
|-------------|-----------------|---------|
| API連携    | `reqwest` + `serde_json` | REST APIのデータ取得 |
| SSH接続    | `russh` / `ssh2` | リモートサーバー監視 |
| P2P通信    | `libp2p` | 分散データ共有 |

---

## 5. AI・オートメーション（ロードマップ）
| **機能**     | **技術 / ライブラリ** | **用途** |
|-----------|-----------------|---------|
| AIアシスタント | `ollama` / `whisper.cpp` | 自然言語コマンド解析 |
| 自動化      | `autopilot-rs` | RPAワークフロー実装 |

---

## 6. ビルド・パッケージ管理
| **機能**   | **技術 / ライブラリ** | **用途** |
|---------|-----------------|---------|
| ビルド管理 | `cargo` | Rustのビルドツール |
| バイナリ配布 | `cargo-binstall` | 各環境への簡単インストール |
| コンテナ化 | `Docker` | OS環境に依存しない実行環境 |

---

## 設計のポイント
- **Rustベース** - 高速・安全・低リソース消費  
- **完全TUI** - `ratatui` によるモダンなTUI UI  
- **タイル型UI** - `tmux` のようなウィンドウ管理  
- **マルチスクリーン対応** - 複数モニター拡張  
- **AI & 自動化** - 未来的なワークスペースの実現  

---

この技術スタックに変更や追加が必要な場合は、適宜アップデートする。

# GhostShell - ディレクトリ構成

GhostShellは、**モジュール化された設計** を採用し、拡張性と保守性を重視したディレクトリ構成を採用する。

\`\`\`
GhostShell/
│── src/               # コアソースコード
│   │── main.rs        # エントリーポイント
│   │── app.rs         # アプリケーション管理
│   │── ui.rs          # TUIのレンダリング
│   │── input.rs       # キーバインド・イベント処理
│   │── system/        # システムモニター機能
│   │   │── mod.rs
│   │   │── cpu.rs
│   │   │── memory.rs
│   │   │── network.rs
│   │── editor/        # テキストエディタ機能
│   │   │── mod.rs
│   │   │── buffer.rs
│   │   │── commands.rs
│   │── browser/       # TUIブラウザ機能
│   │   │── mod.rs
│   │   │── renderer.rs
│   │── tiling/        # タイル型ウィンドウ管理
│   │   │── mod.rs
│   │   │── layout.rs
│   │   │── workspace.rs
│── docs/              # ドキュメント
│   │── README.md      # プロジェクト概要
│   │── tech_stack.md  # 技術スタック
│   │── architecture.md # アーキテクチャ設計
│   │── usage.md       # 使用方法
│── assets/            # 設定ファイルやリソース
│── config/            # 設定・環境ファイル
│   │── settings.toml  # ユーザー設定
│   │── keybindings.toml # キーバインド設定
│── scripts/           # 補助スクリプト
│   │── install.sh     # インストールスクリプト
│   │── build.sh       # ビルドスクリプト
│── tests/             # テストコード
│   │── test_system.rs # システムモニターのテスト
│   │── test_editor.rs # テキストエディタのテスト
│   │── test_browser.rs # ブラウザ機能のテスト
│── Cargo.toml         # Rustの依存関係
│── README.md          # プロジェクト概要
│── LICENSE            # ライセンス
\`\`\`

このディレクトリ構成に変更が必要な場合は適宜更新する。


