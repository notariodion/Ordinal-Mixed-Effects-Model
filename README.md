# Ordinal-Mixed-Effects-Model
# Ordinal Mixed-Effects Model in R

Repository ini berisi **contoh implementasi Ordinal Mixed-Effects Model** menggunakan bahasa **R**, dengan fokus pada **Cumulative Link Mixed Models (CLMM)** untuk data **ordinal longitudinal** (pre–post, repeated measures).

Model ini sangat relevan untuk penelitian di bidang:
- kesehatan dan klinik
- farmasi dan farmakologi
- psikologi dan ilmu sosial
- pendidikan dan ilmu perilaku

terutama ketika **outcome bersifat ordinal** dan **subjek diukur lebih dari satu kali**.

---

## Latar Belakang

Dalam banyak penelitian klinis dan sosial, variabel hasil sering kali diukur dalam **skala ordinal**, misalnya:
- tingkat keparahan penyakit (normal, ringan, sedang, berat)
- skor kuesioner (PHQ-9, DASH, Likert scale)
- klasifikasi klinis berbasis kategori

Penggunaan metode parametrik seperti **t-test** atau **linear mixed models** pada data ordinal dapat menghasilkan **inferensi yang bias**.

**Ordinal Mixed-Effects Model** (khususnya CLMM) memungkinkan:
- pemodelan outcome ordinal secara tepat
- pengendalian korelasi intra-subjek (repeated measures)
- estimasi efek perlakuan dan interaksi waktu secara valid

---

##  Tujuan Repository

Repository ini dibuat untuk:
- memberikan **pengantar konseptual** Ordinal Mixed-Effects Model
- menyediakan **contoh skrip R siap pakai**
- membantu peneliti memahami **interpretasi output CLMM**
- menjadi **template analisis** untuk studi pre–post dengan kelompok kontrol

---

## Model Statistik

Model utama yang digunakan:

\[
\text{Outcome}_{ij} \sim \text{Treatment}_i \times \text{Period}_j + (1 | \text{Subject}_i)
\]

dengan:
- *Outcome* : variabel ordinal (misalnya DASH, PHQ-9)
- *Treatment* : placebo vs test
- *Period* : pre-test vs post-test
- *(1 | Subject)* : random intercept untuk subjek

Model diestimasi menggunakan **cumulative logit link**.

---

## Tools & Packages

Analisis dilakukan menggunakan paket R berikut:

- `ordinal` – fitting cumulative link mixed models
- `tidyverse` – manipulasi dan visualisasi data
- `lme4` *(opsional)* – perbandingan dengan model linear
- `ggplot2` *(opsional)* – visualisasi hasil

Instalasi paket:
```r
install.packages("ordinal")
