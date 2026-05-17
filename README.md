# FDI ve Enflasyonun Ekonomik Büyüme Üzerine Etkisi
### G20 Ülkeleri için Panel Veri Analizi (2014–2022)

[![R](https://img.shields.io/badge/R-4.0%2B-blue?logo=r)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/Status-Academic%20Research-green)]()

---

## Proje Özeti

Bu çalışma, **Yabancı Doğrudan Yatırım (FDI)** ve **enflasyonun** G20 ülkelerinin ekonomik büyümesi üzerindeki etkisini panel veri yöntemiyle analiz etmektedir. Mevcut literatürde COVID-19, sonrasındaki toparlanma ve 2022 Enerji krizi döneminin bu ilişkiye etkisi yeterince ele alınmadığı için bu çalışma, **COVID öncesi ve sonrası dönemleri ayırt ederek** ilişkiyi ölçmeyi amaçlamaktadır.

### Araştırma Sorusu
> *FDI ve enflasyon, G20 ülkelerinin ekonomik büyümesini ne yönde ve ne ölçüde etkilemektedir?*

---

## Yazarlar

| Ad Soyad | Kurum | İletişim |
|----------|-------|----------|
| **Burak Dinç** | Marmara Üniversitesi | — |
| **Emirhan Acar** | Marmara Üniversitesi | emiracar259-del |
| **Burak Zeytin** | Marmara Üniversitesi | Burak561 |

---

## 🔬 Metodoloji

- **Model:** Sabit Etkiler (Fixed Effects) panel regresyonu
- **Model Seçimi:** Hausman testi (H₀ reddedilerek FE modeli tercih edilmiştir)
- **Dönüşümler:**
  - `IHS` (Inverse Hyperbolic Sine) → FDI değişkenine (negatif değerler içerdiği için)
  - `log` → GDP değişkenine (ölçek farklarını gidermek için)
- **Aykırı Değer Kontrolü:** Robust Scaler yöntemi, Cook uzaklığı analizi, Leverage yöntemi
- **Yapısal Kırılma:** COVID-19 ve sonrası dönem için üç kukla değişken:
  - `D_COVID` → Pandemi şoku (2020)
  - `D_RECOVERY` → Toparlanma dönemi / baz etkisi (2021)
  - `D_2022` → Rusya-Ukrayna kaynaklı enerji krizi (2022)
---

## 📊 Veri Seti

| Özellik | Detay |
|---------|-------|
| **Kaynak** | World Bank – World Development Indicators (WDI) |
| **Erişim** | [Kaggle veri tabanı](https://www.kaggle.com/datasets/haiderkraheem/world-development-indicators) |
| **Dönem** | 2014 – 2022 (yıllık frekans) |
| **Birim** | G20 ülkeleri + Hollanda (AB temsilcisi olarak) |
| **Gözlem** | 171 (aykırı değer hariç: 153) |

### Değişkenler

| Değişken | Açıklama | Birim | Rol |
|----------|----------|-------|-----|
| `gdp_growth` | GDP büyüme oranı | % | **Bağımlı** |
| `ihs_fdi` | FDI net girişi (IHS dönüşümlü) | IHS(USD) | Ana Açıklayıcı |
| `inflation` | Enflasyon (GDP deflatörü) | % | Ana Açıklayıcı |
| `inv` | Yurtiçi yatırım (GCF) | % GDP | Kontrol |
| `export` | İhracat | % GDP | Kontrol |
| `import_` | İthalat | % GDP | Kontrol |
| `pop_growth` | Nüfus büyümesi | % | Kontrol |
| `ln_gdp` | Ekonomi büyüklüğü (log) | log(USD) | Kontrol |

---

## Temel Bulgular

- **FDI** tüm modellerde istatistiksel olarak **anlamsızdır.**
- **Yurtiçi yatırım (`inv`)** ve **ihracat (`export`)** tüm modellerde **pozitif ve anlamlıdır** — G20 büyümesinin en güvenilir belirleyicileridir.
- **COVID-19 şoku, sonrası toparlanma dönemi ve Rusya-Ukrayna kaynaklı enerji krizi** birlikte modeldeki varyansın **%89,4'ünü** açıklamakta; bu durum enflasyonun gerçek etkisini "zayıflatmaktadır".
- COVID yılları çıkarıldığında (2014–2019), **enflasyonun büyüme üzerinde negatif ve anlamlı etkisi** netleşmektedir.
- **Argentina ve Türkiye** aşırı enflasyon değerleri nedeniyle aykırı değer olarak tespit edilmiş; çıkarıldığında Adj-R² 0,649 → 0,674'e yükselmiştir.

---

## Kullanılan Araçlar

- **R** (≥ 4.0)
- **R Markdown** (raporlama)
- Temel paketler: `plm`, `lmtest`, `sandwich`, `ggplot2`, `dplyr`, `tidyr`

---
