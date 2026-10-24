# Nexus Editor

An offline-first, distraction-free desktop word processor for Windows, inspired by Apple Pages.

---

## 🌟 Philosophy & Architecture

Nexus Editor pairs the tactile precision of Swiss and Apple design with the speed and privacy of local-first computing:

- **Zero Telemetry & Local Storage**: No mandatory cloud accounts or tracking. Documents are stored locally as compressed `.nexus` files (Gzip-compressed ProseMirror JSON AST).
- **Decoupled Inspector System**: The editor canvas remains clean and uncluttered; formatting controls reside in a contextual floating/docked inspector panel.
- **Physical A4 Layout**: High-fidelity page dimensions (794px × 1123px at 96 DPI) with 1-inch standard margins, smooth zoom scaling, and page shadow aesthetics.
- **Apple Pages-Style Workspace**: Minimalist dark dashboard with categorized libraries (Recents, Browse, Shared, Recently Deleted) and an interactive Template Chooser modal.

---

## 🛠️ Tech Stack

- **Native Shell**: [Tauri v2](https://v2.tauri.app/) (Rust) targeting native Windows (`.exe`)
- **Frontend**: [React 19](https://react.dev/) + [TypeScript](https://www.typescriptlang.org/) + [Vite](https://vitejs.dev/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/) with macOS/Apple dark palette tokens
- **Editor Engine**: Headless [Tiptap](https://tiptap.dev/) (ProseMirror)
- **UI Components**: [Radix UI](https://www.radix-ui.com/) primitives + [Lucide Icons](https://lucide.dev/)
- **Compression**: Native Rust Gzip compression engine for `.nexus` files

---

## 📁 Repository Structure

```
├── src-tauri/                       # Native Rust Tauri shell
│   ├── src/
│   │   ├── fs.rs                    # Native .nexus Gzip compressed file I/O
│   │   ├── lib.rs                   # Tauri command registration
│   │   └── main.rs                  # Native application entry point
│   ├── capabilities/default.json    # Tauri v2 security capabilities
│   └── tauri.conf.json              # Window frame & Tauri configuration
├── src/
│   ├── assets/                      # Application icons and branding
│   ├── components/
│   │   ├── canvas/                  # A4 paper container & editor viewport
│   │   ├── dashboard/               # Apple Pages workspace & template chooser
│   │   └── inspector/               # Contextual floating inspector panel
│   ├── data/
│   │   └── templates.ts             # Template dataset (Reports, Books, CVs, etc.)
│   ├── extensions/image/            # Custom resizable image node & React NodeView
│   ├── hooks/                       # Editor initialization & auto-save hooks
│   ├── lib/                         # Window control helpers & Tailwind utils
│   ├── services/                    # Local storage & document templates
│   └── types/                       # Shared TypeScript interfaces
└── index.html                       # Base HTML entry point
```

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18+)
- [Rust & Cargo](https://rustup.rs/) (latest stable)
- Visual Studio C++ Build Tools (for Windows native compilation)

### Development

1. Install frontend dependencies:
   ```bash
   npm install
   ```

2. Run in development mode (Vite frontend server):
   ```bash
   npm run dev
   ```

3. Launch Tauri desktop app:
   ```bash
   npm run tauri dev
   ```

4. Build production bundle:
   ```bash
   npm run build
   npm run tauri build
   ```

---

## 📄 License

MIT
