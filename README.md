# SalesmanBot – AI Shopping Assistant

A powerful Chrome extension that acts as your personal AI assistant for discovering and comparing **different products** on leading e-commerce websites such as Amazon, Flipkart, Walmart. Whether you’re shopping for PC components, smartphones, appliances, or fashion, SalesmanBot brings AI-powered recommendations and smart filtering to elevate your online shopping experience.

---

## Features

- 🤖 **AI-Powered Recommendations**: Uses Google's Gemini-1.5-flash to analyze and intelligently recommend the best products across categories  
- 💰 **Budget-Aware Filtering**: Understands your budget and narrows down the choices accordingly  
- 🔍 **Smart Query Parsing**: Parses your natural language queries to capture specs, brands, preferences, or intended use  
- ⚡ **Real-time Analysis**: Extracts and analyzes product listings on any supported e-commerce page  
- 🛒 **Multi-Site Support**: Works seamlessly on Amazon India, Amazon.com, and Flipkart  
- 📊 **Detailed Product Info**: Shows ratings, key specifications, compatibility/fit notes, and pros & cons—even for non-tech products

---

## Installation

1. **Download the Extension**
    - Clone or download this repository
    - Ensure all files are in the `Salesman Bot Extension` folder

2. **Load in Chrome**
    - Open Chrome and go to `chrome://extensions/`
    - Enable "Developer mode" (toggle in top-right)
    - Click "Load unpacked" and select the extension folder
    - The SalesmanBot icon should appear in your toolbar

3. **Get Gemini API Key**
    - Visit Google AI Studio and create a free API key
    - Copy the key for setup

---

## Setup & Usage

### Initial Setup

1. **Navigate to a Supported Site**: Amazon India, Amazon.com, or Flipkart  
2. **Click the Extension Icon** to open the popup  
3. **Enter your Gemini API key** when prompted  
4. **Click "Setup AI"** to enable AI-powered recommendations  

### Using the Extension

1. **Go to a product listing page** (e.g., search results or category pages)
2. **Open the extension popup**
3. **Type your query in natural language**, e.g.:
    - For any product:
        - `wireless headphones under ₹5,000 with good battery life`
        - `water bottle, BPA-free, 1 liter`
        - `sofa set for small living room under ₹35,000`
    - For PC category (example):
        - `gaming PC under ₹70,000 with 16GB RAM and SSD`
        - `Intel processor for video editing under ₹25,000`

### Query Examples

- **Budget queries**: `under ₹1,000`, `around 30k`, `budget of ₹500`
- **Specification queries**: `noise cancellation`, `1TB storage`, `4-star energy rating`
- **Purpose queries**: `for traveling`, `kids`, `for gaming`, `work from home`
- **Brand queries**: `Sony`, `Apple`, `Prestige`, `Intel`, `ASUS`
- **Category queries**: `headphones`, `washing machine`, `PC components`, `smartphone`, `kitchen appliances`

---

## How It Works

### 1. Product Extraction

- **Smart Selectors**: Uses advanced CSS selectors to extract all relevant product info on listing pages
- **Multi-Site Support**: Extraction logic custom-tailored for Amazon and Flipkart
- **Rich Data**: Extracts title, price, ratings, images, salient features/specs, and links

### 2. Query Parsing

- **Natural Language Processing**: Understands your goals, budget, important specs, preferred brands, and intended use (across all product categories)
- **Budget Recognition**: Handles formats like `₹2,000`, `under 1 lakh`, `50 dollars`
- **Spec Extraction**: Identifies unique product properties (color, storage, material, warranty, etc.—relevant to category)
- **Brand Detection**: Recognizes brands across different retail categories

### 3. AI Analysis

- **Gemini Integration**: Uses Google Gemini-1.5-flash for deep product comparison and recommendation logic
- **Category Adaptation**: Highlights relevant pros/cons per product category  
    - For PCs: Compatibility warnings, performance notes  
    - For apparel: Size/fit tips  
    - For appliances: Energy efficiency, warranty info  
- **Score-based Ranking**: Evaluates matches for your query and requirements
- **Explanations**: Tells you *why* a product is recommended

### 4. Smart Filtering

- **Budget Filtering**: Respects your price constraints, with intelligent tolerance
- **Category Matching**: Detects and filters across virtually any product type from electronics to home goods to apparel and more
- **Brand Preferences**: Prioritizes any named brands in your query
- **Spec Requirements**: Ensures products meet minimum user-specified criteria

---

## File Structure

```
Salesman Bot Extension/
├── manifest.json # Extension configuration
├── popup.html # Extension popup interface
├── popup.js # Popup logic and UI handling
├── content.js # Main content script
├── background.js # Background service worker
├── style.css # Popup styling
├── Salesman bot.png # Extension icon
└── utils/
├── productExtractor.js # Product extraction/adaptation logic
├── queryParser.js # Smart query parsing and analysis
└── aiService.js # Gemini AI integration
```


---

## Technical Details

### Supported Sites

- **Amazon India** (`*.amazon.in`)
- **Amazon.com** (`*.amazon.com`)
- **Flipkart** (`*.flipkart.com`)
- *Extendable* to more sites (see below)

### Permissions Required

- `scripting`: To inject content scripts
- `activeTab`: To access content on your active tab
- `storage`: To securely save your API key and preferences
- `notifications`: For contextual product/feature notifications
- `contextMenus`: Power right-click options for additional actions

### API Usage

- Utilizes **Google Gemini API** for AI-powered product analysis and conversation
- **Free tier available** (ideal for personal and educational use)
- API key is securely stored *locally* in Chrome

---

## Privacy & Security

- **Local, Private Processing**: All your data stays on your device
- **No Data Collection**: Your browsing and queries aren’t collected or stored by the extension authors
- **Secure API Key Handling**: Stored only in Chrome’s secure storage
- **No External Analytics**: No tracking or analytics scripts

---

## Troubleshooting

### Content Script Not Loading

1. **Check Supported Site**: Make sure you’re on an Amazon or Flipkart product search/category page
2. **Reload the Extension**: Use `chrome://extensions/` → reload SalesmanBot
3. **Refresh the Page**: After reloading the extension, reload your e-commerce site page
4. **Console Logs**: Open DevTools (F12) and inspect the Console tab for clues
5. **Try Various Pages**: Some listings may work better than others due to layout differences

### AI Not Working

1. **API Key**: Ensure your Gemini API key is entered and valid
2. **API Quota**: Check you haven’t exceeded your free quota
3. **Network**: Confirm your device has a working internet connection

### No Products Found

1. **Be on Listing/Search Pages**: The extension doesn’t extract from individual product detail pages
2. **Let Listing Load**: Wait until all products are visible before activating the extension
3. **Try Alternate Queries or Categories**
4. **Check Browser Console for Debug Messages**

---

## Development

### Adding New Sites

1. **Update Manifest**: Add new URL patterns under `matches` and `host_permissions`
2. **Extend ProductExtractor**: Add/modify selectors to support product listings on new sites
3. **Test Across Categories**: Ensure it works for your expanded range of product types

### Customizing AI Prompts

- **Edit `aiService.js`**: Improve or specialize the `buildPrompt` logic for various categories
- **Tweak AI Parameters**: Adjust temperature/max tokens for answer style and length
- **Feature Extensions**: Add new product category-specific logic

---

## Support

If you experience issues or have suggestions:

1. **Check the Console**: Error messages will often guide you
2. **Reload the Extension**
3. **Try on Different Pages or Product Categories**
4. **Open an Issue or Request on the GitHub Repository**

---

## License

This project is for **educational and personal use** only. Please ensure you comply with each e-commerce site’s terms of service when using this extension.

---

**Happy Shopping with AI! 🛍️🛠️**  
