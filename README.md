# ReinforcementDeepLearning

![reinforcement](https://github.com/user-attachments/assets/b9f0d7c6-69ba-400d-93b4-4575c582dd74)
# 🧠 RL-YOLOv8 Görüntü Etiketleme Otomasyonu

Bu proje, YOLOv8 nesne tespiti ile güçlendirilmiş bir Görüntü Etiketleme Otomasyon sistemidir. Takviye öğrenmesi (Reinforcement Learning) ile geliştirilen bir ajan, tespit edilen görüntülerin **otomatik kabul**, **manuel inceleme** veya **atla** gibi kararlarını verir.

## 🚀 Özellikler

- 🔍 YOLOv8 ile görüntülerde nesne tespiti
- 🧠 DQN tabanlı RL ajanı ile karar verme mekanizması
- 📦 Görüntüleri `auto_accepted`, `manual_review`, `skipped` klasörlerine ayırır
- 🗂️ YOLO formatında otomatik etiketleme
- 🧪 Simüle edilmiş ödül sistemi ile ajan eğitimi
- 📊 Eğitim süreci boyunca konsola çıktı alma
- 💾 Eğitilmiş ajanı kaydetme ve tekrar kullanabilme

## 📸 Örnek Görsel

<p align="center">
  <img src="https://user-images.githubusercontent.com/your-example-image.png" width="600" alt="YOLOv8 Detection Example">
</p>

## 📂 Klasör Yapısı

## 📁 Proje Klasör Yapısı

<pre>```bash
project/
├── rl_agent.pth                   # 🎯 Eğitilmiş RL ajan modeli (PyTorch formatında)
├── output_labels/                 # 📦 Etiketlenmiş çıktı klasörü
│   ├── auto_accepted/             # ✅ Otomatik kabul edilen görüntüler ve YOLO etiket dosyaları
│   ├── manual_review/             # 🕵️‍♂️ Manuel inceleme gerektiren görüntüler
│   └── skipped/                   # ⏭️ Atlanan, işlem yapılmayan görüntüler
├── /content/drive/                # 💾 Google Drive yolu (Colab için)
│   └── MyDrive/
│       ├── yolov8_model.pt        # 🧠 YOLOv8 model dosyası (eğitimli)
│       └── RL deep/train/images/  # 🖼️ Eğitim sırasında işlenecek ham görüntüler
└── main.py                        # 🐍 Ana çalışma dosyası (RL ajan + YOLO çalıştırıcısı)
</pre>


## 🛠️ Gereksinimler

Aşağıdaki kütüphaneleri yüklemeniz gerekmektedir:

<pre>```bash
pip install torch torchvision opencv-python pillow numpy ultralytics
</pre>

## 🤖 Ajanın Karar Mekanizması

YOLOv8 çıktısına göre etiketlenecek görüntünün ortalama güven skoruna göre RL ajanı aşağıdaki kararlardan birini verir:

| Ortalama Güven Skoru         | Ajanın Kararı       | Açıklama                                         |
|------------------------------|---------------------|--------------------------------------------------|
| > 0.7                        | ✅ Otomatik Kabul    | Etiket direkt sistem tarafından onaylanır        |
| 0.4 - 0.7 arası              | 🕵️ Manuel İnceleme  | Etiket kullanıcının onayına sunulur             |
| ≤ 0.4 veya hiç tespit yok    | ⏭️ Atla              | Görüntü geçilir, etiketleme yapılmaz             |


## 🏁 Eğitim Parametreleri

Ajanın eğitimi sırasında kullanılan hiperparametreler aşağıdaki gibidir:

| Parametre                  | Değer   |
|----------------------------|---------|
| Memory Size               | 5000    |
| Batch Size                | 32      |
| Gamma (Discount Factor)   | 0.99    |
| Epsilon Başlangıcı        | 1.0     |
| Epsilon Minimum           | 0.01    |
| Epsilon Azalış Katsayısı  | 0.995   |
| Öğrenme Oranı (LR)        | 0.001   |
| Epoch Sayısı              | 3       |
---------------------------------------
<br>![images](https://github.com/user-attachments/assets/fee7aeff-05c7-4042-a3ae-fc4a763f0dee)
<br>
