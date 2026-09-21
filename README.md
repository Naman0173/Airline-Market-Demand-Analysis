# ✈️ Airline Market Demand Analysis

A Flask-based web application for exploring airline market demand through **flight pricing, route activity, and short-term price trends**.

The application lets users select an origin country and airport, a destination country and airport, and a departure date. It then generates an analysis covering a **10-day window** around the selected date.

## 🌐 Project Overview

The project combines:

- **Python + Flask** for the backend
- **HTML/CSS/JavaScript** for the frontend
- **Chart.js** for price-trend visualization
- **Pandas** for flight-data processing
- **AviationStack API** for country, airport, and flight information
- **Mock flight data** as a fallback/testing mode
- **Render** configuration for cloud deployment

## ✨ Features

### 🔎 Flight Search & Analysis
- Select an origin country and airport
- Select a destination country and airport
- Choose a departure date
- Analyze flight information for the selected route

### 📊 Market Insights
The dashboard provides:

- Average flight price
- Number of routes analyzed
- Number of flights found
- Selected departure date
- Popular routes
- 10-day average price trends
- Flight-level details including airline, flight number, date, time, route, and price

### 📈 Interactive Visualization
Price trends are displayed using **Chart.js**, making it easier to understand how estimated flight prices change around the selected date.

### ⚡ Caching & Fallbacks
The application caches country and airport data to reduce repeated API requests.

It also contains fallback country and airport data for several countries, allowing parts of the application to remain usable when API data is unavailable.

### 🧪 Mock Data Mode
The current flight-analysis flow uses generated mock flight data by default. This makes the application easy to test without depending on live flight availability.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Backend programming |
| Flask | Web application framework |
| Pandas | Data processing and analysis |
| Requests | API requests |
| python-dotenv | Environment variable management |
| HTML5 | Frontend structure |
| CSS3 | Frontend styling |
| JavaScript | Frontend interaction |
| Chart.js | Data visualization |
| AviationStack API | Aviation data |
| Render | Deployment |

---

## 📁 Project Structure

```text
Airline_Market_Demand_Analysis/
│
├── aman_airline_app.py       # Flask application
├── render.yaml               # Render deployment configuration
│
└── templates/
    └── index.html            # Web interface
```

> **Note:** The repository currently does not include a `requirements.txt` file. Create one before deploying to platforms that rely on the Render configuration.

A suitable `requirements.txt` is:

```txt
Flask
requests
pandas
python-dotenv
gunicorn
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<YOUR-USERNAME>/Airline_Market_Demand_Analysis.git
cd Airline_Market_Demand_Analysis
```

### 2. Create a virtual environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

#### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the API key

Create a `.env` file in the project root:

```env
API_KEY=your_aviationstack_api_key
```

The application reads the API key using `python-dotenv`.

**Do not commit your `.env` file to GitHub.**

Add this to `.gitignore`:

```gitignore
.env
venv/
__pycache__/
*.pyc
```

### 5. Run the application

The Flask application is currently defined in `naman_airline_app.py`.

Run:

```bash
python aman_airline_app.py
```

Then open:

```text
http://127.0.0.1:5000
```

---

## 🔌 AviationStack API

The application is designed to work with the [AviationStack](https://aviationstack.com/) API.

The backend can request:

- Countries
- Airports
- Flight schedules

The API key is supplied through the `API_KEY` environment variable.

### API configuration

The application uses:

```text
http://api.aviationstack.com/v1/
```

If API requests fail, the application falls back to predefined country/airport data and generated flight data where applicable.

---

## 📅 How the Analysis Works

When a user selects a departure date, the application creates an analysis window around that date.

```text
5 days before
       ↓
Selected date
       ↓
5 days after
```

For each date, flight information is processed and the application calculates:

- Daily average price
- Overall average price
- Route frequency
- Flight count
- Flight details

The frontend then displays the results in cards, tables, and a price-trend chart.

---

## 🧮 Mock Flight Data

For testing, the application can generate simulated flight data.

Mock data includes:

- Random flight numbers
- Random airlines
- Random prices
- Departure times
- Origin and destination airports

The generated prices include basic variation based on:

- Days until departure
- Weekend vs. weekday travel
- Random base pricing

This data is **synthetic** and should not be treated as real market pricing.

---

## ☁️ Deployment on Render

The repository includes a `render.yaml` configuration intended for Render.

Before deploying, make sure the deployment configuration matches the actual Flask entry point.

The current application file is:

```text
aman_airline_app.py
```

while the current `render.yaml` starts:

```text
python app.py
```

Therefore, update the start command to match the application file, for example:

```yaml
startCommand: gunicorn naman_airline_app:app
```

Also ensure `requirements.txt` exists and includes the required dependencies.

### Environment Variable

Add the following environment variable in Render:

```text
API_KEY=your_aviationstack_api_key
```

---

## 🔗 Application Routes

The Flask backend currently exposes:

| Route | Method | Purpose |
|---|---|---|
| `/` | GET | Main dashboard |
| `/get_airports/<country_iso2>` | GET | Retrieve airports for a country |
| `/analyze` | POST | Analyze flight data |

---

## 🎯 Use Cases

This project can be used as a starting point for:

- Airline market analysis
- Flight price exploration
- Route-demand analysis
- Aviation data visualization
- Data analytics portfolio projects
- Flask dashboard development
- API integration projects

---

## 🔮 Future Improvements

Potential enhancements include:

- [ ] Add a complete `requirements.txt`
- [ ] Add real-time flight pricing
- [ ] Add airline comparison
- [ ] Add route-demand forecasting
- [ ] Add historical price storage
- [ ] Add more advanced statistical analysis
- [ ] Add machine-learning-based price prediction
- [ ] Add interactive geographic maps
- [ ] Add downloadable CSV reports
- [ ] Add user authentication
- [ ] Add database support
- [ ] Improve mobile responsiveness
- [ ] Add automated tests
- [ ] Add CI/CD with GitHub Actions

---

## ⚠️ Disclaimer

Flight prices and flight information generated through mock mode are for **demonstration and development purposes only**.

Do not use generated mock data for real-world booking, financial, or travel decisions.

---

## 👨‍💻 Author

**Aman**

Airline Market Demand Analysis — a data-driven Flask project for exploring airline routes, pricing, and market demand.

---

## ⭐ Support

If you find this project useful, consider giving the repository a ⭐ on GitHub.
