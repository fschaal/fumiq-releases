# Fumiq

A cross-platform Azure Service Bus Explorer.

![Fumiq — peek messages](screenshots/peek-messages.png)

Fumiq lets you browse, inspect, and manage Azure Service Bus entities from a native desktop app. Built for developers who find the Azure Portal too slow and ServiceBusExplorer too Windows-centric. Support for other queue providers (RabbitMQ, Amazon SQS) is planned.

## Features

### Browse & Inspect

- Entity tree with live message counts for queues, topics, and subscriptions
- Peek messages without consuming them
- JSON and XML syntax highlighting with JSON tree view
- Message property inspection (system, application, custom)
- Automatic stack trace detection and formatting

![Message body with JSON highlighting](screenshots/message-body.png)

![Message properties](screenshots/message-properties.png)

### Send & Schedule

- Send messages with full metadata (content type, correlation ID, custom properties, etc.)
- Schedule messages with relative or absolute delivery times
- Bulk send with progress tracking

![Bulk send messages](screenshots/bulk-send.png)

### Edit & Resubmit

- Edit message body and properties, then resubmit
- Works from any tab — active messages, dead-letter queue, or deferred

### Dead Letter Management

- Peek and inspect dead-lettered messages
- Resubmit to the original entity or a different one
- Bulk delete and purge operations

![Dead letter queue](screenshots/dead-letter.png)

### Entity Management

- Create, update, and delete queues, topics, and subscriptions
- Manage subscription rules with SQL and correlation filters

### Advanced Features

- Session-aware browsing and message peeking
- Deferred message support
- Message filtering with 14+ operators
- Custom columns from application properties or JSON paths
- Export and import messages

![Filtered message table with custom columns](screenshots/filtered-table.png)

![Import messages dialog](screenshots/import-dialog.png)

### Keyboard-First

- Command palette (Cmd+K / Ctrl+K)
- Keyboard shortcuts throughout the app
- Fast entity search

![Command palette](screenshots/command-palette.png)

### Cross-Platform

- macOS, Windows, and Linux
- Native Rust backend — not Electron

### Getting Started

Connect to your Azure Service Bus namespace using a connection string or Azure AD.

![Add connection dialog](screenshots/add-connection.png)

## Installation

Download the latest release from the [releases page](https://github.com/fschaal/fumiq-releases/releases).

## Troubleshooting

### Linux: WebKitGTK crash on systems with Intel Arc GPUs

Fumiq uses WebKitGTK for rendering on Linux. On systems with Intel Arc GPUs (e.g. Intel Ultra 7/9 series), the WebKit renderer may crash due to DMA-BUF buffer sharing issues between Mesa and WebKitGTK on Wayland.

**Symptoms:** The app crashes with a `WebKitWebProcess` SIGABRT in system logs.

**Fix:** Fumiq automatically disables the DMA-BUF renderer on Linux to prevent this crash. If you're on an older version, update to the latest release.

If the crash persists, try also disabling GPU compositing by launching Fumiq with:

```bash
WEBKIT_DISABLE_COMPOSITING_MODE=1 fumiq
```

This is a known upstream issue with Intel Arc drivers and WebKitGTK, not a bug in Fumiq.

## Website

For more information, pricing, and downloads, visit [fumiq.app](https://fumiq.app).

## License

Fumiq is proprietary software. See the [LICENSE](LICENSE) file for details.
