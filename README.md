# VanaCam Clone — Phase 1

Project ini adalah fondasi APK Android untuk konsep VanaCam:
- pemilih video dari HP
- preview video
- play/pause/seek
- looping
- status virtual-camera
- target SDK 36 / Android 16

## Catatan penting

AOSP memang menyediakan arsitektur Virtual Camera yang memungkinkan aplikasi konsumen
Camera2/CameraX/camera1 menerima kamera virtual. Namun implementasi AOSP contoh
`VirtualCameraDemo` adalah aplikasi privileged/system (`platform_apis` + `privileged`),
bukan APK biasa.

Karena itu project ini sengaja memisahkan:
1. UI/player yang bisa berjalan sebagai APK normal.
2. VirtualCameraBridge yang pada fase berikutnya akan dibuat sebagai backend
   privileged atau jalur root/Magisk, tergantung perangkat.

## Target fase berikutnya

VIDEO FILE
  -> MediaCodec / Surface
  -> frame conversion YUV
  -> Virtual Camera producer
  -> Android Camera Framework
  -> TikTok / Camera2 consumer

Untuk perangkat yang tidak mengekspos virtual camera kepada aplikasi biasa,
jalur root/Magisk + Zygisk atau system integration diperlukan.

## Build

Buka folder ini di Android Studio/IDE yang mendukung Gradle Android Plugin 8.13,
atau gunakan GitHub Actions untuk menghasilkan APK.
