<div align="center">

<img src="https://fumiq.app/logo-64.png" alt="Fumiq logo" width="80" />

# Fumiq

### The fast, visual Azure Service Bus explorer

A native desktop app for browsing queues and subscriptions, peeking and sending messages, and clearing dead-letters in seconds.

**macOS · Windows · Linux**

[**Download**](https://github.com/fschaal/fumiq-releases/releases/latest) · [Website](https://fumiq.app) · [Pricing](https://fumiq.app/#pricing) · [Changelog](https://fumiq.app/changelog)

<sub>Free 30-day trial · All features included · No credit card</sub>

<br />

<a href="https://fumiq.app/video/intro.mp4">
  <img src="screenshots/intro-poster.jpg" alt="Watch the Fumiq intro video" width="820" />
</a>

<sub>▶ <a href="https://fumiq.app/video/intro.mp4">Watch the 27-second intro</a></sub>

</div>

<br />

## ✨ Features

### 🌳 Browse & Inspect

- Entity tree with live message counts for queues, topics, and subscriptions
- Peek messages without consuming them
- JSON and XML syntax highlighting with collapsible tree view
- Full message property inspection (system, application, custom)
- Automatic stack trace detection and formatting

![Fumiq showing a namespace in the sidebar, a queue with peeked messages, and the JSON body of the selected message](screenshots/browse-and-peek.png)

![Fumiq showing a message with its JSON body expanded and syntax highlighted](screenshots/message-detail.png)

![Message properties](screenshots/message-properties.png)

### 📨 Send & Schedule

- Send messages with full metadata (content type, correlation ID, custom properties, etc.)
- Schedule messages with relative or absolute delivery times
- Bulk send with template engine: define variables, generate sequences, stress-test queues
- Placeholders like `{{index}}`, `{{guid}}`, `{{timestamp}}` and `{{random.int}}` make every message unique

![Fumiq's bulk send dialog with a JSON template using index, GUID and timestamp placeholders](screenshots/send-with-a-template.png)

### 🔧 Repair & Resubmit

- Edit message body and properties, then resubmit
- Fix malformed payloads directly from the dead-letter queue
- Works from any tab: active messages, dead-letter queue, or deferred

### 💀 Dead Letter Management

- Browse, inspect, and resubmit dead-lettered messages
- View dead-letter reason and error descriptions
- Bulk delete and purge operations

![Fumiq showing the dead-letter tab with failed messages selected and the actions menu open on Resubmit](screenshots/dead-letter-repair.png)

### 🏗️ Entity Management

- Create, update, and delete queues, topics, and subscriptions
- Manage subscription filter rules with SQL and correlation filters

### 📋 Custom Columns & Filtering

- Add columns for application properties or extract values from JSON bodies using JSONPath
- Resize, reorder, and persist layouts per entity
- Filter messages with a visual query builder and 14+ operators

![Filtered message table with custom columns](screenshots/filtered-table.png)

### 📦 Copy, Export & Import

- Copy messages between queues
- Export to JSON files or import messages from disk
- Move data across environments in seconds

![Import messages dialog](screenshots/import-dialog.png)

### ⚡ Bulk Operations

- Select multiple messages with checkboxes or Shift+click ranges
- Bulk delete, dead-letter, resubmit, or cancel scheduled messages in one action

### 🔒 Receive & Settle (PeekLock)

- Receive and lock messages without consuming them
- Settle individually: complete, abandon, or dead-letter with reason and description
- Lock timer countdown per message so you know when locks expire
- Works on both active queues and dead-letter queues

### 🔐 Authentication

- Connect with connection strings or Azure AD with RBAC
- Organize connections into folders with drag-and-drop

![Add connection dialog](screenshots/add-connection.png)

### 🎯 Advanced

- Session-aware browsing and message peeking
- Deferred message support
- Scheduled message management (view, cancel, purge)
- Auto-refresh with configurable intervals

### ⌨️ Keyboard-First

- Command palette (`Cmd+K` / `Ctrl+K`)
- Full keyboard navigation with shortcuts for all common actions
- Fast entity search

![Fumiq's command palette listing actions with their keyboard shortcuts](screenshots/command-palette.png)

### 💻 Cross-Platform & Native

- macOS, Windows, and Linux
- Native performance with minimal memory footprint

## 🔌 Supported Providers

- **Azure Service Bus**: full support for queues, topics, subscriptions, dead-letter queues, sessions, deferred messages, and more
- **RabbitMQ**: coming soon
- **Kafka, Amazon SQS, Google Pub/Sub**: on the horizon

## 📥 Installation

Download the latest build for your platform from the [releases page](https://github.com/fschaal/fumiq-releases/releases/latest). Fumiq updates itself after that.

## 🔧 Troubleshooting

<details>
<summary><b>Linux: WebKitGTK crash on systems with Intel Arc GPUs</b></summary>

<br />

Fumiq uses WebKitGTK for rendering on Linux. On systems with Intel Arc GPUs (e.g. Intel Ultra 7/9 series), the WebKit renderer may crash due to DMA-BUF buffer sharing issues between Mesa and WebKitGTK on Wayland.

**Symptoms:** The app crashes with a `WebKitWebProcess` SIGABRT in system logs.

**Fix:** Fumiq automatically disables the DMA-BUF renderer on Linux to prevent this crash. If you're on an older version, update to the latest release.

If the crash persists, try also disabling GPU compositing by launching Fumiq with:

```bash
WEBKIT_DISABLE_COMPOSITING_MODE=1 fumiq
```

This is a known upstream issue with Intel Arc drivers and WebKitGTK, not a bug in Fumiq.

</details>

## 📄 License

Fumiq is proprietary software. See the [LICENSE](LICENSE) file for details.
