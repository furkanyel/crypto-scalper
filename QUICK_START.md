# ⚡ Hızlı Başlangıç Rehberi / Quick Start Guide

## 🇹🇷 Türkçe Hızlı Kurulum

### 1️⃣ Dosyaları İndirin
- `scalping_indicator.pine` - Sinyaller ve fiyat seviyeleri için
- `scalping_strategy.pine` - Backtest yapmak için

### 2️⃣ Sinyaller İçin (Önerilen Başlangıç)

1. **TradingView'e Gidin**: https://www.tradingview.com/
2. **5 dakika BTC/USDT grafiği açın**
3. **Pine Editor'ü açın** (altta)
4. **`scalping_indicator.pine` kodunu kopyalayıp yapıştırın**
5. **"Add to Chart" tıklayın**

✅ Artık grafikte sinyalleri görebilirsiniz!

### 3️⃣ Sinyal Geldiğinde Ne Yapmalı?

#### 🟢 LONG Sinyali Gördüğünüzde:
```
Grafikte yeşil ok ve etiket göreceksiniz:

📊 LONG
💰 Giriş: 50,000 ← Bu fiyattan ALIŞ yapın
🛑 SL: 49,000 ← Stop loss buraya
🎯 TP1: 51,000 (RR: 1:1) ← İlk hedef
🎯 TP2: 52,000 (RR: 1:2) ← İkinci hedef  
🎯 TP3: 53,000 (RR: 1:3) ← Son hedef
```

**Ne Yapmalısınız:**
1. Giriş fiyatından alış emri verin
2. Stop loss'u 49,000'e koyun
3. TP1'de %50 pozisyonu kapatın
4. TP2'de %30 pozisyonu kapatın
5. TP3'te %20 pozisyonu kapatın

#### 🔴 SHORT Sinyali Gördüğünüzde:
```
Grafikte kırmızı ok ve etiket göreceksiniz:

📊 SHORT
💰 Giriş: 50,000 ← Bu fiyattan SATIŞ yapın
🛑 SL: 51,000 ← Stop loss buraya
🎯 TP1: 49,000 (RR: 1:1) ← İlk hedef
🎯 TP2: 48,000 (RR: 1:2) ← İkinci hedef
🎯 TP3: 47,000 (RR: 1:3) ← Son hedef
```

### 4️⃣ Backtest Nasıl Yapılır?

1. **`scalping_strategy.pine` kodunu Pine Editor'e yapıştırın**
2. **"Add to Chart" tıklayın**
3. **Alt tarafta "Strategy Tester" sekmesine bakın**
4. **Sonuçları görün:**
   - Kazanma oranı
   - Toplam kar/zarar
   - Kazanan/Kaybeden işlemler

**İyi Sonuç:**
- ✅ Kazanma oranı > %50
- ✅ Kar faktörü > 1.5
- ✅ Max düşüş < %20

### 5️⃣ Alert (Uyarı) Kurulumu

1. Grafikte **sağ tıklayın**
2. **"Add Alert"** seçin
3. **Condition**: "5M Crypto Scalping Indicator" seçin
4. **Alert türü**: "Any Signal Alert" seçin
5. **Bildirim**: Mobil, e-posta aktifleştirin
6. **"Create" tıklayın**

Artık sinyal geldiğinde telefonunuza bildirim gelecek! 📱

### 6️⃣ Risk Yönetimi (ÇOK ÖNEMLİ!)

**Asla bu kuralları çiğnemeyin:**
- ❌ Stop loss kullanmadan işlem YAPMAIN
- ❌ Hesabınızın %2'sinden fazla risk ALMAYIN
- ❌ Tüm paranızı tek işleme YATIRMAYIN
- ❌ Sinyal yokken zorla işlem AÇMAYIN

**Mutlaka yapın:**
- ✅ Her işlemde max %1-2 risk alın
- ✅ Stop loss kullanın
- ✅ Küçük pozisyonlarla başlayın
- ✅ İlk hafta sadece gözlemleyin

### 7️⃣ Önerilen Ayarlar

**Başlangıç için varsayılan ayarlar iyidir:**
- Stop Loss: %2
- TP1: %2, TP2: %4, TP3: %6

**Çok fazla sinyal istiyorsanız:**
- RSI Oversold: 35'e çıkarın
- RSI Overbought: 65'e indirin

**Az ama güvenilir sinyal istiyorsanız:**
- RSI Oversold: 25'e indirin
- RSI Overbought: 75'e çıkarın
- BB Std Dev: 2.5'e çıkarın

---

## 🇬🇧 English Quick Start

### 1️⃣ Download Files
- `scalping_indicator.pine` - For signals and price levels
- `scalping_strategy.pine` - For backtesting

### 2️⃣ For Signals (Recommended Start)

1. **Go to TradingView**: https://www.tradingview.com/
2. **Open 5-minute BTC/USDT chart**
3. **Open Pine Editor** (bottom)
4. **Copy and paste `scalping_indicator.pine` code**
5. **Click "Add to Chart"**

✅ You can now see signals on the chart!

### 3️⃣ What to Do When Signal Appears?

#### 🟢 LONG Signal:
```
You'll see green arrow with label:

📊 LONG
💰 Entry: 50,000 ← BUY at this price
🛑 SL: 49,000 ← Place stop loss here
🎯 TP1: 51,000 (RR: 1:1) ← First target
🎯 TP2: 52,000 (RR: 1:2) ← Second target  
🎯 TP3: 53,000 (RR: 1:3) ← Final target
```

**Action Plan:**
1. Place buy order at entry price
2. Set stop loss at 49,000
3. Close 50% at TP1
4. Close 30% at TP2
5. Close 20% at TP3

#### 🔴 SHORT Signal:
```
You'll see red arrow with label:

📊 SHORT
💰 Entry: 50,000 ← SELL at this price
🛑 SL: 51,000 ← Place stop loss here
🎯 TP1: 49,000 (RR: 1:1) ← First target
🎯 TP2: 48,000 (RR: 1:2) ← Second target
🎯 TP3: 47,000 (RR: 1:3) ← Final target
```

### 4️⃣ How to Backtest?

1. **Paste `scalping_strategy.pine` code in Pine Editor**
2. **Click "Add to Chart"**
3. **Look at "Strategy Tester" tab at bottom**
4. **View results:**
   - Win rate
   - Total profit/loss
   - Winning/Losing trades

**Good Results:**
- ✅ Win rate > 50%
- ✅ Profit factor > 1.5
- ✅ Max drawdown < 20%

### 5️⃣ Alert Setup

1. **Right-click** on chart
2. Select **"Add Alert"**
3. **Condition**: Choose "5M Crypto Scalping Indicator"
4. **Alert type**: Select "Any Signal Alert"
5. **Notifications**: Enable mobile, email
6. Click **"Create"**

You'll now receive notifications when signals appear! 📱

### 6️⃣ Risk Management (CRITICAL!)

**Never break these rules:**
- ❌ DON'T trade without stop loss
- ❌ DON'T risk more than 2% per trade
- ❌ DON'T put all capital in one trade
- ❌ DON'T force trades when no signal

**Always do:**
- ✅ Risk max 1-2% per trade
- ✅ Use stop loss
- ✅ Start with small positions
- ✅ Observe only first week

### 7️⃣ Recommended Settings

**Default settings are good for beginners:**
- Stop Loss: 2%
- TP1: 2%, TP2: 4%, TP3: 6%

**For more signals:**
- RSI Oversold: Increase to 35
- RSI Overbought: Decrease to 65

**For fewer but reliable signals:**
- RSI Oversold: Decrease to 25
- RSI Overbought: Increase to 75
- BB Std Dev: Increase to 2.5

---

## 📚 Full Documentation

- **[README.md](README.md)** - Complete English documentation
- **[README_TR.md](README_TR.md)** - Türkçe detaylı dökümantasyon

## ⚠️ Important Warnings

1. **This is NOT a guarantee** - No indicator is 100% accurate
2. **Always use stop loss** - Risk management is mandatory
3. **Backtest first** - Test before using real money
4. **Start small** - Use minimal position sizes initially
5. **Stay disciplined** - Follow your trading plan

---

**💡 Pro Tip**: Spend first week just watching signals without trading. Then paper trade for 2 weeks. Only then start with small real positions.

**📊 Success = Discipline + Risk Management + Patience**
