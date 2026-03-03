# Filtered Data Access API

A FastAPI REST API that provides filtered access to large datasets (e.g., NSS/Statistical data) with dynamic query parameters.

---

## 🚀 Tech Stack

- **Backend Framework:** FastAPI  
- **Database:** SQL (SQLite/MySQL/PostgreSQL depending on setup)  
- **ORM:** SQLAlchemy  
- **Middleware:** CORS support

---

## 📌 Project Summary

This API allows clients to query and filter statistical data using multiple parameters such as state, sector, district, religion, social group, household size, panel, quarter, and visit. The filters are dynamically applied to database queries, enabling flexible access to records. The API returns a structured JSON response with results and metadata.

---

## 📂 Project Structure

```
/Filtered-Data-Access-API
│
├── database.py         # Database setup and session
├── main.py             # FastAPI application and route logic
├── frontend/           # (Optional) Frontend UI for testing
├── __pycache__/
├── requirements.txt    # Python dependencies
└── README.md
```

---

## 📡 API Endpoint

### ➤ Home

**GET** `/`

Returns a welcome message.

```json
{
  "message": "Welcome to the Statathon Project!"
}
```

---

### ➤ Filtered Data Query

**GET** `/api/filter`

**Query Parameters (all optional):**

| Parameter      | Description                             |
|----------------|-----------------------------------------|
| `state_name`   | Filter by state name                    |
| `sector`       | Filter by sector                        |
| `district_name`| Filter by district                      |
| `religion`     | Filter by religion                      |
| `social_group` | Filter by social group                  |
| `household_size` | Filter by household size              |
| `panel`        | Filter by panel                         |
| `quarter`      | Filter by quarter                       |
| `visit`        | Filter by visit                         |

Example request:

```
GET /api/filter?state_name=Karnataka&sector=Agriculture
```

Sample response:

```json
{
  "success": true,
  "count": 42,
  "filters_applied": {
    "state_name": "Karnataka",
    "sector": "Agriculture"
  },
  "data": [
    {
      "column1": "value1",
      "column2": "value2",
      ...
    }
  ]
}
```

---

## 🛠️ How It Works

- The API dynamically builds an SQL query based on provided query parameters.
- Filtering logic checks each parameter and appends conditions accordingly.
- Results are returned as JSON with:
  - status (success/failure),
  - count of records,
  - filters applied,
  - array of matching data.

---

## 📁 Database Setup

This project uses a database table defined in the `database.py` file. Make sure:

- You have a database file or instance ready
- Table names and field names match those in your dataset
- You install all dependencies

Example database setup:

```python
# in database.py
LocalSession, Base, engine, TABLE_NAME, STATE_TABLE_NAME
```

---

## ▶️ How to Run

1. Clone the repository
2. Install dependencies:

```
pip install -r requirements.txt
```

3. Start the server:

```
uvicorn main:app --reload
```

Application runs at:

```
http://localhost:8000
```

You can now query filtered endpoints using your browser or tools like Postman.

---

## 🧠 Learning Outcomes

- Built a flexible RESTful API with FastAPI  
- Dynamic SQL query formation based on user parameters  
- Integrated SQLAlchemy with database sessions  
- Implemented CORS for cross-origin support  
- Returned structured JSON with request metadata

---

## ⚙️ Future Improvements

- Add pagination support  
- Include authentication (e.g., API key / JWT)  
- Add data documentation or dataset schema  
- Provide frontend UI for instant queries  

---

## 👨‍💻 Author

Vinayak Vishwakarma  
Backend Developer | FastAPI | Python
