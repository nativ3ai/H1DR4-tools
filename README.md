# Complete Staking Health Check CLI Tool

A comprehensive blockchain staking analysis tool that provides detailed health metrics, flow analysis, and projections for staking protocols. This tool analyzes both staking and unstaking events to give you a complete view of your protocol's health.

## Features

- 📊 **Complete Health Metrics**: Staking percentage, flow analysis, trend detection
- 🔄 **Flow Analysis**: Detailed comparison of staking vs unstaking activities
- 🔮 **Future Projections**: 30-day projections and selling pressure analysis
- 📈 **Trend Detection**: Automatic trend classification (Growth, Stable, Decline)
- ⚠️ **Risk Assessment**: Liquidity risk, growth sustainability, market impact
- 📋 **Executive Summary**: Clear recommendations and priority actions
- 💾 **JSON Export**: Save detailed reports for further analysis

## Requirements

- Python 3.7+
- Alchemy API key (for Base network access)
- Internet connection

## Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd staking-health-check
   ```

2. **Install dependencies**
   ```bash
   pip install requests
   ```

3. **Configure your API key**
   
   Open `complete_staking_health_check_en.py` and replace the placeholder:
   ```python
   def __init__(self, alchemy_key: str = "YOUR_ALCHEMY_API_KEY_HERE"):
   ```
   
   With your actual Alchemy API key:
   ```python
   def __init__(self, alchemy_key: str = "your_actual_api_key_here"):
   ```

## Getting Your Alchemy API Key

1. Visit [Alchemy](https://www.alchemy.com/)
2. Sign up for a free account
3. Create a new app for Base Mainnet
4. Copy your API key from the dashboard

## Usage

### Basic Usage

Run the tool interactively:
```bash
python3 complete_staking_health_check_en.py
```

The tool will prompt you for:
- Staking contract address
- Token contract address
- Analysis period (optional, defaults to 14 days)

### Command Line Arguments

```bash
python3 complete_staking_health_check_en.py \
  --staking 0x1234567890abcdef... \
  --token 0xabcdef1234567890... \
  --days 30 \
  --supply 1000000000 \
  --output my_report.json
```

### Parameters

- `--staking`: Staking contract address (required)
- `--token`: Token contract address (required)
- `--days`: Analysis period in days (default: 14)
- `--supply`: Total token supply (default: 1,000,000,000)
- `--output`: Output JSON file name (optional)

## Example Usage

### Analyze a 30-day period
```bash
python3 complete_staking_health_check_en.py \
  --staking 0x742d35Cc6634C0532925a3b8D400E4C0C0C8C0C8 \
  --token 0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913 \
  --days 30 \
  --supply 500000000
```

### Quick 7-day analysis
```bash
python3 complete_staking_health_check_en.py \
  --staking 0x742d35Cc6634C0532925a3b8D400E4C0C0C8C0C8 \
  --token 0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913 \
  --days 7
```

## Output

The tool provides:

### Console Output
- Real-time progress updates
- Phase-by-phase analysis results
- Complete health report with metrics
- Executive summary with recommendations

### JSON Report
Detailed JSON file containing:
- Raw data and events
- Calculated metrics
- Projections and risk assessment
- Executive summary

## Understanding the Results

### Health Scores
- 🟢 **EXCELLENT**: Strong staking activity, positive trends
- 🟡 **GOOD**: Healthy metrics with minor concerns
- 🟠 **MODERATE**: Mixed signals, requires attention
- 🔴 **CRITICAL**: Immediate action required

### Key Metrics
- **Staking Percentage**: % of total supply currently staked
- **Net Flow**: Difference between staking and unstaking
- **Selling Pressure**: Upcoming unstaking events (14-day window)
- **Trend Direction**: Overall protocol direction

### Risk Levels
- **Liquidity Risk**: Potential impact on token liquidity
- **Growth Sustainability**: Long-term growth prospects
- **Market Impact**: Expected market effects

## Customization

### Adding New Function Signatures

To monitor different staking/unstaking functions, modify the signatures in the class:

```python
self.stake_signatures = [
    "0xa694fc3a",  # stake()
    "0xb6b55f25",  # deposit()
    "0x1249c58b",  # mint()
    "0x12345678"   # your_custom_function()
]

self.unstake_signatures = [
    "0xf48355b9",  # toggleAutoRenew()
    "0x2e1a7d4d",  # withdraw()
    "0x3d18b912",  # unstake()
    "0x87654321"   # your_custom_unstake()
]
```

### Adjusting Analysis Parameters

Modify the health score thresholds in `calculate_complete_health_metrics()`:

```python
# Staking percentage thresholds
if staking_percentage > 40:    # Excellent
if staking_percentage > 20:    # Good
if staking_percentage > 10:    # Moderate
```

## Troubleshooting

### Common Issues

1. **API Rate Limits**
   - The tool includes automatic rate limiting
   - For large analyses, consider using a paid Alchemy plan

2. **No Events Found**
   - Verify contract addresses are correct
   - Check if the contracts use standard function signatures
   - Try a longer analysis period

3. **Balance Not Found**
   - Tool will estimate balance from activity
   - Ensure token contract implements standard ERC-20 `balanceOf`

### Error Messages

- `❌ Staking contract address required!`: Provide valid contract address
- `❌ Analysis interrupted by user`: Ctrl+C was pressed
- `❌ Error during analysis`: Check API key and network connection

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is open source. Please check the LICENSE file for details.

## Support

For issues and questions:
1. Check the troubleshooting section
2. Review existing GitHub issues
3. Create a new issue with detailed information

## Disclaimer

This tool is for analysis purposes only. Always verify results independently and consider multiple data sources when making important decisions about your staking protocol.

---

**Note**: This tool analyzes on-chain data and provides estimates. Actual results may vary based on network conditions, contract implementations, and other factors.

