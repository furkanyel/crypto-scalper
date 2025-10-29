# 5-Minute Crypto Scalping Indicator for TradingView

A comprehensive Pine Script v5 indicator designed for cryptocurrency scalping on 5-minute timeframes. This indicator uses a multi-indicator confirmation system to generate high-probability buy and sell signals.

> **⚡ Want to start immediately? Check [QUICK_START.md](QUICK_START.md) for 5-minute setup guide!**
> 
> **🇹🇷 Türkçe dökümantasyon için [README_TR.md](README_TR.md) dosyasına bakın.**

## 🎯 NEW Features

### ✅ Entry & Exit Price Levels
- **Exact Entry Price**: Automatically calculated entry price for each signal
- **Stop Loss Levels**: Automatic SL calculation with risk management
- **3 Take Profit Targets**: TP1, TP2, TP3 for gradual profit taking
- **Risk/Reward Ratios**: Automatic RR calculation for each level
- **Visual Price Labels**: All price levels clearly visible on chart with detailed information

### ✅ Backtesting Capability
- **Separate Strategy File**: `scalping_strategy.pine` for full backtesting support
- **Performance Metrics**: Win rate, profit factor, and detailed statistics
- **Date Range Filter**: Backtest specific time periods
- **Commission & Slippage**: Included for realistic backtesting results
- **Performance Table**: Live statistics displayed on chart

## 📁 Files

1. **scalping_indicator.pine** - Main indicator (signals with price levels and recommendations)
2. **scalping_strategy.pine** - Backtest strategy (for performance analysis and testing)
3. **README_TR.md** - Turkish documentation

## 🎯 Core Features

- **Multi-Indicator Confirmation System**: Combines RSI, EMA crossovers, Bollinger Bands, and Volume analysis
- **No Repainting**: Uses confirmed close values to ensure signals don't repaint
- **Fully Customizable**: All parameters can be adjusted via input settings
- **Visual Signals**: Clear buy/sell arrows displayed on chart with price recommendations
- **Alert System**: Built-in alert conditions with entry/exit prices
- **Information Dashboard**: Real-time indicator values displayed in a clean table
- **Flexible Display**: Toggle indicators on/off and customize colors
- **Risk Management**: Built-in stop loss and take profit calculations

## 📊 Strategy Components

### 1. RSI (Relative Strength Index)
- **Default Period**: 14
- **Purpose**: Identifies momentum and overbought/oversold conditions
- **Overbought Level**: 70
- **Oversold Level**: 30

### 2. EMA Crossover (Exponential Moving Averages)
- **Fast EMA**: 9 periods (blue)
- **Slow EMA**: 21 periods (orange)
- **Purpose**: Determines trend direction
- **Bullish**: Fast EMA crosses above Slow EMA
- **Bearish**: Fast EMA crosses below Slow EMA

### 3. Bollinger Bands
- **Period**: 20
- **Standard Deviation**: 2.0
- **Purpose**: Measures volatility and identifies overbought/oversold conditions
- **Upper Band**: Resistance level (red)
- **Lower Band**: Support level (green)

### 4. Volume Analysis
- **Volume MA Period**: 20
- **Purpose**: Confirms signal strength
- **Requirement**: Volume must be above its moving average for valid signals

## 🚀 Installation Instructions

### Option 1: Indicator (For Signals & Price Recommendations)

**Step 1: Copy the Code**
1. Open the `scalping_indicator.pine` file
2. Copy the entire content (Ctrl+A, Ctrl+C)

**Step 2: Add to TradingView**
1. Go to [TradingView](https://www.tradingview.com/)
2. Open any chart (recommended: BTC/USDT 5-minute chart)
3. Click on "Pine Editor" at the bottom of the screen
4. Paste the code into the editor
5. Click "Add to Chart" at the top of the Pine Editor

**Step 3: Configure Settings**
1. Click the gear icon ⚙️ next to the indicator name on the chart
2. Adjust parameters as needed:
   - **Risk Management**: Set Stop Loss % and Take Profit levels
   - **Display Settings**: Toggle price labels on/off
   - Customize colors and other parameters
3. Click "OK" to apply changes

### Option 2: Strategy (For Backtesting)

**Step 1: Copy the Strategy Code**
1. Open the `scalping_strategy.pine` file
2. Copy the entire content

**Step 2: Add to TradingView**
1. In TradingView Pine Editor, create a new script
2. Paste the strategy code
3. Click "Add to Chart"

**Step 3: View Backtest Results**
1. Look at the "Strategy Tester" tab at the bottom of the screen
2. View detailed performance metrics:
   - **Overview**: Total profit/loss, win rate
   - **Performance Summary**: Detailed statistics
   - **List of Trades**: All executed trades
3. Adjust date range in settings if needed

**Step 4: Optimize Parameters**
1. Click settings ⚙️ on the strategy
2. Adjust parameters and see how results change
3. Find optimal settings for your trading style

### Step 5: Set Up Alerts (Indicator Only)
1. Right-click on the chart
2. Select "Add Alert"
3. Choose the indicator from the "Condition" dropdown
4. Select your preferred alert type:
   - **"Buy Signal Alert"** - Only long signals with entry/exit prices
   - **"Sell Signal Alert"** - Only short signals with entry/exit prices
   - **"Any Signal Alert"** - Both buy and sell signals
5. Configure notification preferences (popup, email, mobile, webhook, etc.)
6. Click "Create"

**Alert Message Example:**
```
🟢 LONG SIGNAL
📈 Entry Price: 50000
🛑 Stop Loss: 49000
🎯 TP1: 51000
🎯 TP2: 52000
🎯 TP3: 53000
```

## 📈 Signal Conditions & Price Levels

### Buy Signal (Green Arrow Below Candle) ▲
All of the following conditions must be met simultaneously:
1. ✅ RSI crosses above 30 (oversold recovery)
2. ✅ 9 EMA crosses above 21 EMA (bullish trend confirmation)
3. ✅ Price touches or breaks below lower Bollinger Band (potential reversal)
4. ✅ Volume is above the volume moving average (strong momentum)

**When Signal Appears:**
- Green arrow with "BUY" text appears below the candle
- A detailed label shows:
  - 💰 **Entry Price**: Current close price (where to enter)
  - 🛑 **Stop Loss**: Calculated SL level (default 2% below entry)
  - 🎯 **TP1**: First target (default 2% above entry) with RR ratio
  - 🎯 **TP2**: Second target (default 4% above entry) with RR ratio
  - 🎯 **TP3**: Third target (default 6% above entry) with RR ratio
- Horizontal lines show all price levels on the chart

**Example:**
```
📊 LONG
💰 Entry: $50,000
🛑 SL: $49,000 (Risk: $1,000)
🎯 TP1: $51,000 (RR: 1:1) - Take 50% profit
🎯 TP2: $52,000 (RR: 1:2) - Take 30% profit
🎯 TP3: $53,000 (RR: 1:3) - Take 20% profit
```

### Sell Signal (Red Arrow Above Candle) ▼
All of the following conditions must be met simultaneously:
1. ✅ RSI crosses below 70 (overbought reversal)
2. ✅ 9 EMA crosses below 21 EMA (bearish trend confirmation)
3. ✅ Price touches or breaks above upper Bollinger Band (potential reversal)
4. ✅ Volume is above the volume moving average (strong momentum)

**When Signal Appears:**
- Red arrow with "SELL" text appears above the candle
- A detailed label shows:
  - 💰 **Entry Price**: Current close price (where to enter short)
  - 🛑 **Stop Loss**: Calculated SL level (default 2% above entry)
  - 🎯 **TP1**: First target (default 2% below entry) with RR ratio
  - 🎯 **TP2**: Second target (default 4% below entry) with RR ratio
  - 🎯 **TP3**: Third target (default 6% below entry) with RR ratio
- Horizontal lines show all price levels on the chart

**Example:**
```
📊 SHORT
💰 Entry: $50,000
🛑 SL: $51,000 (Risk: $1,000)
🎯 TP1: $49,000 (RR: 1:1) - Take 50% profit
🎯 TP2: $48,000 (RR: 1:2) - Take 30% profit
🎯 TP3: $47,000 (RR: 1:3) - Take 20% profit
```

## ⚙️ Parameter Settings Guide

### RSI Settings
- **RSI Period**: Default 14. Lower values (7-10) make it more sensitive; higher values (14-21) make it smoother.
- **RSI Overbought Level**: Default 70. Common range: 65-80
- **RSI Oversold Level**: Default 30. Common range: 20-35

### EMA Settings
- **Fast EMA Period**: Default 9. Quicker to respond to price changes.
- **Slow EMA Period**: Default 21. Provides longer-term trend confirmation.

### Bollinger Bands Settings
- **BB Period**: Default 20. Standard setting for most timeframes.
- **BB Std Dev**: Default 2.0. Increase for wider bands (fewer signals), decrease for tighter bands (more signals).

### Volume Settings
- **Volume MA Period**: Default 20. Matches the BB period for consistency.

### Risk Management Settings (NEW!)
- **Show Stop Loss & Take Profit Levels**: Toggle price level lines on/off
- **Stop Loss %**: Default 2.0%. Adjust based on volatility (1-5% range)
  - Lower % = Tighter stop, more frequent stops
  - Higher % = Wider stop, fewer stops but bigger risk
- **Take Profit 1 %**: Default 2.0%. First profit target (recommended: same as SL for 1:1 RR)
- **Take Profit 2 %**: Default 4.0%. Second profit target (recommended: 2x SL for 1:2 RR)
- **Take Profit 3 %**: Default 6.0%. Third profit target (recommended: 3x SL for 1:3 RR)
- **Show Price Level Labels**: Toggle detailed entry/exit labels on/off

**Recommended Settings for Different Assets:**
- **BTC/ETH**: SL 1.5-2%, TP 2-4-6%
- **High Volatility Altcoins**: SL 3-5%, TP 5-10-15%
- **Stable Assets**: SL 1%, TP 1-2-3%

### Display Settings
- **Show EMAs**: Toggle EMA display on/off
- **Show Bollinger Bands**: Toggle BB display on/off
- **Show Background Color**: Enable/disable background highlighting on signals
- **Show Trade Info Panel**: Toggle the information table display

### Color Settings
Customize all colors to match your chart theme and preferences.

## 💡 Best Practices for 5-Minute Crypto Scalping

### 1. Timeframe Optimization
- **Primary Timeframe**: 5-minute charts (optimized for this indicator)
- **Confirmation Timeframe**: Check 15-minute chart for trend alignment
- **Higher Timeframe**: Review 1-hour chart for overall market direction

### 2. Market Conditions
- **Best Performance**: High volatility markets with clear trends
- **Avoid**: Low volume periods, major news releases without proper risk management
- **Trading Hours**: Most active during overlapping market sessions

### 3. Entry Strategy
- **Wait for Confirmation**: Ensure the candle closes with the signal
- **Volume Confirmation**: Higher volume signals are generally more reliable
- **Trend Alignment**: Stronger signals when aligned with higher timeframe trends

### 4. Exit Strategy
- **Take Profit**: Use support/resistance levels, or 1:2 risk/reward ratio minimum
- **Stop Loss**: Place below recent swing low (buy) or above recent swing high (sell)
- **Trailing Stop**: Consider using a trailing stop to lock in profits
- **Opposite Signal**: Exit when opposite signal appears

### 5. Risk Management (CRITICAL)
- **Position Size**: Never risk more than 1-2% of your capital per trade
- **Stop Loss**: ALWAYS use stop losses - no exceptions
- **Risk/Reward**: Aim for minimum 1:2 ratio (risk $1 to make $2)
- **Daily Loss Limit**: Set a maximum daily loss limit (e.g., 5% of capital)
- **Avoid Overtrading**: Quality over quantity - don't force trades

### 6. Market Selection
- **High Liquidity Pairs**: BTC/USDT, ETH/USDT, BNB/USDT, etc.
- **Avoid Low Volume**: Pairs with low volume can have false signals
- **Volatility**: This indicator works best with moderate to high volatility

### 7. False Signal Reduction
- **Multiple Timeframe Analysis**: Confirm signals on higher timeframes
- **Market Structure**: Trade in the direction of the overall trend
- **Support/Resistance**: Signals near key levels are more reliable
- **Volume Profile**: Higher volume at signal points increases reliability

## ⚠️ Risk Management Recommendations

### Position Sizing
```
Position Size = (Account Size × Risk Percentage) / Stop Loss Distance

Example:
- Account Size: $10,000
- Risk Per Trade: 1% = $100
- Entry: $50,000
- Stop Loss: $49,500
- Stop Loss Distance: $500

Position Size = $100 / $500 = 0.002 BTC (or equivalent)
```

### Stop Loss Placement
- **Buy Signals**: Place stop loss 1-2 ATR below entry or below recent swing low
- **Sell Signals**: Place stop loss 1-2 ATR above entry or above recent swing high
- **Never Move Stop Loss** in the wrong direction (against your position)

### Take Profit Targets
1. **Conservative**: 1:1 Risk/Reward (take profit at same distance as stop loss)
2. **Moderate**: 1:2 Risk/Reward (recommended minimum)
3. **Aggressive**: 1:3 Risk/Reward (hold for larger moves)

### Portfolio Risk
- **Maximum Open Positions**: 3-5 positions simultaneously
- **Correlation**: Avoid multiple correlated pairs (e.g., don't trade BTC/USDT and BTC/EUR simultaneously)
- **Capital Allocation**: Don't use more than 10-15% of capital on scalping

## 📝 Backtesting Guide

### How to Backtest (Using Strategy File)

**Step 1: Load the Strategy**
1. Copy `scalping_strategy.pine` code
2. Add to TradingView chart (5-minute timeframe recommended)
3. The strategy will automatically execute trades based on signals

**Step 2: Configure Backtest Settings**
1. Click settings ⚙️ on the strategy
2. Under "Backtest Settings":
   - Enable "Use Date Filter"
   - Set **Start Date** and **End Date** for your test period
3. Adjust Risk Management settings:
   - Stop Loss % (test different values: 1%, 2%, 3%)
   - Take Profit levels
   - Enable/disable Trailing Stop

**Step 3: View Results**
Go to "Strategy Tester" tab at bottom of TradingView:

**Overview Tab:**
- **Net Profit**: Total profit/loss in $
- **Total Closed Trades**: Number of completed trades
- **Percent Profitable**: Win rate %
- **Profit Factor**: Gross profit ÷ Gross loss
- **Max Drawdown**: Largest capital decline

**Performance Summary Tab:**
- Detailed statistics
- Average trade duration
- Average win vs average loss
- Largest winning/losing trade

**List of Trades Tab:**
- Every single trade executed
- Entry/exit prices
- Profit/loss per trade
- Trade duration

### On-Chart Performance Table

The strategy displays a live performance table showing:
- **Toplam İşlem** (Total Trades)
- **Kazanan İşlem** (Winning Trades)
- **Kaybeden İşlem** (Losing Trades)
- **Kazanma Oranı** (Win Rate %)
- **Kar Faktörü** (Profit Factor)
- **Ort. Kazanç** (Average Win)
- **Ort. Kayıp** (Average Loss)

### Key Metrics to Track

✅ **Good Backtest Results:**
- Win Rate: **> 50%**
- Profit Factor: **> 1.5**
- Max Drawdown: **< 20%**
- Average Win > Average Loss
- Consistent profit across different time periods

❌ **Poor Backtest Results:**
- Win Rate: < 40%
- Profit Factor: < 1.0
- Max Drawdown: > 30%
- Average Win < Average Loss
- Inconsistent or declining equity curve

### Optimization Tips

**Test Different Scenarios:**
1. **Different Stop Loss %**: Try 1%, 2%, 3%, 5%
2. **Different Take Profit Levels**: Adjust TP1, TP2, TP3
3. **Different Time Periods**: Bull market vs bear market
4. **Different Assets**: BTC, ETH, altcoins
5. **Different Timeframes**: Test on 3m, 5m, 15m

**Parameter Optimization:**
- Use TradingView's built-in optimization feature
- Test RSI periods: 10, 12, 14, 16
- Test EMA periods: 5/13, 9/21, 12/26
- Find the best combination for your asset

### Recommended Testing Approach
1. **Historical Data**: Test on at least 6-12 months of data
2. **Different Market Conditions**: Include bull, bear, and sideways markets
3. **Multiple Assets**: Test on various cryptocurrency pairs
4. **Walk-Forward Testing**: Test on past data, then validate on recent unseen data
5. **Paper Trading**: After good backtest, practice with paper trading for 2-4 weeks
6. **Small Live Positions**: Start with minimal position sizes

### Known Limitations
- **Choppy Markets**: May generate false signals in ranging, low-volatility conditions
- **News Events**: Major news can cause whipsaws - avoid trading during high-impact news
- **Gaps**: Crypto markets are 24/7, but exchange outages can cause gaps
- **Slippage**: Fast-moving markets may result in slippage (strategy includes 2 ticks slippage)
- **Commission**: Strategy includes 0.1% commission per trade (adjust if needed)
- **Over-optimization**: Don't over-optimize to past data - it may not work in future

## 🔧 Troubleshooting

### Signal Not Appearing
- Ensure all four conditions are met simultaneously
- Check that volume is above average
- Verify the indicator is applied to the correct timeframe (5-minute)

### Too Many Signals
- Increase RSI overbought/oversold levels (e.g., 75/25)
- Increase Bollinger Bands standard deviation (e.g., 2.5)
- Use longer EMA periods (e.g., 12/26)

### Too Few Signals
- Decrease RSI overbought/oversold levels (e.g., 65/35)
- Decrease Bollinger Bands standard deviation (e.g., 1.5)
- Use shorter EMA periods (e.g., 5/13)

### Alerts Not Working
- Ensure you've created the alert (see Installation Step 4)
- Check TradingView notification settings
- Verify you have an active TradingView subscription (alerts may be limited on free plans)

## 📚 Additional Resources

### Learning Materials
- [TradingView Pine Script Documentation](https://www.tradingview.com/pine-script-docs/)
- [Understanding RSI](https://www.investopedia.com/terms/r/rsi.asp)
- [EMA Strategies](https://www.investopedia.com/terms/e/ema.asp)
- [Bollinger Bands Explained](https://www.investopedia.com/terms/b/bollingerbands.asp)

### Risk Warnings
- **Past Performance**: Does not guarantee future results
- **High Risk**: Scalping is high-risk and not suitable for all traders
- **Cryptocurrency Volatility**: Crypto markets are extremely volatile
- **Never Invest More**: Than you can afford to lose
- **Not Financial Advice**: This indicator is for educational purposes only

## 📄 Version History

### Version 1.0.0 (Current)
- Initial release
- Multi-indicator confirmation system
- RSI, EMA, Bollinger Bands, and Volume analysis
- Buy/Sell signal arrows
- Alert conditions
- Information dashboard
- Full customization options
- No repainting signals

## 🤝 Support & Contributions

For issues, questions, or suggestions, please open an issue in the repository.

## ⚖️ License

This indicator is provided as-is for educational and informational purposes only. Use at your own risk.

## ⚠️ Disclaimer

**IMPORTANT**: This indicator is a tool to assist with trading decisions, not a guarantee of profits. Always:
- Do your own research (DYOR)
- Practice proper risk management
- Start with small positions
- Never trade with money you cannot afford to lose
- Consider seeking advice from a qualified financial advisor

**Cryptocurrency trading carries substantial risk of loss and is not suitable for every investor. The valuation of cryptocurrencies may fluctuate, and you may lose all or more than your original investment.**

---

*Happy Trading! Remember: Discipline and risk management are more important than any indicator.*
