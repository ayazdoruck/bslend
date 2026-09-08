# Bslend

A LocalSend-style cross-platform Flutter app that automatically discovers iOS
and Windows devices on the same local network and transfers files between them.

## How it works

- Devices discover each other automatically over UDP broadcast — no IP address
  to type in.
- Sending happens in two stages: the receiver is asked to accept or reject
  first, and only then is the file streamed over HTTP.
- The same Flutter codebase runs on both iOS and Windows desktop.

## Features

- **Automatic discovery** — peers on the same network are found via UDP broadcast
- **Confirmed transfers** — nothing is sent until the receiver accepts
- **Streamed sending** — large files are transferred in chunks over HTTP with live progress
- **Localised UI** — English, Turkish, Russian and Chinese
- **One codebase** — iOS and Windows build from the same Flutter project

## Project layout

```
lib/services/discovery_service.dart   # peer discovery over UDP broadcast
lib/services/transfer_server.dart     # HTTP server receiving incoming transfers
lib/services/transfer_client.dart     # outgoing transfers
lib/models/                           # Peer, TransferTask, DiscoveryStatus
lib/screens/                          # UI screens
lib/l10n/                             # translation files (.arb)
```

## Development

```bash
flutter pub get
flutter run -d windows   # desktop
flutter run              # connected iOS device
```

## Requirements

- Flutter SDK ^3.12.2
- Visual Studio (Desktop development with C++) for Windows builds
- Xcode for iOS builds

Both devices must be on the **same local network**, and the firewall has to
allow UDP broadcast.

## License

[MIT](LICENSE)
