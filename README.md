# 📊 A/B Testi Raporu: Abonelik Ekranı Dönüşüm Oranı Karşılaştırması

---

## 1. 🎯 Testin Tanımı

### 🔍 Neyi Test Ediyoruz?
Bu A/B testinde, mobil uygulama üzerindeki abonelik teklif ekranının kullanıcı dönüşüm oranları üzerindeki etkisini test ediyoruz.

- **Grup A**: Kullanıcılara premium özelliklere erişmek için **$4.99’lık** standart abonelik ekranı gösteriliyor.
- **Grup B**: Aynı abonelik **%50 indirimli olarak ($2.49)** sunuluyor.

### ⚙️ Kullanılan A/B Testi Tasarımı
- **Tasarım tipi**: Klasik split A/B testi
- **Rastgele atama**: Kullanıcılar rastgele şekilde A ve B gruplarına atanmıştır.
- **Ölçülen metrik**: Dönüşüm oranı (abone olan kullanıcı oranı)

### 🔄 Gerçekleştirilen İşlev Değişikliği
- Arayüzde sadece fiyat bilgisi değiştirilmiş; akış ve içerik aynı.

### 📈 Akış Şeması (Metin Formatında)

Uygulama Açıldı
↓
Abonelik Ekranı Gösterildi
↓
Kullanıcı Grubu Belirleme (A/B)
↓
A → $4.99 fiyat
B → %50 indirim ($2.49)
↓
Kullanıcı Abone Oldu Mu?


---

## 2. 🧠 Problem ve Amaç

### 🤔 Problem
Kullanıcıların abonelik ekranında yeterince dönüşüm sağlamaması, uygulama gelirlerini düşürmektedir.

### 🎯 Amaç
Dönüşüm oranını artırmak için daha cazip bir fiyat (%50 indirim) sunarak kullanıcıları satın almaya yönlendirip yönlendiremeyeceğimizi anlamak.

---

## 3. 🔬 Hipotezler

- **H₀ (Null Hipotezi)**: Grup A ve Grup B dönüşüm oranları arasında anlamlı bir fark yoktur.  
  `p_A = p_B`

- **H₁ (Alternatif Hipotez)**: Grup A ve Grup B dönüşüm oranları arasında anlamlı bir fark vardır.  
  `p_A ≠ p_B`

---

## 4. 🧪 Kullanılan Test

- **İstatistiksel Test**: Ki-Kare Bağımsızlık Testi (Chi-Square Test)
- **Neden seçildi?**: Her iki değişken (grup ve dönüşüm) kategorik olduğu için uygun bir testtir.
- **Python kodu**:
```python
observed = pd.crosstab(df["test_group"], df["conversion"])
statistic, pvalue, dof, expected = stats.chi2_contingency(observed)

Test Sonucu:
Chi-squared statistic: 56.14

p-değeri: 0.0

Yorum: p < 0.05 olduğu için H₀ reddedilir. İki grup arasında istatistiksel olarak anlamlı bir fark vardır.

5. 📊 Sonuçların Analizi
Grup	Kullanıcı Sayısı	Dönüşüm Sayısı	Dönüşüm Oranı
A	9.975	172	%1,72
B	10.023	239	%2,38

Grup B’nin dönüşüm oranı, Grup A’ya göre belirgin şekilde daha yüksektir.

%50 indirimli teklif, kullanıcıların satın alma ihtimalini artırmaktadır.

6. ✅ Sonuç ve Aksiyon Planı
✔️ Olumlu Senaryo (p < 0.05 → H₀ reddedildi)
Karar: %50 indirimli abonelik ekranı daha etkili.

Aksiyon:

Grup B'deki tasarım tüm kullanıcılara sunulmalı

Uzun vadede kullanıcı başı gelir (LTV) izlenmeli

