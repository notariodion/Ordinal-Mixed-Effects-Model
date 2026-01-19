# Clinical Trial Visualization with Ordinal Mixed-Effects Model 

Repository ini berisi **skrip R lengkap** untuk:
1. **Simulasi data uji klinik**
2. **Analisis Ordinal Mixed-Effects Model (CLMM)**
3. **Visualisasi distribusi skor DASH dan PHQ-9**
   pada desain **pre-test–post-test dengan kelompok placebo dan test**

Script ini ditujukan sebagai **contoh reproducible workflow** untuk penelitian klinik dengan **outcome ordinal dan repeated measures**.

---

## Latar Belakang

Dalam penelitian klinis dan farmasi, instrumen seperti:
- **DASH** (Disabilities of the Arm, Shoulder and Hand)
- **PHQ-9** (Patient Health Questionnaire)

menghasilkan **data ordinal**, bukan numerik kontinu.  
Analisis yang tidak tepat (misalnya t-test) dapat menyebabkan **inferensi yang bias**.

Skrip ini menggunakan **Ordinal Mixed-Effects Model (Cumulative Link Mixed Model / CLMM)** untuk:
- menangani sifat ordinal data
- mengakomodasi korelasi intra-subjek (pre–post)
- menguji efek *treatment*, *time*, dan interaksinya

---

## Tujuan Repository

- Menyediakan **contoh simulasi data uji klinik** yang realistis
- Menunjukkan implementasi **CLMM menggunakan paket `ordinal`**
- Menyajikan **visualisasi distribusi kategori ordinal**
- Menjadi **template analisis** untuk penelitian klinik berbasis skala ordinal

---

## Desain Data Simulasi

- **Jumlah subjek**: 126
- **Kelompok**:  
  - Placebo (n = 63)  
  - Test (n = 63)
- **Pengukuran**:
  - Pre-test
  - Post-test
- **Outcome**:
  - DASH (5 tingkat ordinal)
  - PHQ-9 (4 tingkat ordinal)

Distribusi post-test pada kelompok *test* disimulasikan **lebih baik secara klinis** dibanding placebo.

---

## Model Statistik

Model utama yang digunakan:
Outcome ~ treatment × period + (1 | subject)


Dengan:
- *Outcome*: DASH atau PHQ-9 (ordinal)
- *treatment*: placebo vs test
- *period*: pre-test vs post-test
- *(1 | id)*: random intercept untuk subjek

Model diestimasi menggunakan **cumulative logit link** melalui fungsi `clmm()`.

---

## Visualisasi

Skrip menghasilkan:
- **Grouped bar chart** distribusi kategori ordinal
- Perbandingan **pre-test vs post-test**
- Ditampilkan terpisah untuk:
  - Placebo group
  - Test group

Visualisasi bertujuan **deskriptif**, bukan inferensial, dan selaras dengan sifat ordinal data.

---

## Packages yang Digunakan

- `ggplot2` – visualisasi
- `dplyr`, `tidyr` – manipulasi data
- `ordinal` – ordinal mixed-effects model
- `scales` – formatting persentase
- `gridExtra` – pengaturan layout (opsional)

Instalasi:
```r
install.packages(c("ggplot2", "dplyr", "tidyr", "ordinal", "scales", "gridExtra"))
```
# Struktur Skrip
├── data_simulation_and_analysis.R
├── plot1.png   # DASH visualization
├── plot2.png   # PHQ-9 visualization
└── README.md

# Output
- Ringkasan model CLMM untuk DASH dan PHQ-9
- Visualisasi distribusi skor pre–post
- File gambar resolusi tinggi (PNG, 300 dpi)

# Referensi
Agresti, A. (2010). Analysis of Ordinal Categorical Data. Wiley. https://onlinelibrary.wiley.com/doi/book/10.1002/9780470594001?msockid=1d905d87d53b66f3279a4e45d47e67a9 
Christensen, R. H. B. (2019). ordinal — Regression Models for Ordinal Data. R package. https://www.semanticscholar.org/paper/Cumulative-Link-Models-for-Ordinal-Regression-with-Haubo-Christensen/2130d63b9a6eab9612b97b0b738122a30d636227
Liu, L., & Hedeker, D. (2005). A mixed-effects regression model for longitudinal multivariate ordinal data. Biometrics, 62(1), 261–268. https://www.jstor.org/stable/3695729 

