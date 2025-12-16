# Real-World APIs – Weather, Crypto & Space (Postman + Newman)

This project simulates **real-world API testing** from a QA automation perspective using **public production APIs**.  
It demonstrates positive testing, negative testing, authentication handling, numeric assertions, pagination, performance checks, and CI-ready execution with Newman.

---

## APIs Covered

### OpenWeather API (Weather Data)
- API-key based authentication
- Missing / invalid API key validation
- Invalid city handling
- Numeric assertions (temperature, humidity)
- Performance validation

### CoinGecko API (Cryptocurrency Prices)
- Live BTC & ETH prices
- Multi-currency support
- Numeric assertions (> 0 price)
- Performance checks
- Edge-case handling for invalid coins

### NASA Images API (Mars Rover Search)
- Public NASA Images API
- Large JSON response validation
- Pagination handling
- Manual schema-style assertions
- Negative tests for no-result scenarios

---

## Tech Stack

- Postman
- Newman (CLI)
- Node.js
- JavaScript (Postman test scripts)
- JSON

---

## Project Structure

irl-api-testing/
│
├── Real-World APIs – Weather Crypto Space.postman_collection.json
├── realworld-apis-env.newman.json
├── newman-report.html
└── README.md


---

## Environment Configuration (IMPORTANT)

 **Postman v11+ does not export environment “current values” by default.**  
Because of this, exported environment files may contain empty values, which causes Newman runs to fail.

### Solution Used in This Project

A **separate Newman-ready environment file** is provided:

`realworld-apis-env.newman.json`

This file contains **explicit values** for:
- Base URLs
- Query parameters
- API keys (OpenWeather)

### Required Environment Variables

```json
openweather_base_url
openweather_api_key
city

coingecko_base_url
coin_ids
vs_currencies

nasa_images_base_url
nasa_query 
```
## Commands

- Install Newman
npm install -g newman newman-reporter-html
- Run the full test suite
newman run "Real-World APIs – Weather Crypto Space.postman_collection.json" \
-e "realworld-apis-env.newman.json" \
--reporters cli,html \
--reporter-html-export "newman-report.html"
  
## Test Coverage Summary

- OpenWeather

401 Unauthorized (missing / invalid key)
404 / 400 for invalid city
200 OK for valid city
Numeric validation on weather data
Response-time checks

- CoinGecko

Live crypto pricing
Multi-currency validation
Numeric assertions
Performance checks

- NASA Images

Search API validation
Pagination handling
Schema-like field validation
Empty result handling

## Why This Project Matters

This project demonstrates:
Real API testing against production systems
Authentication handling (API keys)
Defensive test scripting
Edge-case awareness
CI-ready execution using Newman
Professional Postman collection structure

## Author

Chriso Christudhas
QA Engineer | API Testing | Test Automation
GitHub: https://github.com/doki2212
