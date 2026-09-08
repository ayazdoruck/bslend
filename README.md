# Bslend

Aynı yerel ağdaki iOS ve Windows cihazları otomatik olarak bulup aralarında hızlı dosya aktarımı yapan, LocalSend tarzı, cross-platform bir Flutter uygulaması.

## Nasıl çalışır?

- Cihazlar UDP broadcast ile birbirini otomatik keşfeder (IP girmeye gerek yok).
- Dosya gönderimi iki aşamalıdır: önce alıcıya kabul/red sorulur, kabul edilirse dosya HTTP üzerinden akış halinde gönderilir.
- Aynı Flutter kod tabanı hem iOS hem Windows masaüstünde çalışır.

## Geliştirme

```
flutter pub get
flutter run -d windows   # PC tarafı
flutter run               # bağlı iOS cihazında
```

## Özellikler

- **Otomatik keşif** — UDP broadcast ile aynı ağdaki cihazlar IP girmeden bulunur
- **Onaylı aktarım** — alıcı kabul etmeden dosya gönderilmez
- **Akış tabanlı gönderim** — büyük dosyalar HTTP üzerinden parça parça aktarılır, ilerleme anlık gösterilir
- **Çok dilli arayüz** — Türkçe, İngilizce, Rusça, Çince
- **Tek kod tabanı** — iOS ve Windows aynı Flutter projesinden derlenir

## Proje yapısı

```
lib/services/discovery_service.dart   # UDP broadcast ile cihaz keşfi
lib/services/transfer_server.dart     # gelen aktarımları karşılayan HTTP sunucusu
lib/services/transfer_client.dart     # giden aktarımlar
lib/models/                           # Peer, TransferTask, DiscoveryStatus
lib/screens/                          # arayüz ekranları
lib/l10n/                             # çeviri dosyaları (.arb)
```

## Gereksinimler

- Flutter SDK ^3.12.2
- Windows derlemesi için Visual Studio (Desktop development with C++)
- iOS derlemesi için Xcode

Her iki cihaz da **aynı yerel ağda** olmalı ve güvenlik duvarı UDP broadcast'e
izin vermelidir.

## Lisans

[MIT](LICENSE)
