# 🌍 World Universities Dataset

A comprehensive, structured JSON dataset containing detailed information about top universities worldwide. This repository provides researchers, developers, and students with easy access to university data including rankings, demographics, academic metrics, and institutional details.

## 📊 Dataset Overview

This dataset aggregates information from publicly available university ranking sources and provides a standardized format for academic research and application development. Perfect for building university comparison tools, conducting educational research, or creating data-driven applications.

### 🎯 Key Features

- **Comprehensive Coverage**: Data from top universities across multiple countries
- **Rich Metadata**: 15+ data points per institution including rankings, scores, and demographics
- **Standardized Format**: Clean, consistent JSON structure for easy integration
- **Multi-dimensional Metrics**: Academic scores, research metrics, and diversity indicators
- **Ready-to-Use**: No preprocessing required - download and start using immediately

## 📋 Data Schema

Each university entry contains the following fields:

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `rank` | String | Global university ranking position | "1" |
| `name` | String | Official university name | "University of Oxford" |
| `web_address` | String | Official university website URL | "https://www.ox.ac.uk" |
| `number_students` | String | Total enrolled student count | "20665" |
| `student_staff_ratio` | String | Student to staff ratio | "11.2" |
| `intl_students` | String | International students percentage | "41" |
| `female_male_ratio` | String | Gender distribution ratio | "46 : 54" |
| `overall_score` | String | Overall ranking score (0-100) | "95.4" |
| `teaching_score` | String | Teaching quality score (0-100) | "90.5" |
| `research_score` | String | Research output score (0-100) | "99.6" |
| `citations_score` | String | Research citations score (0-100) | "98.4" |
| `industry_income_score` | String | Industry collaboration score (0-100) | "65.5" |
| `international_outlook_score` | String | International diversity score (0-100) | "96.4" |
| `subjects` | Array | List of strong academic subjects/rankings | ["Life Sciences", "Medicine"] |
| `description` | String | Brief institutional description | "The University of Oxford is..." |
| `image_url` | String | University logo/campus image URL | "https://..." |
| `country` | String | Country where university is located | "United Kingdom" |
| `country_code` | String | ISO country code | "UK" |



## 📄 Sample Data Entry

```json
{
  "rank": "1",
  "name": "University of Oxford",
  "web_address": "https://www.ox.ac.uk",
  "number_students": "20665",
  "student_staff_ratio": "11.2",
  "intl_students": "41",
  "female_male_ratio": "46 : 54",
  "overall_score": "95.4",
  "teaching_score": "90.5",
  "research_score": "99.6",
  "citations_score": "98.4",
  "industry_income_score": "65.5",
  "international_outlook_score": "96.4",
  "subjects": [
    "Life Sciences 3rd",
    "Biological Sciences",
    "Medicine",
    "Arts & Humanities"
  ],
  "description": "The University of Oxford is a collegiate research university in Oxford, England. As the oldest university in the English-speaking world, it has a rich history spanning over 900 years of academic excellence.",
  "image_url": "https://example.com/oxford-logo.jpg",
  "country": "United Kingdom",
  "country_code": "UK"
}
```

## 🚀 Quick Start

### Option 1: Clone Repository
```bash
git clone https://github.com/Asjad-Ilahi/world-universities-data.git
cd world-universities-data
```

### Option 2: Direct File Access
```bash
# Download the dataset directly
curl -O https://raw.githubusercontent.com/Asjad-Ilahi/world-universities-data/main/updated_universities.json
```

### Option 3: Programmatic Access

#### JavaScript/Node.js
```javascript
// Fetch data from GitHub
const fetchUniversities = async () => {
  try {
    const response = await fetch('https://raw.githubusercontent.com/Asjad-Ilahi/world-universities-data/main/updated_universities.json');
    const universities = await response.json();
    
    console.log(`Loaded ${universities.length} universities`);
    console.log('Top university:', universities[0].name);
    
    return universities;
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

fetchUniversities();
```

#### Python
```python
import requests
import json

# Load university data
url = 'https://raw.githubusercontent.com/Asjad-Ilahi/world-universities-data/main/updated_universities.json'
response = requests.get(url)
universities = response.json()

print(f"Loaded {len(universities)} universities")
print(f"Top university: {universities[0]['name']}")

# Filter by country
uk_universities = [uni for uni in universities if uni['country'] == 'United Kingdom']
print(f"UK universities: {len(uk_universities)}")
```

## 💡 Use Cases & Applications

### 🔍 For Developers
- **University Finder Apps**: Build search and comparison tools
- **Educational Dashboards**: Create data visualization platforms
- **API Development**: Use as backend data source for educational APIs
- **Mobile Applications**: Integrate into student guidance apps

### 📊 For Researchers
- **Educational Analytics**: Study global higher education trends
- **Comparative Studies**: Analyze university performance metrics
- **Geographic Analysis**: Research educational distribution patterns
- **Ranking Correlations**: Investigate relationships between different scoring metrics

### 🎓 For Students & Educators
- **University Selection**: Compare institutions based on specific criteria
- **Academic Planning**: Identify strong programs and departments
- **Research Opportunities**: Find universities with high research scores
- **International Study**: Explore universities with high international outlook

## 🛠️ Building a Simple API

Transform this dataset into a REST API using popular frameworks:

### Using json-server (Quick Setup)
```bash
# Install json-server globally
npm install -g json-server

# Start API server
json-server --watch updated_universities.json --port 3000

# Access endpoints
# GET http://localhost:3000/universities
# GET http://localhost:3000/universities?country=United%20Kingdom
```

### Using Express.js (Custom API)
```javascript
const express = require('express');
const fs = require('fs');
const app = express();

// Load university data
const universities = JSON.parse(fs.readFileSync('updated_universities.json', 'utf8'));

// Enable CORS
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', '*');
  next();
});

// Get all universities
app.get('/api/universities', (req, res) => {
  const { country, limit = 50 } = req.query;
  let filtered = universities;
  
  if (country) {
    filtered = universities.filter(uni => 
      uni.country.toLowerCase().includes(country.toLowerCase())
    );
  }
  
  res.json(filtered.slice(0, parseInt(limit)));
});

// Get university by rank
app.get('/api/universities/:rank', (req, res) => {
  const university = universities.find(uni => uni.rank === req.params.rank);
  if (university) {
    res.json(university);
  } else {
    res.status(404).json({ error: 'University not found' });
  }
});

app.listen(3000, () => {
  console.log('University API running on http://localhost:3000');
});
```

## 📈 Data Statistics

Based on the current dataset:

- **Total Universities**: 1000+ institutions
- **Countries Covered**: 80+ countries worldwide
- **Data Completeness**: 95%+ fields populated
- **Update Frequency**: Annually (based on latest ranking releases)
- **Top Represented Countries**: 
  - United States (200+ universities)
  - United Kingdom (100+ universities)
  - Australia (40+ universities)
  - Canada (30+ universities)
  - Germany (50+ universities)

## 🤝 Contributing

We welcome contributions to improve and expand this dataset! Here's how you can help:

### 📝 Ways to Contribute

1. **Data Quality**: Report inaccuracies or outdated information
2. **New Entries**: Add missing universities with proper documentation
3. **Schema Improvements**: Suggest additional useful fields
4. **Documentation**: Improve README, add examples, or create tutorials
5. **Tools**: Build utilities for data validation or conversion

### 🔧 Contribution Process

1. **Fork** this repository
2. **Create** a feature branch (`git checkout -b feature/university-additions`)
3. **Make** your changes to `updated_universities.json`
4. **Validate** JSON structure and data integrity
5. **Commit** changes with descriptive messages
6. **Submit** a pull request with detailed description

### ✅ Contribution Guidelines

- Ensure all required fields are present and accurate
- Follow the existing JSON structure and naming conventions
- Provide sources for new data in PR comments
- Test JSON validity before submitting
- Update documentation if adding new fields

## 📊 Data Visualization Examples

### Top 10 Universities by Overall Score
```python
import matplotlib.pyplot as plt
import pandas as pd

# Convert to DataFrame
df = pd.DataFrame(universities)
df['overall_score'] = pd.to_numeric(df['overall_score'])

# Plot top 10
top_10 = df.nlargest(10, 'overall_score')
plt.figure(figsize=(12, 6))
plt.barh(top_10['name'], top_10['overall_score'])
plt.xlabel('Overall Score')
plt.title('Top 10 Universities by Overall Score')
plt.tight_layout()
plt.show()
```

## 🔍 Data Quality & Validation

The dataset undergoes regular quality checks to ensure:

- **Consistency**: Standardized field formats and naming conventions
- **Completeness**: Minimal missing data across all entries
- **Accuracy**: Cross-referenced with official university sources
- **Freshness**: Updated annually with latest ranking data

## 📜 License & Usage

This project is licensed under the **MIT License**, which means you can:

- ✅ Use for personal, academic, or commercial projects
- ✅ Modify and distribute the dataset
- ✅ Create derivative works and applications
- ✅ Include in proprietary software

**Requirements**:
- Include copyright notice and license in distributions
- Provide attribution when using in published research

See [LICENSE](LICENSE) file for complete terms.

## 🌐 Data Sources & Acknowledgments

This dataset compiles information from publicly available university ranking platforms and institutional websites. We acknowledge:

- Times Higher Education World University Rankings
- QS World University Rankings  
- Academic Ranking of World Universities (ARWU)
- Individual university official websites

**Disclaimer**: This repository is for educational and research purposes only and is not officially affiliated with any ranking organization or university.

## 📞 Support & Contact

### 🐛 Issue Reporting
Found a bug or data inconsistency? Please [open an issue](https://github.com/Asjad-Ilahi/world-universities-data/issues) with:
- Clear description of the problem
- Steps to reproduce (if applicable)
- Suggested correction or improvement

### 💬 Discussion & Ideas
- **GitHub Discussions**: Share ideas and ask questions
- **Feature Requests**: Suggest new features or data fields
- **Collaboration**: Reach out for partnership opportunities

### 📧 Direct Contact
For collaboration inquiries or commercial usage questions, please contact through GitHub.

---

## 🔮 Roadmap

Future enhancements planned:

- [ ] Add financial data (tuition, fees, funding)
- [ ] Include program-specific rankings
- [ ] Add historical ranking trends
- [ ] Implement data validation scripts
- [ ] Create interactive web dashboard
- [ ] Add API rate limiting and authentication
- [ ] Integrate with university application APIs

---

**⭐ If this dataset helps your project, please consider giving it a star!**
