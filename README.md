# IPL 2026 Analysis & Insights Generator

A comprehensive data science project for analyzing IPL (Indian Premier League) cricket matches, generating predictive models, visualizations, and AI-powered insights for the 2026 season. This project leverages historical match data to provide deep analytics, player performance tracking, and social media-ready content.

## 🚀 Features

- **Data Ingestion**: Load and process IPL match data from Cricsheet JSON files and live scraping from Cricinfo.
- **Data Processing**: Clean, feature engineering, and historical dataset building.
- **Predictive Models**:
  - Expected Runs Model: Predict ball-by-ball expected runs using machine learning.
  - Impact Model: Calculate player and team impact scores.
- **Analysis Modules**:
  - Live Insights: Real-time match analysis.
  - Historical Comparisons: Compare current matches with past performances.
  - Player Intent Analysis: Understand batting/bowling strategies.
  - Surge Analysis: Identify run rate surges and turning points.
  - Zone Analysis: Pitch zone performance metrics.
- **Visualizations**: Generate pitch maps, run rate graphs, and interactive charts.
- **AI Insights**: Use Google Gemini AI to generate contextual match insights and narratives.
- **Social Media Assets**: Create LinkedIn posts, Instagram reels, and other shareable content.
- **Modular Architecture**: Clean, extensible codebase with separate modules for ingestion, processing, modeling, analysis, and visualization.

## 📊 Data Sources

- **Historical Data**: IPL matches from previous seasons (stored as JSON files from Cricsheet).
- **Live Data**: Scraped from ESPN Cricinfo for real-time updates.
- **Processed Data**: Ball-level and match-level features stored in CSV format.

## 🏗️ Project Structure

```
IPL_2026/
├── config/                 # Configuration files (YAML)
├── data/
│   ├── raw/                # Raw data (historical JSONs, scraped data)
│   └── processed/          # Cleaned and feature-engineered data
├── outputs/
│   ├── charts/             # Generated visualizations
│   ├── linkedin_assets/    # Social media content
│   └── reels_ready/        # Video-ready assets
├── scripts/                # Executable scripts
│   ├── build_historical_dataset.py  # Build historical CSV
│   ├── run_pipeline.py              # Main analysis pipeline
│   └── test_scraper.py               # Test data scraping
├── src/                    # Source code
│   ├── analysis/           # Analysis modules (insights, comparisons, etc.)
│   ├── ingestion/          # Data loading and scraping
│   ├── models/             # ML models (expected runs, impact)
│   ├── processing/         # Data cleaning and feature engineering
│   ├── utils/              # Utilities (match selector)
│   └── visualization/      # Plotting and charting
├── requirements.txt        # Python dependencies
├── README.md               # This file
└── Match1_analysis.ipynb   # Jupyter notebook for exploratory analysis
```

## 🛠️ Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/SouRitra01/IPL_2026.git
   cd IPL_2026
   ```

2. **Set Up Virtual Environment** (Recommended):
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Set Environment Variables**:
   - For AI insights: `export GOOGLE_API_KEY=your_google_api_key`
   - (Get your key from [Google AI Studio](https://makersuite.google.com/app/apikey))

## 🚀 Usage

### Build Historical Dataset
Compile all historical match data into a single CSV:
```bash
python scripts/build_historical_dataset.py
```

### Run Full Analysis Pipeline
Process a match, generate models, visualizations, and insights:
```bash
python scripts/run_pipeline.py
```
- This loads data, cleans it, adds features, runs models, creates plots, and generates AI insights.

### Test Data Scraping
Verify scraping functionality:
```bash
python scripts/test_scraper.py
```

### Jupyter Notebook
For exploratory analysis:
- Open `Match1_analysis.ipynb` in Jupyter Lab/Notebook.
- Run cells to analyze a sample match interactively.

## 📈 Models & Analysis

- **Expected Runs Model**: Uses scikit-learn to predict expected runs based on ball features (e.g., batsman, bowler, venue).
- **Impact Model**: Calculates win probability changes and player contributions.
- **Context Builder**: Aggregates match summaries, historical stats, and player profiles for AI input.
- **Insight Generator**: Leverages Google Gemini to create human-readable insights from data.

## 🎨 Visualizations

- **Run Rate Graphs**: Track scoring surges and partnerships.
- **Pitch Maps**: Show ball locations and outcomes.
- **Charts**: Custom plots for match analysis.

## 🤖 AI Integration

Powered by Google Gemini 1.5 Flash for generating:
- Match summaries
- Player insights
- Strategic analysis
- Social media narratives

## 📝 Configuration

Edit `config/config.yaml` to customize:
- Data paths
- Match IDs
- Model parameters

## 🤝 Contributing

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/your-feature`.
3. Commit changes: `git commit -m 'Add your feature'`.
4. Push to branch: `git push origin feature/your-feature`.
5. Open a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Contact

For questions or collaborations, reach out via GitHub Issues.

---

**Note**: Ensure your Google API key is set securely and never commit it to version control. Use environment variables for sensitive data.
