<div align="center">

# 🦴 Osteoprofile

### *Adli antropolojik biyolojik profile analiz platformu*

**Türk popülasyonu için valide edilmiş formüllerle cinsiyet, boy ve yaş tahmini**

## 🎯 Osteoprofile Nedir?

**Osteoprofile**, insan iskelet kalıntılarından **biyolojik profile** (cinsiyet, boy, ölüm yaşı) çıkarımı yapan, **Türk/Anadolu popülasyonu için bilimsel olarak valide edilmiş** formüllere dayalı modüler bir adli antropoloji yazılımıdır.

Adli vakalarda, arkeolojik kazılarda ve antropolojik araştırmalarda iskelet kalıntılarının kimliklendirilmesine yardımcı olmak üzere tasarlanmıştır. Tüm hesaplamalar **peer-reviewed literatürden** türetilmiştir ve her sonuç ilgili güven aralıklarıyla birlikte sunulur.

### 💡 Neden "Osteoprofile"?

- **Osteo** (ὀστέον) — Yunanca *"kemik"*
- **profile** — Biyolojik profile *(sex · stature · age-at-death)*

> 🔍 **Kritik bilimsel bulgu:** Klasik Trotter-Gleser White formülleri Türk bireylerde ortalama **+4 cm aşırı tahmin** yapar (*Duyar & Pelin, 2003 — J Forensic Sci*). Osteoprofile, Türk/Anadolu örneklemleriyle valide edilmiş katsayıları kullanarak bu sistematik hatayı ortadan kaldırır.

---

## ✨ Özellikler

| Modül | Açıklama | Kaynaklar |
|:-:|---|---|
| 🧬 **Cinsiyet Tahmini** | Femur VHD + humerus başı analizi, Türk popülasyonu eşikleri | Askan 2007, Ekizoglu 2015 |
| 📐 **Boy Tahmini** | 5 uzun kemik (Femur, Tibia, Fibula, Humerus, Radius) | Duyar-Pelin 2003, Michopoulou 2017 |
| 🕐 **Yaş Tahmini** | Pubis sempfizisi + Auricular yüzey + Kranial sutur (çoklu birleştirme) | Suchey-Brooks 1990, Lovejoy 1985 |
| 📊 **Görselleştirme** | Örtüşme zonları, güven aralıkları, yöntem karşılaştırması | Matplotlib |
| 🎯 **Belirsizlik Analizi** | "Belirsiz" zonu matematiksel ve görsel tanımı | — |
| 📑 **Raporlama** | PDF/metin rapor çıktısı | *(geliştirme aşamasında)* |
| 🔬 **Modüler Mimari** | Core/UI/Visualization ayrımı, birim testler | Python |

---

## 🚀 Hızlı Başlangıç

### Kurulum

```bash
# 1. Depoyu klonla
git clone https://github.com/<kullanici-adi>/osteoprofile.git
cd osteoprofile

# 2. Sanal ortam oluştur (önerilir)
python -m venv venv
source venv/bin/activate       # Linux/macOS
# venv\Scripts\activate        # Windows

# 3. Bağımlılıkları yükle
pip install -r requirements.txt

# 4. Uygulamayı başlat
streamlit run program/app.py
```

Uygulama otomatik olarak tarayıcınızda `http://localhost:8501` adresinde açılacaktır. 🎉

### İlk Analiz

1. Sol menüden **üç sekme** arasında geçiş yapın: `⚧ Cinsiyet` · `📐 Boy` · `🕐 Yaş`
2. Kemik ölçümlerinizi ilgili alanlara girin
3. **🔬 Analiz Et** butonuna tıklayın
4. Sonuçları güven aralıklarıyla birlikte görsel olarak inceleyin

---

## 📂 Proje Yapısı

```
osteoprofile/
│
├── 📄 README.md              ← Bu dosya
├── 📄 LICENSE                ← MIT Lisansı
├── 📄 requirements.txt       ← Python bağımlılıkları
├── 📄 setup.py               ← Paket kurulumu
│
├── 📁 docs/                  ← Dokümantasyon
│   ├── ACIKLAMA.md           ← Detaylı proje açıklaması
│   ├── METHODOLOGY.md        ← Bilimsel metodoloji
│   ├── REFERENCES.md         ← Akademik kaynaklar
│   └── CHANGELOG.md          ← Versiyon geçmişi
│
├── 📁 program/               ← Ana uygulama
│   ├── app.py                ← Giriş noktası
│   ├── 📁 core/              ← Bilimsel hesaplama motoru
│   │   ├── constants.py
│   │   ├── sex_estimation.py
│   │   ├── stature_estimation.py
│   │   └── age_estimation.py
│   ├── 📁 ui/                ← Arayüz bileşenleri
│   ├── 📁 visualization/     ← Grafik fonksiyonları
│   └── 📁 utils/             ← Yardımcı araçlar
│
├── 📁 data/                  ← Formül tabloları (JSON)
│   └── references/
│
└── 📁 tests/                 ← Birim testler
```

---

## 📊 Desteklenen Analizler

### Cinsiyet Tahmini

| Gösterge | Ortalama (Türk E) | Ortalama (Türk K) | Doğruluk |
|---|:-:|:-:|:-:|
| Femur Vertikal Baş Çapı | 48.8 mm | 43.4 mm | ~%90-95 |
| Humerus Baş Çapı | ~48 mm | ~42 mm | ~%90 |
| **Kombine (çoklu gösterge)** | — | — | **%95+** |

### Boy Tahmini Formülleri

**Erkek (Trotter-Gleser Mongoloid — Türk validate)**

| Kemik | Formül | SE |
|:-:|:-:|:-:|
| Femur | 2.15 × F + 72.57 | ±3.80 |
| Tibia | 2.39 × T + 81.45 | ±3.24 |
| Fibula | 2.40 × Fib + 80.56 | ±3.24 |
| Humerus | 2.68 × H + 83.19 | ±4.16 |
| Radius | 3.54 × R + 82.00 | ±4.60 |

**Kadın (Trotter-Gleser White Female — Türk için önerilen)**

| Kemik | Formül | SE |
|:-:|:-:|:-:|
| Femur | 2.47 × F + 54.10 | ±3.72 |
| Tibia | 2.90 × T + 61.53 | ±3.66 |
| Fibula | 2.93 × Fib + 59.61 | ±3.57 |
| Humerus | 3.36 × H + 57.97 | ±4.45 |
| Radius | 4.74 × R + 54.93 | ±4.24 |

### Yaş Tahmini Yöntemleri

| Yöntem | Evre | Yaş Aralığı | Güvenilirlik |
|:-:|:-:|:-:|:-:|
| Pubis Sempfizisi (Suchey-Brooks) | 1–6 | 18–87 | ⭐⭐⭐⭐⭐ |
| Auricular Yüzey (Lovejoy) | 1–8 | 20–80 | ⭐⭐⭐⭐ |
| Kranial Sutur (Meindl-Lovejoy) | 0–21 skor | 19–85 | ⭐⭐⭐ |

> 🧮 **Çoklu yöntem birleştirme:** `Birleşik = Σ(yaş × w) / Σw`, `w = 1/SD²`
> Düşük standart sapmalı (daha hassas) yöntemler otomatik olarak daha ağırlıklı hesaplanır.

---

## 📚 Dokümantasyon

| Belge | İçerik |
|---|---|
| 📖 [**ACIKLAMA.md**](docs/ACIKLAMA.md) | Proje vizyonu, hedefler, kullanım senaryoları |
| 🔬 [**METHODOLOGY.md**](docs/METHODOLOGY.md) | Bilimsel yöntemler, formül türetimleri, istatistik |
| 📑 [**REFERENCES.md**](docs/REFERENCES.md) | Tam akademik bibliyografya (30+ kaynak) |
| 📝 [**CHANGELOG.md**](docs/CHANGELOG.md) | Versiyon geçmişi ve değişiklikler |

---

## 🧪 Test

```bash
# Tüm testleri çalıştır
pytest tests/

# Sadece cinsiyet modülü testleri
pytest tests/test_sex.py -v

# Kapsam raporu
pytest --cov=program tests/
```

---

## 🗺️ Yol Haritası

### ✅ v1.0 — Mevcut Sürüm
- Cinsiyet, boy, yaş tahmini modülleri
- Türk popülasyonu formülleri
- Temel görselleştirmeler
- "Belirsiz" zon analizi
- Modüler mimari

### 🔄 v1.1 — Yakın Gelecek
- [ ] PDF rapor çıktısı
- [ ] CSV ile toplu vaka işleme
- [ ] Sağır (2000) formüllerinin bağımsız seçeneği
- [ ] Özaslan (2003) alt ekstremite formülleri

### 🔮 v1.2 — Planlanan
- [ ] Subadult yaş tahmini (epifiz kaynaşması)
- [ ] Pelvis morfolojisi (Phenice 1969)
- [ ] Kranial cinsiyet tahmini (Ekizoglu 2016)
- [ ] Bayesian yaklaşım (Godde 2025)

### 🚀 v2.0 — Uzun Vadeli
- [ ] Makine öğrenmesi sınıflandırıcılar
- [ ] 3D CT entegrasyonu
- [ ] Çok dilli arayüz (TR/EN)
- [ ] Türk-spesifik popülasyon veritabanı
- [ ] FORDISC benzeri ankestri tahmini

---

## ⚠️ Sorumluluk Reddi

> **Osteoprofile yalnızca eğitim ve araştırma amaçlıdır.**

- ⚖️ Gerçek adli vakalarda **tek başına kullanılmamalıdır**
- 👨‍⚖️ Her adli antropolojik değerlendirme, **uzman bir adli antropolog** tarafından yapılmalıdır
- 📋 Tam iskelet incelemesi ve **çoklu gösterge** zorunludur
- 🏛️ Yazılımın sonuçları **bilirkişi raporu** niteliğinde değildir
- 📖 Sonuçlar **tavsiye niteliğindedir** ve hiçbir hukuki/tıbbi sorumluluk doğurmaz

---

## 🤝 Katkıda Bulunma

Katkılarınız memnuniyetle karşılanır! Özellikle aşağıdaki alanlarda:

- 🐛 **Hata bildirimleri** → [GitHub Issues](../../issues)
- 💡 **Özellik önerileri** → [GitHub Discussions](../../discussions)
- 🔬 **Yeni formüller** → Pull Request + kaynak makale
- 🌍 **Çeviri** → `docs/` altına yeni dil klasörü
- 📝 **Dokümantasyon** → İyileştirme PR'leri

### Katkı Adımları

```bash
# 1. Fork'layın ve klonlayın
git clone https://github.com/<kullanici-adi>/osteoprofile.git

# 2. Yeni branch oluşturun
git checkout -b feature/yeni-ozellik

# 3. Değişikliklerinizi yapın ve test edin
pytest tests/

# 4. Commit ve push yapın
git commit -m "feat: yeni özellik eklendi"
git push origin feature/yeni-ozellik

# 5. Pull Request açın
```

---

## 📖 Atıf

Eğer Osteoprofile'i akademik çalışmanızda kullanırsanız, lütfen şu şekilde atıf yapın:

```bibtex
@software{osteoprofile2026,
  title  = {Osteoprofile: Adli Antropolojik Biyolojik profile Analiz Platformu},
  author = {<Yazar Adı>},
  year   = {2026},
  url    = {https://github.com/<kullanici-adi>/osteoprofile},
  note   = {Türk popülasyonu için valide edilmiş formüllerle v1.0}
}
```

Ve temelinde bulunan orijinal çalışmaları da ayrıca atıflamayı unutmayın → [REFERENCES.md](docs/REFERENCES.md)

---

## 🛠️ Teknoloji Yığını

<div align="center">

| Kategori | Teknoloji |
|---|---|
| **Dil** | Python 3.9+ |
| **Web Framework** | Streamlit |
| **Görselleştirme** | Matplotlib, NumPy |
| **Hesaplama** | NumPy, SciPy |
| **Test** | pytest |
| **Dokümantasyon** | Markdown |
| **Veri Formatı** | JSON |

</div>

---

## 📄 Lisans

Bu proje **APACHE Lisansı** altında yayınlanmıştır. Detaylar için [LICENSE](LICENSE) dosyasına bakınız.

```
Apache License - Özgürce kullanın, dağıtın ve geliştirin.
```

---



<div align="center">

### 🦴 *"Kemikler konuşur, yeter ki dinleyenler olsun."* 🦴

**Osteoprofile ile iskelet kalıntıları hikayelerini anlatır.**

⭐ *Projeyi beğendiyseniz yıldızlamayı unutmayın!* ⭐

---

<sub>© 2026 Osteoprofile · MIT Licensed · Made with 🦴 for forensic science</sub>

</div>
