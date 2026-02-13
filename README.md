# 🎯 Brand Intelligence Pipeline - Streamlit Interface

## Overview
AI-powered brand sentiment and archetype analyzer that processes RSS feeds using OpenAI GPT-4o-mini.

**Student:** MyclineShareena John Peter Kennedy  
**Course:** INFO7375 - Branding & AI  
**Institution:** Northeastern University  
**Assignment:** Assignment 5 - Wrap Your Tool & Know Your Market

## Features
- ✅ **RSS Feed Analysis:** Parse multiple RSS feeds simultaneously
- ✅ **Sentiment Detection:** Positive, neutral, negative classification with confidence scores
- ✅ **Brand Archetype Mapping:** 12 Jungian archetypes (Hero, Sage, Explorer, etc.)
- ✅ **Strategic Insights:** AI-generated market trends and positioning recommendations
- ✅ **Export Capability:** Download results as JSON or CSV
- ✅ **Beautiful UI:** Gradient metrics, interactive charts, responsive design
- ✅ **Cost Efficient:** ~$0.08 per 100 articles analyzed

## Live Demo
**Deployment URL:** [Will be added after successful deployment]

## Tech Stack
- **Frontend:** Streamlit 1.31.0
- **AI Model:** OpenAI GPT-4o-mini
- **RSS Parsing:** feedparser 6.0.11
- **Data Processing:** pandas 2.2.0
- **Deployment:** Streamlit Community Cloud

## Local Installation

### Prerequisites
- Python 3.9 or higher
- OpenAI API key ([Get one here](https://platform.openai.com/api-keys))

### Setup Steps

1. **Clone or download this folder**
   ```bash
   cd interface
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the app**
   ```bash
   streamlit run app.py
   ```

4. **Enter your OpenAI API key** in the sidebar when prompted

5. **Analyze feeds!** Use the default RSS feeds or add your own

## Streamlit Cloud Deployment

### Method 1: Deploy from GitHub (Recommended)

1. **Create a GitHub account** if you don't have one: https://github.com

2. **Create a new repository**
   - Repository name: `brand-intelligence-pipeline`
   - Visibility: Public
   - Initialize with README: No (we have one)

3. **Upload files to GitHub**
   - Upload `app.py`, `requirements.txt`, and `README.md`
   - Commit with message: "Initial commit - Streamlit interface"

4. **Deploy to Streamlit Cloud**
   - Go to https://streamlit.io/cloud
   - Click "Sign in" and use your GitHub account
   - Click "New app"
   - Select your repository: `brand-intelligence-pipeline`
   - Main file path: `app.py`
   - Click "Deploy!"

5. **Add OpenAI API key as secret**
   - In Streamlit Cloud dashboard, go to your app settings
   - Click "Secrets" tab
   - Add:
     ```toml
     OPENAI_API_KEY = "sk-your-actual-api-key-here"
     ```
   - Click "Save"

6. **Get your public URL**
   - Your app will be available at: `https://[your-app-name].streamlit.app`
   - Share this URL in your assignment submission!

### Method 2: Direct File Upload

1. **Go to Streamlit Cloud:** https://share.streamlit.io
2. **Create account** with GitHub
3. **Upload folder** containing `app.py` and `requirements.txt`
4. **Add API key** in Secrets settings (see step 5 above)
5. **Get public URL** from dashboard

## Usage Guide

### For End Users:
1. Open the app URL
2. (Optional) Enter your own OpenAI API key in sidebar, or use the pre-configured one
3. Add RSS feed URLs (one per line), or use the default tech/AI feeds:
   - Azure Blog
   - OpenAI Blog
   - Google AI Blog
   - Microsoft Dev Blog
4. Set max articles per feed (1-50)
5. Click "Analyze Feeds"
6. Wait 30-60 seconds for analysis
7. View results: sentiment metrics, archetype distribution, detailed article table
8. Download JSON or CSV dataset

### Default RSS Feeds Included:
- **Azure Blog:** https://azure.microsoft.com/en-us/blog/feed/
- **OpenAI Blog:** https://openai.com/blog/rss.xml
- **Google AI Blog:** http://googleaiblog.blogspot.com/atom.xml
- **Google Developers:** https://developers.googleblog.com/feeds/posts/default
- **Microsoft DevBlogs:** https://devblogs.microsoft.com/feed/

## How It Works

1. **Feed Parsing:** Uses `feedparser` to extract articles from RSS feeds
2. **API Call:** Sends each article (title + content) to GPT-4o-mini with structured prompt
3. **Analysis:** AI returns JSON with sentiment, confidence, archetype, insight, recommendation
4. **Aggregation:** Combines all results into pandas DataFrame
5. **Visualization:** Streamlit displays interactive metrics and charts
6. **Export:** Allows download as JSON or CSV

## Prompt Engineering

The GPT-4o-mini prompt is designed for:
- **Structured output:** Forces JSON format for consistent parsing
- **Brand focus:** Emphasizes market trends and brand positioning insights
- **Actionable recommendations:** Asks for specific strategy advice
- **Archetype framework:** Uses Carl Jung's 12 archetypes for brand personality mapping

## Cost Analysis
- **GPT-4o-mini pricing:** $0.000150/1K input tokens, $0.000600/1K output tokens
- **Average article:** ~500 tokens input, ~100 tokens output
- **Cost per article:** ~$0.0008
- **100 articles:** ~$0.08
- **500 articles:** ~$0.40

## Assignment 5 Context

This interface wraps the **Assignment 4 Brand Intelligence Pipeline** (n8n workflow) into a user-friendly web application for:
- Non-technical stakeholders
- Real-time analysis without n8n knowledge
- Shareable public URL
- User testing with 3 participants

## File Structure
```
interface/
├── app.py                 # Main Streamlit application
├── requirements.txt       # Python dependencies
└── README.md             # This file (deployment guide)
```

## Troubleshooting

### "OpenAI API key not found"
- Enter your API key in the sidebar text input
- OR add to Streamlit Cloud secrets (see deployment guide)

### "Failed to process feed"
- Check RSS URL is valid and accessible
- Try reducing max articles per feed
- Some feeds may have CORS restrictions

### "Analysis error"
- Verify OpenAI API key has credits
- Check internet connection
- Reduce number of feeds/articles to avoid rate limits

### Deployment fails
- Ensure `requirements.txt` has all dependencies
- Check Python version compatibility (3.9+)
- Verify GitHub repository is public

## Future Enhancements
- [ ] Add caching for faster repeated analysis
- [ ] Support for CSV feed lists
- [ ] Historical trend tracking
- [ ] Competitor brand comparison mode
- [ ] Email report scheduling
- [ ] Multi-language support

## Credits
- **Built by:** MyclineShareena John Peter Kennedy
- **Course:** INFO7375 - Branding & AI (Spring 2026)
- **Instructor:** [Professor Name]
- **University:** Northeastern University
- **Assignment:** Assignment 5 - Wrap Your Tool & Know Your Market

## License
Educational project - Northeastern University © 2026

## Contact
- **Email:** mycline.s@northeastern.edu
- **GitHub:** [Your GitHub Profile]
- **LinkedIn:** [Your LinkedIn Profile]

---

**Last Updated:** February 13, 2026  
**Version:** 1.0.0
