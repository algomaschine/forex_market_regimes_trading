FX Market Analysis Framework

https://img.shields.io/badge/FX-Analysis-blue
https://img.shields.io/badge/Multi--Factor-Strategy-green
https://img.shields.io/badge/Institutional-Grade-orange

A comprehensive multi-factor FX analysis system that integrates DXY, commodities, volatility indices, currency futures, and global equity indices to generate professional trading signals.
📋 Overview

This framework provides institutional-grade analysis of foreign exchange markets by combining multiple data sources and analytical techniques. The system processes DXY trends, oil prices, volatility indicators, currency futures, and global market sentiment to generate actionable trading signals with confidence scoring.
🚀 Key Features
🎯 Multi-Factor Analysis

    DXY Regime Detection: Identifies USD strength/weakness cycles

    Commodity Integration: Special handling for oil-sensitive pairs (USD/CAD) and gold volatility

    Volatility Analysis: Incorporates VIX, VVIX, SKEW, MOVE, and GVZ (Gold Volatility) indices

    Futures-Spot Divergence: Compares spot FX with futures market positioning

    Currency Strength Matrix: Calculates relative strength across 8 major currencies

    Global Equity Integration: Analyzes regional indices for risk sentiment

📊 Data Integration

    Local Data Support: Reads from local CSV files in standardized formats

    Flexible Formats: Handles both factors (indices) and FX pair data

    Technical Indicators: Implements moving averages, RSI, MACD, Bollinger Bands, ADX

    Automated Data Processing: Standardizes column names and date formats

🌍 Global Market Coverage

    Volatility Complex: VIX, VVIX, SKEW, MOVE, GVZ, OVX, VXD, VXN

    Regional Equity Indices: DJI, NDX, SPY, QQQ, HSI, BSESN, IBEX, SSEC

    Commodities: Oil index, gold, silver, platinum, palladium, soybeans

    Currency Analysis: DXY and major FX pairs

📁 Data Structure
Factors Folder Structure
text

factors/
├── 📈 Volatility Indices
│   ├── VIX.INDX_daily.csv        # S&P 500 Volatility (Fear Gauge)
│   ├── VVIX.INDX_daily.csv       # VIX of VIX (Volatility of Volatility)
│   ├── SKEW.INDX_daily.csv       # Tail Risk Index
│   ├── MOVE.INDX_daily.csv       # Treasury Bond Volatility
│   ├── GVZ.INDX_daily.csv        # Gold Volatility Index
│   ├── OVX.INDX_daily.csv        # Oil Volatility Index
│   ├── VXD.INDX_daily.csv        # DJIA Volatility
│   └── VXN.INDX_daily.csv        # NASDAQ Volatility
├── 🌍 Equity Indices
│   ├── DJI.INDX_daily.csv        # Dow Jones Industrial Average
│   ├── NDX.INDX_daily.csv        # NASDAQ 100
│   ├── SPY_daily.csv             # S&P 500 ETF
│   ├── QQQ_daily.csv             # NASDAQ 100 ETF
│   ├── HSI.INDX_daily.csv        # Hong Kong Hang Seng
│   ├── BSESN.INDX_daily.csv      # India S&P BSE Sensex
│   ├── IBEX.INDX_daily.csv       # Spain IBEX 35
│   └── SSEC.INDX_daily.csv       # Shanghai Composite
├── ⛽ Commodities
│   ├── Global_Oil_Index.csv      # S&P Global Oil Index
│   ├── XAUUSD_daily.csv          # Gold
│   ├── XAGUSD_daily.csv          # Silver
│   ├── XPTUSD_daily.csv          # Platinum
│   ├── XPDUSD_daily.csv          # Palladium
│   └── SOYB_daily.csv            # Soybeans
└── 💵 Currency Index
    └── DXY.INDX_daily.csv        # US Dollar Index

FX Folder Structure
text

fx/
├── 🌏 Major Pairs
│   ├── AUDUSD1440.csv
│   ├── EURUSD1440.csv
│   ├── GBPUSD1440.csv
│   ├── USDCAD1440.csv
│   ├── USDJPY1440.csv
│   └── USDCHF1440.csv
├── 🔄 Cross Pairs
│   ├── AUDCAD1440.csv
│   ├── AUDCHF1440.csv
│   ├── AUDJPY1440.csv
│   ├── AUDNZD1440.csv
│   ├── CADCHF1440.csv
│   ├── CADJPY1440.csv
│   ├── CHFJPY1440.csv
│   ├── EURAUD1440.csv
│   ├── EURCAD1440.csv
│   ├── EURCHF1440.csv
│   ├── EURGBP1440.csv
│   └── EURJPY1440.csv

⚙️ Installation & Dependencies
bash

pip install pandas numpy ta datetime pathlib

🧠 Core Analysis Logic
DXY Influence Framework
python

# Pseudo-code for DXY-based analysis
IF DXY_TREND == BULLISH:
    FOR pair in [EURUSD, GBPUSD, AUDUSD, NZDUSD]:
        SIGNAL = BEARISH (inverse correlation)
    FOR pair in [USDJPY, USDCHF]:
        SIGNAL = BULLISH (positive correlation)
ELSE IF DXY_TREND == BEARISH:
    # Reverse the signals

USD/CAD Oil Override Logic
python

# Special handling for oil-sensitive pairs
IF OIL_TREND == BULLISH:
    USD/CAD_SIGNAL = BEARISH (CAD strengthens with oil)
ELSE IF OIL_TREND == BEARISH and DXY_BULLISH:
    USD/CAD_SIGNAL = BULLISH

Volatility Regime Detection
python

# Risk sentiment analysis
IF VIX > 30 OR VVIX > 120 OR SKEW > 140 OR MOVE > 150:
    RISK_REGIME = "EXTREME_RISK_OFF"
    SAFE_HAVENS = [JPY, CHF, USD, Gold]
ELSE IF VIX < 15 AND VVIX < 90 AND GVZ < 20:
    RISK_REGIME = "RISK_ON" 
    RISK_ASSETS = [AUD, NZD, CAD, MXN]

💻 Usage Examples
Basic Analysis
python

from local_fx_analyzer import LocalFXAnalyzer

# Initialize analyzer
analyzer = LocalFXAnalyzer(factors_folder='factors', fx_folder='fx')

# Generate comprehensive report
report = analyzer.generate_comprehensive_report()

# Access specific components
signals = report['fx_signals']
strength_matrix = report['strength_matrix']
volatility_regime = report['volatility_analysis']['risk_regime']

Advanced Configuration
python

# Custom analysis with specific pairs
analyzer = LocalFXAnalyzer(factors_folder='factors', fx_folder='fx')

# Load data manually
analyzer.load_factors_data()
analyzer.load_fx_data()

# Run individual analyses
dxy_analysis = analyzer.analyze_dxy_regime()
volatility_analysis = analyzer.analyze_volatility_regime()
oil_analysis = analyzer.analyze_oil_impact()

# Generate custom signals
signals = analyzer.generate_fx_signals()

Volatility-Focused Analysis
python

# Specialized volatility analysis
vol_analysis = analyzer.analyze_volatility_regime()

print(f"VIX Level: {vol_analysis['current_values']['VIX']}")
print(f"VVIX Trend: {vol_analysis['metrics']['VVIX']['trend']}")
print(f"Gold Volatility (GVZ): {vol_analysis['current_values'].get('GVZ', 'N/A')}")
print(f"Risk Regime: {vol_analysis['risk_regime']}")

📊 Sample Output
text

COMPREHENSIVE FX ANALYSIS REPORT
======================================================================

📊 MARKET REGIME SUMMARY:
   DXY Regime: DXY_BULLISH (Strength: 68.2)
   Volatility Regime: NEUTRAL
   Oil Signal: BULLISH (Confidence: 72.5%)
   Global Risk: MODERATE

🎭 VOLATILITY METRICS:
   VIX: 16.8 (MODERATE_NEUTRAL) - Equity Fear
   VVIX: 88.3 (WEAK_BULLISH) - Volatility Stability
   SKEW: 135.2 (MODERATE_BEARISH) - Tail Risk
   MOVE: 98.5 (BOND_CALM) - Bond Volatility
   GVZ: 19.2 (LOW) - Gold Volatility

🌍 GLOBAL INDICES:
   SPY: STRONG_BULLISH (US Markets)
   HSI: WEAK_BEARISH (Asian Markets)
   IBEX: MODERATE_NEUTRAL (European Markets)

💪 CURRENCY STRENGTH MATRIX:
   USD: 🔥 78.4
   JPY: ✅ 65.1
   CHF: ⚖️ 54.3
   EUR: 🔻 42.7
   AUD: 🔻 38.9
   CAD: ✅ 61.2 (Oil Boost)

🎯 TRADING SIGNALS (Top 10):
   🟢 BUY USDJPY (Confidence: 82.1%)
      Reasoning: DXY bullish + Risk-off sentiment favors USD over JPY
   🔴 SELL EURUSD (Confidence: 76.8%)
      Reasoning: DXY bullish typically weakens EURUSD
   🟢 BUY USDCAD (Confidence: 68.3%)
      Reasoning: Strong USD overriding moderate oil bullishness

⚠️  RISK WARNINGS:
   - SKEW above 130 indicates elevated tail risk
   - Consider reduced position sizes

📈 Key Trading Insights
DXY Correlations Table
DXY Movement	USD Implication	EUR/USD	USD/JPY	GBP/USD	USD/CAD
↑ Rising	Strong USD	↓ Falling	↑ Rising	↓ Falling	Oil Dependent
↓ Falling	Weak USD	↑ Rising	↓ Falling	↑ Rising	Oil Dependent
Volatility Thresholds
Indicator	Low Volatility	Normal	Elevated	Extreme
VIX	< 15	15-20	20-30	> 30
VVIX	< 90	90-110	110-120	> 120
SKEW	< 125	125-135	135-145	> 145
MOVE	< 100	100-120	120-150	> 150
GVZ	< 18	18-25	25-35	> 35
Regional Market Correlations
Region	Index	Risk Sensitivity	FX Impact
US	SPY/DJI	High	USD, Risk Sentiment
Europe	IBEX	Medium	EUR, CHF
Asia	HSI/SSEC	High	AUD, NZD, JPY
Emerging	BSESN	Very High	Risk Currencies
Oil Impact Matrix (USD/CAD)
Oil Trend	DXY Trend	USD/CAD Signal	Confidence
↑ Bullish	Any	↓ Bearish	High
↓ Bearish	↑ Bullish	↑ Bullish	High
↓ Bearish	↓ Bearish	→ Neutral	Low
Gold Volatility (GVZ) Impact
GVZ Level	Market Implication	Safe Haven Demand
< 18	Calm Markets	Low
18-25	Normal Conditions	Moderate
25-35	Uncertainty	High (Gold, JPY, CHF)
> 35	Fear/Crisis	Very High
🔧 Advanced Features
1. Currency Strength Matrix

Calculates relative strength scores (0-100) for major currencies based on:

    Spot price trends across multiple pairs

    Futures index performance (when available)

    Technical indicator strength (ADX, trend consistency)

    Regional equity market correlations

2. Risk Management Integration

    Position sizing based on volatility regime

    Stop-loss recommendations using ATR

    Correlation analysis to avoid over-concentration

    VIX-based leverage adjustment

3. Multi-Timeframe Analysis

    Combines daily data with longer-term trends

    Futures-spot divergence detection

    Leading vs lagging indicator weighting

    Regional market opening/closing effects

4. Global Sentiment Engine
python

def calculate_global_sentiment(self):
    """Combines regional indices for global risk assessment"""
    us_sentiment = self.analyze_index_sentiment('SPY')
    eu_sentiment = self.analyze_index_sentiment('IBEX') 
    asia_sentiment = self.analyze_index_sentiment('HSI')
    
    return self.combine_regional_views(us_sentiment, eu_sentiment, asia_sentiment)

🛠️ Extending the Framework
Adding New Factors
python

# Custom factor integration
def analyze_custom_factor(self, factor_data):
    """Add your custom analysis logic"""
    factor_data = self.add_technical_indicators(factor_data)
    trend, strength = self.calculate_trend_strength(factor_data)
    return {'trend': trend, 'strength': strength}

# Regional analysis enhancement
def analyze_regional_markets(self):
    """Enhanced regional market analysis"""
    regions = {
        'US': ['SPY', 'QQQ', 'DJI'],
        'Europe': ['IBEX', ' regional_eu_index'],
        'Asia': ['HSI', 'SSEC', 'BSESN']
    }
    return self.calculate_regional_strength(regions)

Custom Signal Generation
python

def custom_signal_generator(self, pair_analysis, custom_factors):
    """Implement your proprietary logic"""
    # Your custom signal generation
    return signal, confidence, reasoning

Volatility Composite Index
python

def create_volatility_composite(self):
    """Creates a composite volatility score across all volatility indices"""
    vix_score = self.normalize_vol_score(self.data['VIX'])
    vvix_score = self.normalize_vol_score(self.data['VVIX'])
    gvz_score = self.normalize_vol_score(self.data['GVZ'])
    move_score = self.normalize_vol_score(self.data['MOVE'])
    
    composite = (vix_score + vvix_score + gvz_score + move_score) / 4
    return composite

✅ Best Practices
Data Quality

    Ensure consistent date formats across all files

    Handle missing data with appropriate fallbacks

    Validate data ranges for alignment

    Regular data integrity checks

Risk Management

    Use confidence scores for position sizing

    Implement correlation checks between signals

    Consider volatility-adjusted position sizing

    Monitor VVIX for volatility regime changes

Performance Optimization

    Cache technical indicator calculations

    Use vectorized operations for large datasets

    Implement incremental updates for real-time analysis

    Parallel processing for multiple currency pairs

Model Validation

    Backtest signals against historical data

    Validate volatility regime classifications

    Monitor correlation stability

    Regular performance reviews

🌟 Pro Tips
Gold Volatility (GVZ) Insights

    GVZ > 25 often precedes safe-haven flows to JPY and CHF

    Combining GVZ with VIX provides cross-asset fear assessment

    Gold volatility spikes can signal currency market stress

VVIX Interpretation

    VVIX > 100 indicates unstable volatility expectations

    Rising VVIX with stable VIX suggests impending volatility breakouts

    VVIX divergence from VIX can signal regime changes

Regional Index Correlations

    Asian session (HSI) often sets tone for AUD and NZD

    European opens (IBEX) impact EUR and GBP

    US session (SPY) drives overall risk sentiment

🤝 Contributing

We welcome contributions to enhance this framework! Areas for improvement:

    Additional volatility indices

    Machine learning integration

    Real-time data feeds

    Backtesting capabilities

    Portfolio optimization

    Risk management systems

Please ensure proper testing of any modifications and maintain the code documentation.
📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
⚠️ Disclaimer

This framework is for analytical and educational purposes only. It should be used as part of a comprehensive trading strategy with proper risk management. Past performance is not indicative of future results. Always consult with qualified financial professionals before making investment decisions.

Maintained with ❤️ for the quantitative finance community
