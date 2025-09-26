# Neeko AI Toy — Hardware & Firmware

Sesle etkileşimli, Wi-Fi / BLE ile internete bağlanabilen ve sunucu tabanlı zekâsı olan akıllı oyuncak için firmware.

---

## 🚦 Yol Haritası (Checkpoint Tabanlı)
- **Checkpoint-0**: 🎤 → 🔊 I2S loopback (mikrofon → hoparlör test)  
- Checkpoint-1: Wi-Fi bağlantısı + WebSocket iskeleti  
- Checkpoint-2: Sesin WebSocket üzerinden gönderilmesi  
- Checkpoint-3: Sunucudan gelen sesin çalınması  
- Checkpoint-4+: Wakeword, güç yönetimi, BLE provisioning, zekâ entegrasyonu  

---

## 📂 Repo Yapısı
voice-toy/
├── main/ # Uygulama kaynak kodu
│ ├── main.c # Checkpoint-0 loopback pipeline
│ └── app_config.h
├── tools/ # Flash ve monitor scriptleri
├── CMakeLists.txt
├── sdkconfig.defaults
└── README.md

bash
Kodu kopyala

---

## ⚡️ Kurulum


git clone --recursive https://github.com/espressif/esp-adf
export ADF_PATH=$PWD/esp-adf
export IDF_PATH=$PWD/esp-idf
. $IDF_PATH/export.sh

# Repo'yu klonla
git clone https://github.com/erdalgumuss/neeko-ai-toy-hardware
cd neeko-ai-toy-hardware
Board seçimi:


idf.py menuconfig
# → Audio HAL → ESP32-LyraT-Mini
▶️ Çalıştırma
bash
Kodu kopyala
chmod +x tools/*.sh
./tools/flash.sh
./tools/monitor.sh
Test: Mikrofona konuş → hoparlörden geri gelmeli.
Hedef: <150 ms gecikme, kesinti olmadan ≥5 dk çalışmalı.

✅ Definition of Done (Checkpoint-0)
 Ses mikrofondan hoparlöre geliyor

 Crash / buffer underrun yok

 En az 5 dk stabil çalışıyor

📌 Lisans
MIT (ileride değişebilir)
