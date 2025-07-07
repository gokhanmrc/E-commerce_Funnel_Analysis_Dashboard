# 📊 A/B Testi Raporu: Abonelik Ekranı Dönüşüm Oranı Karşılaştırması

---

## 🎯 Testin Tanımı

### 🔍 Neyi Test Ediyoruz?
Bu A/B testinde, mobil uygulama üzerindeki abonelik teklif ekranının kullanıcı dönüşüm oranları üzerindeki etkisini test ediyoruz.

- **Grup A**: Kullanıcılara premium özelliklere erişmek için **$4.99’lık** standart abonelik ekranı gösteriliyor.
- **Grup B**: Aynı abonelik **%50 indirimli olarak ($2.49)** sunuluyor.

### ⚙️ Kullanılan A/B Testi Tasarımı
- **Tasarım tipi**: Klasik split A/B testi
- **Rastgele atama**: Kullanıcılar rastgele şekilde A ve B gruplarına atanmıştır.
- **Ölçülen metrik**: Dönüşüm oranı (abone olan kullanıcı oranı)

## 🧠 Problem ve Amaç

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
from scipy import stats

alpha = 0.05

observed = pd.crosstab(df["test_group"].values, df["conversion"].values)
statistic, pvalue, dof, expected_values = stats.chi2_contingency(observed)

print(f"chi2-statistic: {round(statistic, 2)}, p-value: {round(pvalue,2)}")

if pvalue < alpha:
    print("The difference is statistically significant, Null Hypothesis is rejected.")
else:
    print("The difference is insignificant, Null Hypothesis cannot be rejected.")
```
Test Sonucu:
chi2-statistic: 56.14, p-value: 0.0

Yorum: p < 0.05 olduğu için H₀ reddedilir. İki grup arasında istatistiksel olarak anlamlı bir fark vardır.

5. 📊 Sonuçların Analizi
                             | Kullanıcı Sayısı	 | Dönüşüm Sayısı |	Dönüşüm Oranı
Standart ekran (Grup A)      |	10013	           |	611	          |   6.10%     
%50 indirimli ekran (Grup B) |	9985	           |	889           | 	8.90%    

Grup B’nin dönüşüm oranı, Grup A’ya göre belirgin şekilde daha yüksektir.

%50 indirimli teklif, kullanıcıların satın alma ihtimalini artırmaktadır.

 Sonuç ve Aksiyon Planı
✔️ Olumlu Senaryo (p < 0.05 → H₀ reddedildi)
Karar: %50 indirimli abonelik ekranı daha etkili.

Aksiyon:

Grup B'deki tasarım tüm kullanıcılara sunulmalı

