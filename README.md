# 🌍 World Universities Dataset

This repository contains a structured and comprehensive JSON dataset of top universities worldwide, scraped from publicly available sources. It includes key data points such as global rankings, student demographics, academic scores, subjects offered, and institutional links.

This dataset is ideal for:
- Developers building university comparison tools or dashboards
- Researchers analyzing global education trends
- Students and institutions exploring academic insights
- Open-source projects or public APIs

---

## 📦 File Format

The main file is `updated_universities.json`, which is a JSON array where each object represents a university.

### 📄 Sample Entry

```json
{
  "rank": "1",
  "name": "University of Oxford",
  "web_address": "https://...",
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
    "Life Sciences3rd",
    "Biological Sciences",
    ...
  ],
  "description": "The University of Oxford is a collegiate research university...",
  "image_url": "https://...",
  "country": "United Kingdom",
  "country_code": "UK"
}
🚀 How to Use
You can:

Clone this repo and use the data locally:

bash
Copy
Edit
git clone https://github.com/<your-username>/world-universities-data.git
Access the JSON file directly:

bash
Copy
Edit
https://raw.githubusercontent.com/<your-username>/world-universities-data/main/updated_universities.json
Use as a simple API (example in JavaScript):

js
Copy
Edit
fetch("https://raw.githubusercontent.com/<your-username>/world-universities-data/main/updated_universities.json")
  .then(res => res.json())
  .then(data => {
    console.log(data[0]); // First university
  });
You can also host this file on services like GitHub Pages or Vercel to build a frontend or API layer.

🤝 Contributing
Want to help grow this dataset? Great!

✍️ How to Contribute:
Fork this repo

Add or improve university entries in updated_universities.json

Submit a pull request with a clear description of your changes

Please make sure:

Entries are accurate and cleanly formatted

All required fields are present

Optional: Provide sources in pull request comments

📈 API Suggestion (Optional)
You can turn this dataset into a basic REST API using:

json-server

Express.js

Firebase or Supabase

Example with json-server:

bash
Copy
Edit
npm install -g json-server
json-server --watch updated_universities.json --port 3000
Then access:
http://localhost:3000 for full dataset
http://localhost:3000?country=UK for filtering, etc.

📜 License
This project is licensed under the MIT License.

You are free to use, modify, and distribute this dataset for personal, academic, or commercial use, with proper attribution.

See LICENSE for more details.

🌐 Acknowledgments
Data compiled from publicly available information on university ranking platforms. This repository is for open educational use only and is not affiliated with any ranking organization.

✉️ Questions?
Open an issue or reach out via GitHub if you'd like to collaborate or build something with this dataset!
