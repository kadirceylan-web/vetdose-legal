# VetDose iOS - App Store Release Blockers

Updated: 2026-02-16

## P0 (Submission önce kesin çözülmeli)

1. Medical guideline risk (`App Store Review Guidelines 1.4.2`)
   - Drug dosage calculator apps Apple tarafından "approved entity" şartına bağlanıyor.
   - Aksiyon:
     - App Store Connect'te publisher bilgisi kurumsal/klinik kimlikle eşleşmeli.
     - Review Notes içine klinik sorumluluk, veri kaynakları ve güncelleme metodolojisi net yazılmalı.

2. Legal links must be functional
   - Kodda link altyapısı hazır ama build-time URL verilmezse paywall'da linkler çalışmaz.
   - Aksiyon:
     - Build komutunda şu define'lar zorunlu:
       - `PRIVACY_POLICY_URL`
       - `TERMS_OF_USE_URL`
       - `SUPPORT_URL`

3. RevenueCat release key
   - `REVENUECAT_API_KEY` release build'de zorunlu.
   - Aksiyon:
     - `flutter build ios ... --dart-define=REVENUECAT_API_KEY=appl_...`
     - RevenueCat entitlement id (`pro`) ve offering (`default`) eşleşmesini yeniden test et.

## P1 (Güçlü şekilde önerilir)

1. Metadata URL kalitesi
   - Support URL e-posta değil, gerçek HTTPS sayfa olmalı.
   - Privacy + Terms URL farklı ve erişilebilir olmalı.

2. Review packet hazırlığı
   - Review Notes içine şu maddeler eklenmeli:
     - Uygulamanın yalnızca referans amaçlı olduğu
     - Klinik kararın veteriner hekime ait olduğu
     - Doz verilerinin düzenli doğrulama süreci
     - In-app purchase restore/manage akışı uygulama içinde mevcut olduğu

3. Subscription transparency
   - App Store Connect subscription localizations, review screenshot, ve billing textleri tamamlanmalı.
