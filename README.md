# 🚕 NYC Yellow Taxi — Spatiotemporal Demand Forecasting

A pattern recognition project that forecasts hourly taxi pickup demand across 263 NYC locations using 110M+ raw trip records (2023–2025).

## Pipeline
| Step | Technique |
|------|-----------|
| Data Ingestion | Aggregate-First Chunking (OOM-safe, 110M rows) |
| Feature Engineering | Cyclical encoding, lag/rolling features, holiday flags |
| Modeling | GPU LightGBM + Optuna Bayesian hyperparameter tuning |
| Validation | Chronological split + Walk-Forward cross-validation |
| Interpretability | SHAP beeswarm, feature importance, spatial analysis |

## Data Split
- **Train**: Jan 2023 – Dec 2024
- **Validation**: Jan 2025 – Sep 2025 (Optuna tuning)
- **Test**: Oct 2025 – Dec 2025 (Thanksgiving, Christmas, New Year)

## Key Design Choices
- `log1p` transform on target to handle skewed demand distribution
- Zero-padding to 263 × 26,304 hourly grid for well-defined lag features
- `lag_1`, `lag_24`, `lag_168` correlations: **r = 0.961 / 0.932 / 0.954**

## Output Figures
| Folder | Contents |
|--------|----------|
| `outputs/eda/` | Target distribution, temporal patterns, spatial heterogeneity, lag correlations |
| `outputs/figures/` | Hourly/weekly/seasonal trend figures |
| `outputs/model/` | Actual vs predicted, SHAP, Optuna history, walk-forward validation |

## Stack
`Python` · `LightGBM` · `Optuna` · `SHAP` · `pandas` · `pyarrow` · `scikit-learn` · `matplotlib`

---

> Course: Pattern Recognition — Kaggle Notebook

---
---

# 🚕 NYC Sarı Taksi — Uzamsal-Zamansal Talep Tahmini

2023–2025 yılları arasında 110M+ ham seyahat kaydı kullanılarak NYC'deki 263 lokasyonda saatlik taksi talep tahmini yapan bir örüntü tanıma projesi.

## Pipeline
| Adım | Teknik |
|------|--------|
| Veri Yükleme | Aggregate-First Chunking (bellek dostu, 110M satır) |
| Özellik Mühendisliği | Döngüsel kodlama, gecikme/kayan pencere özellikleri, tatil bayrakları |
| Modelleme | GPU LightGBM + Optuna Bayesian hiperparametre optimizasyonu |
| Doğrulama | Kronolojik bölme + Walk-Forward çapraz doğrulama |
| Yorumlanabilirlik | SHAP beeswarm, özellik önemi, uzamsal analiz |

## Veri Bölümü
- **Eğitim**: Ocak 2023 – Aralık 2024
- **Doğrulama**: Ocak 2025 – Eylül 2025 (Optuna tuning)
- **Test**: Ekim 2025 – Aralık 2025 (Şükran Günü, Noel, Yılbaşı)

## Önemli Tasarım Kararları
- Çarpık talep dağılımını dengelemek için hedef değişkende `log1p` dönüşümü
- İyi tanımlı gecikme özellikleri için 263 × 26.304 saatlik tam ızgaraya sıfır dolgusu
- `lag_1`, `lag_24`, `lag_168` korelasyonları: **r = 0.961 / 0.932 / 0.954**

## Çıktı Grafikleri
| Klasör | İçerik |
|--------|--------|
| `outputs/eda/` | Hedef dağılımı, zamansal örüntüler, uzamsal heterojenlik, gecikme korelasyonları |
| `outputs/figures/` | Saatlik/haftalık/mevsimsel trend grafikleri |
| `outputs/model/` | Gerçek vs tahmin, SHAP, Optuna geçmişi, walk-forward doğrulama |

## Teknoloji
`Python` · `LightGBM` · `Optuna` · `SHAP` · `pandas` · `pyarrow` · `scikit-learn` · `matplotlib`

---

> Ders: Örüntü Tanıma — Kaggle Notebook
