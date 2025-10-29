# 5 Dakikalık Kripto Scalping İndikatörü - TradingView

TradingView için Pine Script v5 ile geliştirilmiş profesyonel kripto scalping indikatörü. Multi-indikatör onay sistemi ile yüksek olasılıklı alım-satım sinyalleri üretir.

## 🎯 Yeni Özellikler

### ✅ Giriş ve Çıkış Seviyeleri
- **Tam Giriş Fiyatı**: Her sinyal için otomatik hesaplanan giriş fiyatı
- **Stop Loss Seviyeleri**: Risk yönetimi için otomatik SL hesaplama
- **3 Farklı Take Profit**: TP1, TP2, TP3 seviyeleri ile kademeli kar alma
- **Risk/Reward Oranı**: Her seviye için otomatik RR hesaplama
- **Görsel Etiketler**: Grafikte tüm fiyat seviyeleri net görünür

### ✅ Backtest Özelliği
- **Ayrı Strategy Dosyası**: `scalping_strategy.pine` ile tam backtest desteği
- **Performans Tablosu**: Kazanma oranı, kar faktörü ve detaylı istatistikler
- **Tarih Filtresi**: Belirli dönemler için backtest yapabilme
- **Komisyon ve Slippage**: Gerçekçi backtest için dahil edilmiş

## 📁 Dosyalar

1. **scalping_indicator.pine** - Ana indikatör (sinyaller ve seviyeler)
2. **scalping_strategy.pine** - Backtest stratejisi (performans analizi için)

## 🚀 Kurulum

### 1. İndikatör Kurulumu (Sinyaller için)

1. `scalping_indicator.pine` dosyasını açın ve tüm kodu kopyalayın
2. [TradingView](https://www.tradingview.com/) sitesine gidin
3. Herhangi bir grafik açın (BTC/USDT, ETH/USDT önerilir)
4. Alt tarafta "Pine Editor"ü tıklayın
5. Kodu yapıştırın
6. "Add to Chart" butonuna tıklayın

### 2. Backtest Kurulumu (Performans testi için)

1. `scalping_strategy.pine` dosyasını açın ve tüm kodu kopyalayın
2. TradingView'de yeni bir Pine Editor penceresi açın
3. Kodu yapıştırın
4. "Add to Chart" butonuna tıklayın
5. Alt tarafta "Strategy Tester" sekmesinde sonuçları görün

## 📊 Nasıl Kullanılır?

### Sinyalleri Anlama

#### 🟢 LONG (ALIŞ) Sinyali
Aşağıdaki **tüm koşullar** aynı anda gerçekleştiğinde:
1. RSI 30'un üzerine geçiş yaptı (aşırı satımdan dönüş)
2. 9 EMA, 21 EMA'nın üzerine geçti (yükseliş trendi)
3. Fiyat alt Bollinger Bandı'na değdi (düşük fiyat bölgesi)
4. Hacim ortalamanın üzerinde (güçlü momentum)

**Ne yapmalısınız:**
- Grafikte yeşil üçgen ok ve "BUY" etiketi görünür
- Etiket üzerinde tüm fiyat seviyeleri yazılı:
  - 💰 Entry (Giriş): Bu fiyattan alış yapın
  - 🛑 SL (Stop Loss): Bu fiyatın altına stop koyun
  - 🎯 TP1, TP2, TP3: Kar alma seviyeleri (RR oranlarıyla)

#### 🔴 SHORT (SATIŞ) Sinyali
Aşağıdaki **tüm koşullar** aynı anda gerçekleştiğinde:
1. RSI 70'in altına geçiş yaptı (aşırı alımdan dönüş)
2. 9 EMA, 21 EMA'nın altına geçti (düşüş trendi)
3. Fiyat üst Bollinger Bandı'na değdi (yüksek fiyat bölgesi)
4. Hacim ortalamanın üzerinde (güçlü momentum)

**Ne yapmalısınız:**
- Grafikte kırmızı üçgen ok ve "SELL" etiketi görünür
- Short pozisyon açın veya long pozisyonunuzu kapatın
- Etiket üzerindeki seviyeleri kullanın

### Risk Yönetimi Ayarları

İndikatör ayarlarından (⚙️) Risk Management bölümünde:

- **Stop Loss %**: Varsayılan %2 (ihtiyacınıza göre %1-5 arası ayarlayabilirsiniz)
- **Take Profit 1 %**: Varsayılan %2 (ilk kar alma)
- **Take Profit 2 %**: Varsayılan %4 (ikinci kar alma)
- **Take Profit 3 %**: Varsayılan %6 (son kar alma)

**Örnek Senaryo:**
- Giriş: $50,000
- SL (%2): $49,000
- TP1 (%2): $51,000 - RR: 1:1
- TP2 (%4): $52,000 - RR: 1:2
- TP3 (%6): $53,000 - RR: 1:3

### Backtest Nasıl Yapılır?

1. **Strategy dosyasını ekleyin** (`scalping_strategy.pine`)
2. **Zaman dilimini seçin**: 5 dakika (5m) grafiğe geçin
3. **Tarih aralığını ayarlayın**: 
   - Ayarlar → Backtest Settings
   - Start Date ve End Date belirleyin
4. **Alt tarafta Strategy Tester** sekmesine bakın:
   - **Overview**: Toplam kar/zarar, kazanma oranı
   - **Performance Summary**: Detaylı istatistikler
   - **List of Trades**: Tüm işlemler listesi

**Nelere Dikkat Etmeli:**
- ✅ Win Rate (Kazanma Oranı) > %50 olmalı
- ✅ Profit Factor (Kar Faktörü) > 1.5 olmalı
- ✅ Max Drawdown (Maks. Düşüş) < %20 olmalı
- ✅ Average Win > Average Loss olmalı

## 🎯 İşlem Önerileri

### Pozisyon Yönetimi

**Kademeli Giriş (Önerilen):**
```
%50 pozisyon TP1'de kapat (risksiz işlem)
%30 pozisyon TP2'de kapat (garantiye al)
%20 pozisyon TP3'de kapat (maksimum kar)
```

**Stop Loss Takibi:**
- TP1'e ulaştıktan sonra SL'yi başabaş noktasına çekin
- TP2'ye ulaştıktan sonra SL'yi TP1 seviyesine çekin

### Sinyal Filtreleme

**Daha Güvenilir Sinyaller için:**
1. **Yüksek zaman dilimi kontrolü**: 15m ve 1h grafikte trend aynı yönde mi?
2. **Destek/Direnç seviyeleri**: Sinyal önemli bir seviyede mi?
3. **Hacim onayı**: Hacim çok yüksekse sinyal daha güçlü
4. **RSI ekstrem seviyeleri**: RSI 20'nin altında veya 80'in üstünde ise daha güçlü

### Önemli Uyarılar

❌ **YAPMAYIN:**
- Tek sinyale göre tüm paranızı yatırmayın
- Stop loss kullanmadan işlem açmayın
- Sinyal gelmezken zorla işlem açmayın
- Haber zamanlarında işlem açmayın

✅ **YAPIN:**
- Her işlemde max %1-2 risk alın
- Mutlaka stop loss kullanın
- Günlük loss limiti belirleyin (%5 önerilir)
- Disiplinli olun, plan dışı hareket etmeyin

## ⚙️ Parametre Optimizasyonu

### Daha Fazla Sinyal İsterseniz:
- RSI Oversold: 35'e çıkarın
- RSI Overbought: 65'e indirin
- BB Std Dev: 1.5'e indirin

### Daha Az Ama Güvenilir Sinyal İsterseniz:
- RSI Oversold: 25'e indirin
- RSI Overbought: 75'e çıkarın
- BB Std Dev: 2.5'e çıkarın
- Volume MA Period: 30'a çıkarın

### Farklı Kripto Çiftler İçin:
- **BTC/ETH (volatilite düşük)**: Daha hassas ayarlar
- **Altcoinler (volatilite yüksek)**: Daha geniş BB, yüksek SL

## 📈 Performans Takibi

Strategy dosyasında sağ alt köşede **Performans Tablosu** gösterilir:

- **Toplam İşlem**: Kaç işlem yapıldı
- **Kazanan İşlem**: Kaç işlem karlı
- **Kaybeden İşlem**: Kaç işlem zararlı
- **Kazanma Oranı**: Win rate yüzdesi
- **Kar Faktörü**: Profit Factor (>1.5 iyi)
- **Ort. Kazanç**: Kazanan işlemler ortalaması
- **Ort. Kayıp**: Kaybeden işlemler ortalaması

## 💰 Risk Hesaplama Örneği

**10,000 USDT hesap, %2 risk:**

```
Risk tutarı = 10,000 × 0.02 = 200 USDT
Giriş fiyatı = 50,000 USDT (BTC)
Stop Loss = 49,000 USDT (2% aşağıda)
Risk mesafesi = 1,000 USDT

Pozisyon büyüklüğü = 200 / 1,000 = 0.2 BTC
veya
Pozisyon değeri = 0.2 × 50,000 = 10,000 USDT
```

## 🔔 Alert (Uyarı) Kurulumu

1. Grafikte sağ tıklayın
2. "Add Alert" seçin
3. Condition: "5M Crypto Scalping Indicator"
4. Alert türünü seçin:
   - "Buy Signal Alert" - Sadece long sinyalleri
   - "Sell Signal Alert" - Sadece short sinyalleri
   - "Any Signal Alert" - Tüm sinyaller
5. Bildirim yöntemini seçin (mobil, e-posta, vb.)
6. "Create" tıklayın

**Alert mesajı örneği:**
```
🟢 LONG SİNYALİ
📈 Giriş Fiyatı: 50000
🛑 Stop Loss: 49000
🎯 TP1: 51000
🎯 TP2: 52000
🎯 TP3: 53000
```

## 🎓 Strateji Mantığı

Bu indikatör **çoklu onay sistemi** kullanır:

1. **RSI**: Momentum ve aşırı alım/satım bölgeleri
2. **EMA Crossover**: Trend yönü belirleme
3. **Bollinger Bands**: Volatilite ve fiyat ekstremiteleri
4. **Volume**: Hareketin gücünü onaylama

**Neden 4 koşul birden?**
- Tek indikatör yanıltıcı olabilir
- 4 indikatör aynı anda onay verirse sinyal çok daha güvenilir
- False (yanlış) sinyal oranı azalır

## 📚 Önerilen Çiftler

### Yüksek Likidite (Önerilen):
- BTC/USDT
- ETH/USDT
- BNB/USDT
- SOL/USDT
- XRP/USDT

### Orta Volatilite:
- ADA/USDT
- AVAX/USDT
- MATIC/USDT

### Yüksek Volatilite (Dikkatli):
- Düşük hacimli altcoinler
- Yeni listelenmiş coinler

## ⚠️ Önemli Uyarılar

1. **Bu bir garanti değildir**: Hiçbir indikatör %100 başarı garantisi vermez
2. **Risk yönetimi şarttır**: Her zaman stop loss kullanın
3. **Backtest yapın**: Gerçek parayla işlem yapmadan önce test edin
4. **Demo hesap**: Önce kağıt hesapta pratik yapın
5. **Duygusal olmayın**: Plan dışı hareket etmeyin
6. **Küçük başlayın**: İlk başta küçük pozisyonlarla işlem yapın

## 🆘 Sorun Giderme

### "Sinyal çıkmıyor"
- 5 dakika grafikte misiniz?
- Tüm 4 koşul aynı anda oluşmalı (nadirdir)
- Parametreleri gevşetebilirsiniz

### "Çok fazla sinyal var"
- Parametreleri sıkılaştırın
- Yüksek zaman dilimi filtresi ekleyin

### "Backtest çalışmıyor"
- Strategy dosyasını kullanıyor musunuz?
- Tarih aralığı doğru mu?

### "Stop loss çok sık vuruyor"
- Stop loss %'sini artırın
- Daha güvenilir sinyallerde işlem yapın

## 📞 Destek

Sorunlarınız için GitHub'da issue açabilirsiniz.

## 📄 Lisans

Eğitim amaçlıdır. Kendi sorumluluğunuzda kullanın.

---

**📊 Başarılı Trading! Unutmayın: Disiplin ve risk yönetimi her indikatörden önemlidir.**

**💡 İpucu**: İlk hafta sadece alert kurarak sinyalleri gözlemleyin. Ardından demo hesapta test edin. Sonra küçük pozisyonlarla gerçek işleme başlayın.
