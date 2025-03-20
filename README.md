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


# GhostShell - 開発フロー

GhostShellの開発は、**一貫性のあるコード品質の維持** と **スムーズな機能拡張** を目的に、以下の開発フローを採用する。

---

## 1. ブランチ戦略

**Git Flow** に基づき、以下のブランチ構成を採用する。

\`\`\`
main        # 安定版のみ（リリース用）
dev         # 開発用のメインブランチ
feature-*   # 機能ごとの開発ブランチ
bugfix-*    # バグ修正用のブランチ
hotfix-*    # クリティカルな修正
release-*   # リリース準備ブランチ
\`\`\`

### ブランチの運用ルール
- `main` は **リリース済みの安定版** のみ
- `dev` は **最新の開発版**（安定したら `main` にマージ）
- `feature-*` は **新機能開発用**（`dev` から作成し、完了後に`dev`へマージ）
- `bugfix-*` は **バグ修正用**（`dev` に向けてマージ）
- `hotfix-*` は **緊急修正**（`main` に直接適用し、`dev` にも反映）

---

## 2. コードスタイルと静的解析

### **Rustのスタイルガイド**
GhostShellはRustの標準スタイルを採用し、一貫したコード品質を維持する。

#### フォーマット設定
\`\`\`
cargo fmt --all
\`\`\`

#### 静的解析
\`\`\`
cargo clippy --all-targets --all-features
\`\`\`

\`cargo fmt\` を実行しないコードは **PRを受け付けない**。

---

## 3. コミットメッセージ規則

**Conventional Commits** に従い、以下のフォーマットを採用する。

\`\`\`
<type>(<scope>): <subject>

<body>
\`\`\`

### **コミットタイプ**
| タイプ  | 説明 |
|---------|--------------------------------------------|
| feat    | 新機能の追加 |
| fix     | バグ修正 |
| refactor| コードのリファクタリング（動作変更なし） |
| perf    | パフォーマンス改善 |
| docs    | ドキュメントの追加・更新 |
| test    | テストの追加・修正 |
| chore   | ビルド・CI/CD・依存関係の更新 |

**例**
\`\`\`
feat(editor): Implement syntax highlighting
fix(browser): Resolve issue with URL parsing
docs(README): Update installation instructions
\`\`\`

---

## 4. プルリクエスト（PR）ルール

### **基本ルール**
- **`dev` へのPRのみ受け付ける**（`main` への直接PRは禁止）
- **コードレビューを必須とする**（最低1名の承認）
- **テストがパスしないPRはマージしない**
- **変更内容はPRの説明に明記する**

### **PRテンプレート**
\`\`\`markdown
## Summary
(変更内容の概要)

## Changes
- (変更点1)
- (変更点2)

## Issue Reference
Fixes #(関連Issue番号)

## Checklist
- [ ] `cargo fmt` を適用済み
- [ ] `cargo clippy` のチェックを通過
- [ ] ユニットテストを追加・修正
\`\`\`

---

## 5. CI/CD

GitHub Actionsを利用し、PR作成時に以下を自動チェックする。

| ステップ  | チェック内容 |
|-----------|--------------------------------|
| Format   | `cargo fmt --check` でフォーマットチェック |
| Lint     | `cargo clippy` で静的解析 |
| Build    | `cargo build --release` のビルド検証 |
| Test     | `cargo test` でユニットテスト実行 |

---

## 6. 開発環境セットアップ

**Rustのバージョンを固定する**
\`\`\`
rustup override set stable
\`\`\`

**開発用の依存関係をインストール**
\`\`\`
cargo install cargo-binstall
cargo install cargo-watch
\`\`\`

**TUIの動作確認**
\`\`\`
cargo run
\`\`\`

---

## 7. リリース手順

1. `dev` で全ての機能が安定したら `release-*` ブランチを作成
2. `release-*` の最終確認後、`main` にマージ
3. `git tag vX.Y.Z` でバージョンタグを付与
4. `cargo publish` でリリース
5. `CHANGELOG.md` を更新

---

## 8. バグ報告・フィードバック

バグ報告・改善提案は **GitHub Issues** に投稿する。  
再現手順・エラーログ・期待する動作を明記すること。

\`\`\`markdown
### Issueテンプレート

## Description
(問題の説明)

## Steps to Reproduce
1. (再現手順)
2. (再現手順)
3. (結果)

## Expected Behavior
(期待する動作)

## Environment
- OS: (例: Ubuntu 22.04)
- Rust Version: (例: 1.76.0)
- Terminal Emulator: (例: Alacritty)
\`\`\`

---

この開発フローに変更が必要な場合は適宜更新する。

# GhostShell - 設定・環境変数

GhostShellでは、ユーザーのカスタマイズ性を確保しつつ、シンプルな設定管理を実現するために **TOML形式の設定ファイル** と **環境変数** を採用する。

---

## 1. 設定ファイル (`config/settings.toml`)

GhostShellの主要な設定は `config/settings.toml` に保存され、ユーザーがカスタマイズ可能。

\`\`\`toml
[general]
theme = "dark"  # テーマ: dark / light / hacker
language = "en" # 言語: en / ja / etc.

[editor]
default_mode = "normal"  # 初期モード: normal / insert
tab_size = 4             # タブ幅
syntax_highlighting = true  # シンタックスハイライトを有効化

[system_monitor]
update_interval = 1  # 更新間隔（秒単位）
show_process_tree = true  # プロセスツリー表示を有効化

[browser]
default_engine = "w3m"  # 使用するTUIブラウザ: w3m / lynx / carbonyl
proxy = ""  # プロキシ設定（未使用なら空）

[keybindings]
quit = "Ctrl+Q"
toggle_monitor = "Ctrl+1"
toggle_editor = "Ctrl+2"
toggle_browser = "Ctrl+3"
\`\`\`

---

## 2. 環境変数

環境変数は `.env` ファイルまたはシステム環境変数として設定可能。  
（`.env` ファイルを `config/.env` に配置）

\`\`\`
GHOSTSHELL_THEME=dark
GHOSTSHELL_LANG=en
GHOSTSHELL_UPDATE_INTERVAL=1
\`\`\`

環境変数の優先順位:
1. コマンドライン引数（`--theme light`）
2. 環境変数（`GHOSTSHELL_THEME=light`）
3. 設定ファイル（`settings.toml`）
4. デフォルト値

---

## 3. 設定のロード優先度

GhostShellは **コマンドラインオプション > 環境変数 > 設定ファイル** の優先順位で設定をロードする。

\`\`\`
# 例: テーマをlightに変更
GHOSTSHELL_THEME=light cargo run
\`\`\`

または、設定ファイルを直接編集:

\`\`\`toml
[general]
theme = "light"
\`\`\`

---

## 4. 設定の適用方法

設定を変更した後、以下のコマンドで反映。

\`\`\`
cargo run -- --reload-config
\`\`\`

または `Ctrl+R` で再読み込み。

---

## 5. OSごとの設定

| OS | 設定ファイルのパス |
|----|----------------|
| Linux | `~/.config/ghostshell/settings.toml` |
| macOS | `~/Library/Application Support/GhostShell/settings.toml` |
| Windows | `%APPDATA%\GhostShell\settings.toml` |

---

この設定・環境変数の設計に変更が必要な場合は適宜更新する。

# GhostShell - MVP（最小限の機能）と開発優先度

GhostShellは、**ターミナル内で完結するハッカー風の統合TUI環境** を目指して開発を進める。  
まずは **MVP（Minimum Viable Product: 最小限の実用レベル）** を確立し、基本機能を実装した上で拡張していく。

---

## 1. MVP（最小限の機能）

最初に実装する **コア機能** は以下の4つ。

### ✅ **1. タイル型TUIレイアウト**
- `tmux` のように**3画面分割**（システムモニター / テキストエディタ / TUIブラウザ）
- `Ctrl+1` `Ctrl+2` `Ctrl+3` で各ウィンドウに切り替え
- `Alt+→` `Alt+←` でウィンドウサイズ調整

### ✅ **2. システムモニター**
- `btop++` 風の **CPU / RAM / Disk / Network 監視**
- `update_interval` の設定に基づくリアルタイム更新
- `show_process_tree` オプションでプロセスツリー表示

### ✅ **3. TUIテキストエディタ**
- `Helix` ベースのTUIエディタ
- シンタックスハイライト対応
- `vim` ライクなキーバインド（Normal / Insert / Visual モード）

### ✅ **4. TUIブラウザ**
- `w3m` / `lynx` / `carbonyl` から選択可能
- `default_engine` を `config/settings.toml` で設定可能
- `Ctrl+L` でURL入力、`Enter` でページ遷移

---

## 2. 機能開発の優先順位

### **🛠️ フェーズ1: MVP**
\`\`\`
[ ] タイル型レイアウトの実装
[ ] システムモニターの基本機能
[ ] TUIテキストエディタの組み込み
[ ] TUIブラウザの基本機能
\`\`\`

### **🔧 フェーズ2: 拡張機能**
\`\`\`
[ ] プラグインシステム
[ ] 設定ファイルのホットリロード
[ ] マルチスクリーン対応
\`\`\`

### **🚀 フェーズ3: 高度な機能**
\`\`\`
[ ] AIアシスタント統合（音声 / 自然言語処理）
[ ] P2Pファイル共有
[ ] Git連携（リポジトリ管理機能）
\`\`\`

---

## 3. 最初に実装すべきディレクトリ構成

\`\`\`
src/
│── main.rs            # エントリーポイント
│── app.rs             # アプリケーション管理
│── ui.rs              # TUIのレンダリング
│── input.rs           # キーバインド・イベント処理
│── system/            # システムモニター
│── editor/            # TUIテキストエディタ
│── browser/           # TUIウェブブラウザ
│── tiling/            # タイルレイアウト管理
\`\`\`

---

## 4. 開発の進め方

- **`dev` ブランチでMVP開発を進める**
- **MVP完了後に`main`へマージ**
- **拡張機能は`feature-*` ブランチで並行開発**
- **優先度の高い機能から順番に実装**

---

このロードマップを基準に開発を進め、必要に応じて更新する。

# GhostShell - 使用ライブラリとバージョン管理

GhostShellは **Rust製のTUI統合環境** であり、**高パフォーマンス・低リソース消費・拡張性** を重視したライブラリ構成を採用する。  
また、ライブラリのバージョン管理を徹底し、一貫した開発環境を維持する。

---

## 1. 使用ライブラリ一覧

### **🖥️ TUIレンダリング**
\`\`\`
| ライブラリ  | 用途                      | 備考                        |
|------------|--------------------------|----------------------------|
| ratatui    | TUIの描画・レイアウト管理  | crossterm と組み合わせて使用 |
| crossterm  | ターミナル入力・イベント処理 | Windows / Linux / macOS 対応 |
| zellij     | タイル型ウィンドウ管理（参考実装） | ratatui で独自実装 |
\`\`\`

---

### **📊 システムモニター**
\`\`\`
| ライブラリ  | 用途                      | 備考                        |
|------------|--------------------------|----------------------------|
| sysinfo    | CPU / RAM / Disk / Network 情報取得 | クロスプラットフォーム対応 |
| procfs     | Linuxのプロセス情報取得   | Windows / macOS では不要  |
\`\`\`

---

### **📝 TUIテキストエディタ**
\`\`\`
| ライブラリ  | 用途                      | 備考                        |
|------------|--------------------------|----------------------------|
| Helix      | テキストエディタエンジン  | nvim に近い操作性         |
| ropey      | テキストバッファ管理      | 高速な文字列処理           |
\`\`\`

---

### **🌐 TUIウェブブラウザ**
\`\`\`
| ライブラリ  | 用途                      | 備考                        |
|------------|--------------------------|----------------------------|
| w3m        | テキストベースのウェブブラウザ | 軽量                      |
| lynx       | w3m の代替ブラウザ        | シンプル                    |
| carbonyl   | ChromiumベースのTUIブラウザ | 重めだが高機能              |
\`\`\`

---

### **🔗 ネットワーク・API**
\`\`\`
| ライブラリ  | 用途                      | 備考                        |
|------------|--------------------------|----------------------------|
| reqwest    | HTTPリクエスト処理        | REST API連携                |
| serde      | JSONパース               | 設定ファイルの読み書き        |
\`\`\`

---

### **🎛️ 設定・環境管理**
\`\`\`
| ライブラリ  | 用途                      | 備考                        |
|------------|--------------------------|----------------------------|
| config     | TOML / JSON 設定ファイルの読み込み | 設定ファイル管理  |
| dotenv     | 環境変数のロード          | .env ファイル対応          |
\`\`\`

---

## 2. Rustのバージョン管理

GhostShellでは、**開発環境の統一** を目的に **Rustのバージョンを固定** する。

\`\`\`sh
rustup override set stable
rustup show
\`\`\`

また、`rust-toolchain.toml` により、Rustのバージョンを明示的に指定。

\`\`\`toml
[toolchain]
channel = "stable"
components = ["rustfmt", "clippy"]
\`\`\`

---

## 3. Cargoのバージョン管理

### **`Cargo.lock` をコミットする**
- **依存ライブラリのバージョンを固定**
- **チーム内で一貫した環境を維持**

\`\`\`sh
git add Cargo.lock
git commit -m "Lock dependencies"
\`\`\`

### **依存関係のアップデート方針**
- **バージョンを固定**（`Cargo.lock` を変更しない）
- **定期的にアップデートを実施**
- **マイナーバージョンアップは `cargo update` で対応**
- **メジャーバージョンアップは `feature-*` ブランチで検証**

\`\`\`sh
cargo update
\`\`\`

---

## 4. OSごとの依存関係

\`\`\`
| OS      | 追加のライブラリ         |
|---------|------------------|
| Linux   | procfs, xrandr-rs |
| macOS   | sysinfo          |
| Windows | winapi           |
\`\`\`

---

## 5. 開発環境のセットアップ

### **必要なツールをインストール**
\`\`\`sh
cargo install cargo-binstall
cargo install cargo-watch
\`\`\`

### **依存関係をインストール**
\`\`\`sh
cargo build
\`\`\`

---

このライブラリ構成とバージョン管理方針を基に、開発を進める。

# GhostShell - ドキュメント管理とテスト方針

GhostShellの開発では、**包括的なドキュメント管理と体系的なテスト** を通じて、コードの可読性と品質を維持する。  
本セクションでは、**ドキュメント管理のルール** と **テストの方針** を定義する。

---

## 1. ドキュメント管理

GhostShellのドキュメントは `docs/` ディレクトリに格納し、**Markdown形式** で管理する。

\`\`\`
docs/
│── README.md          # プロジェクト概要
│── tech_stack.md      # 技術スタック
│── architecture.md    # アーキテクチャ設計
│── usage.md           # 使用方法
│── development.md     # 開発ガイドライン
│── test_strategy.md   # テスト方針
\`\`\`

### **ドキュメントの更新ルール**
- **新機能を追加する際は必ず関連ドキュメントを更新**
- **PRの説明には、変更したドキュメントを明記**
- **アーキテクチャの変更があった場合は `architecture.md` を更新**
- **コマンドの使い方が変わる場合は `usage.md` を更新**

---

## 2. テストの方針

GhostShellのテストは、以下の **3種類** で構成される。

### **1️⃣ ユニットテスト（Unit Test）**
- **対象:** 各モジュールの個別の関数やコンポーネント
- **場所:** `tests/unit/`
- **実行:** `cargo test --lib`
- **例:**
  \`\`\`rust
  #[test]
  fn test_memory_usage() {
      let usage = get_memory_usage();
      assert!(usage >= 0);
  }
  \`\`\`

---

### **2️⃣ 結合テスト（Integration Test）**
- **対象:** 複数のコンポーネントが連携して動作するかを確認
- **場所:** `tests/integration/`
- **実行:** `cargo test --test integration`
- **例:**
  \`\`\`rust
  #[test]
  fn test_full_system_monitor() {
      let output = run_system_monitor();
      assert!(output.contains("CPU Usage"));
  }
  \`\`\`

---

### **3️⃣ UIスナップショットテスト（TUI Snapshot Test）**
- **対象:** TUIのレンダリング結果が意図したものと一致するか
- **場所:** `tests/ui/`
- **実行:** `cargo insta test`
- **例:**
  \`\`\`rust
  #[test]
  fn test_tui_rendering() {
      let snapshot = render_tui();
      insta::assert_snapshot!(snapshot);
  }
  \`\`\`

---

## 3. テストカバレッジ

GhostShellは **最低80%のコードカバレッジ** を目標とする。  
カバレッジの確認には `cargo-tarpaulin` を使用。

\`\`\`sh
cargo tarpaulin --ignore-tests
\`\`\`

---

## 4. 自動テスト（CI/CD）

GitHub Actionsを用いて、**PRごとに自動テストを実行** する。

### **CIテストワークフロー**
\`\`\`
- PR作成
  ├── `cargo fmt --check`（コードフォーマットチェック）
  ├── `cargo clippy`（静的解析）
  ├── `cargo test --all`（ユニット・結合テスト）
  └── `cargo insta test`（UIスナップショットテスト）
\`\`\`

---

## 5. テストディレクトリ構成

\`\`\`
tests/
│── unit/             # ユニットテスト
│   │── test_system.rs
│   │── test_editor.rs
│── integration/      # 結合テスト
│   │── test_full_system.rs
│── ui/               # TUIスナップショットテスト
│   │── test_render.rs
\`\`\`

---

このドキュメントとテスト戦略を基に、開発を進める。
