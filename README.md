# 🏏 Cricbuzz LiveStats - Real-Time Cricket Insights & SQL-Based Analytics

A comprehensive cricket analytics platform that integrates live data from the Cricbuzz API with a SQL database to create an interactive web application.

## 🎯 Project Overview

**Cricbuzz LiveStats** is a full-stack cricket analytics dashboard built with Python and Streamlit that delivers:
- ⚡ Real-time match updates from Cricbuzz API
- 📊 Detailed player statistics and rankings
- 🔍 SQL-driven analytics with 25+ advanced queries
- 🛠️ Full CRUD operations for data management
- 💼 Business insights for sports media, fantasy cricket, and analytics firms
- 🎓 Educational platform for learning database operations

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Database Schema](#-database-schema)
- [SQL Queries](#-sql-queries)
- [API Integration](#-api-integration)
- [Deployment](#-deployment)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)

## ✨ Features

### 🌐 Live Match Updates
- Real-time cricket match data from Cricbuzz API
- Live scorecards and match status
- Team and player information
- Venue details

### 📈 Player Statistics
- Comprehensive player performance metrics
- Career statistics across different formats
- Top batsmen and bowlers rankings
- Player form analysis and trends

### 🔍 SQL Analytics (25 Queries)
- **Beginner Level (Q1-Q8)**: Basic queries on players, matches, venues
- **Intermediate Level (Q9-Q16)**: Complex joins, subqueries, partnerships analysis
- **Advanced Level (Q17-Q25)**: Window functions, time-series analysis, performance rankings

### 🛠️ CRUD Operations
- Create, Read, Update, Delete operations for:
  - Teams
  - Players
  - Venues
  - Matches
  - Statistics

### 💾 Database Integration
- Support for SQLite, MySQL, and PostgreSQL
- Optimized queries with proper indexing
- Data consistency and integrity
- Transaction support

### 📊 Interactive Visualizations
- Charts and graphs for data insights
- Top performers dashboard
- Venue capacity analysis
- Team performance comparison

## 🛠️ Tech Stack

### Backend
- **Python 3.8+** - Programming language
- **Streamlit** - Web application framework
- **SQLAlchemy** - ORM for database operations
- **Requests** - HTTP library for API calls
- **Pandas** - Data processing and analysis
- **Plotly/Matplotlib** - Data visualization

### Database
- **SQLite** - Default (lightweight, file-based)
- **MySQL** - Production option
- **PostgreSQL** - Enterprise option

### External APIs
- **Cricbuzz Cricket API** - Live cricket data source

### Development Tools
- **pytest** - Unit testing
- **black** - Code formatting
- **flake8** - Linting
- **python-dotenv** - Environment variable management

## 📥 Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Virtual environment (recommended)

### Step 1: Clone Repository
```bash
git clone <repository-url>
cd cricbuzz-analytics
```

### Step 2: Create Virtual Environment
```bash
# On Windows
python -m venv venv
venv\Scripts\activate

# On macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Setup Environment Variables
```bash
cp .env.example .env
# Edit .env and add your Cricbuzz API key
```

### Step 5: Initialize Database
```bash
python -c "from database.connection import db_connection; db_connection.create_tables()"
```

## ⚙️ Configuration

### Database Configuration

Edit `.env` file:

**SQLite (Default):**
```env
DB_TYPE=sqlite
SQLITE_DB_PATH=cricbuzz_data.db
```

**MySQL:**
```env
DB_TYPE=mysql
MYSQL_HOST=localhost
MYSQL_USER=root
MYSQL_PASSWORD=your_password
MYSQL_DATABASE=cricbuzz_db
MYSQL_PORT=3306
```

**PostgreSQL:**
```env
DB_TYPE=postgresql
POSTGRES_HOST=localhost
POSTGRES_USER=postgres
POSTGRES_PASSWORD=your_password
POSTGRES_DATABASE=cricbuzz_db
POSTGRES_PORT=5432
```

### API Configuration

Get your Cricbuzz API key from [cricapi.com](https://www.cricapi.com/):

```env
CRICBUZZ_API_KEY=your_api_key_here
```

### Application Configuration

```env
ENVIRONMENT=development
DEBUG=True
LOG_LEVEL=INFO
```

## 🚀 Usage

### Running the Application

```bash
streamlit run app/main.py
```

The application will open in your default browser at `http://localhost:8501`

### Navigation

1. **🏠 Home** - Project overview and quick start
2. **🔴 Live Matches** - Currently ongoing matches
3. **⭐ Top Players** - Best batsmen and bowlers
4. **📊 Analytics** - 25 SQL queries with results
5. **🛠️ CRUD Operations** - Create, Read, Update, Delete data
6. **⚙️ Settings** - Application configuration and info

## 📁 Project Structure

```
cricbuzz-analytics/
│
├── README.md                      # Project documentation
├── requirements.txt               # Python dependencies
├── .env.example                   # Environment variables template
├── .gitignore                     # Git ignore file
│
├── app/
│   ├── main.py                    # Streamlit entry point
│   ├── config.py                  # Configuration management
│   └── __init__.py
│
├── pages/                         # Additional Streamlit pages
│   ├── 1_home.py
│   ├── 2_live_matches.py
│   ├── 3_top_players.py
│   ├── 4_analytics.py
│   ├── 5_crud.py
│   └── 6_settings.py
│
├── database/
│   ├── connection.py              # Database connection handler
│   ├── models.py                  # SQLAlchemy models
│   └── migrations/
│       └── schema.sql             # SQL schema creation
│
├── api/
│   ├── cricbuzz_client.py         # Cricbuzz API wrapper
│   └── endpoints.py               # API endpoint definitions
│
├── services/
│   ├── data_fetcher.py            # Fetch data from API
│   ├── data_processor.py          # Process & transform data
│   ├── crud_service.py            # CRUD operations
│   └── analytics_service.py       # SQL analytics queries
│
├── utils/
│   ├── helpers.py                 # Utility functions
│   ├── validators.py              # Data validation
│   ├── logger.py                  # Logging setup
│   ├── constants.py               # Constants & enums
│   └── decorators.py              # Custom decorators
│
├── sql/
│   ├── queries/
│   │   ├── easy_queries.sql       # Questions 1-8
│   │   ├── medium_queries.sql     # Questions 9-16
│   │   └── hard_queries.sql       # Questions 17-25
│   └── sample_data.sql            # Sample data insert scripts
│
├── tests/
│   ├── test_api.py                # API integration tests
│   ├── test_database.py           # Database tests
│   ├── test_services.py           # Service tests
│   └── test_crud.py               # CRUD operation tests
│
├── documentation/
│   ├── API_SETUP.md               # API configuration guide
│   ├── DATABASE_SETUP.md          # Database setup guide
│   ├── ARCHITECTURE.md            # System architecture
│   ├── SQL_QUERIES.md             # SQL query documentation
│   └── DEPLOYMENT.md              # Deployment guide
│
├── assets/
│   ├── images/                    # Screenshots and logos
│   └── data/                      # Sample datasets
│
└── logs/
    └── app.log                    # Application logs
```

## 🗄️ Database Schema

### Entities

1. **Teams** - Cricket teams information
2. **Players** - Player details and roles
3. **Venues** - Cricket stadium information
4. **Matches** - Match details and results
5. **Innings** - Individual innings records
6. **PlayerStatistics** - Career statistics by format
7. **Series** - Cricket series information

### Relationships

```
Teams ──┬──→ Players
        ├──→ Matches (as team1, team2, winner)
        └──→ Venues
        
Players ──→ PlayerStatistics (career stats)
        └──→ Innings (match performances)

Matches ──→ Innings (batting/bowling details)
        └──→ Venues (match location)

Series ──→ Matches (series composition)
```

### Sample Table Creation

```sql
CREATE TABLE teams (
    team_id INT PRIMARY KEY AUTO_INCREMENT,
    team_name VARCHAR(100) UNIQUE NOT NULL,
    country VARCHAR(100),
    established_year INT,
    logo_url VARCHAR(500)
);

CREATE TABLE players (
    player_id INT PRIMARY KEY AUTO_INCREMENT,
    player_name VARCHAR(150) NOT NULL,
    team_id INT,
    playing_role VARCHAR(50),
    batting_style VARCHAR(50),
    bowling_style VARCHAR(50),
    country VARCHAR(100),
    FOREIGN KEY (team_id) REFERENCES teams(team_id)
);

-- And more tables...
```

## 📊 SQL Queries

### Query Categories

#### Beginner Level (Q1-Q8)
Focus on basic SQL fundamentals:
- Q1: Filter players by country
- Q2: Recent matches filtering
- Q3: Top performers ranking
- Q4: Venue capacity analysis
- Q5: Team statistics aggregation
- Q6: Role-based counting
- Q7: Format-wise maximum values
- Q8: Date-based filtering

#### Intermediate Level (Q9-Q16)
Complex queries with multiple joins:
- Q9: Multi-condition filtering
- Q10: Detailed match information
- Q11: Format comparison analysis
- Q12: Home vs Away performance
- Q13: Partnership analysis
- Q14: Venue-specific performance
- Q15: Match-based filtering
- Q16: Time-series analysis

#### Advanced Level (Q17-Q25)
Expert-level analytical queries:
- Q17: Toss advantage calculation
- Q18: Bowler efficiency metrics
- Q19: Performance consistency analysis
- Q20: Multi-format player analysis
- Q21: Comprehensive ranking system
- Q22: Head-to-head comparison
- Q23: Recent form assessment
- Q24: Partnership success metrics
- Q25: Career trajectory analysis

## 🌐 API Integration

### Cricbuzz API Endpoints

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/currentMatches` | GET | Fetch live/ongoing matches |
| `/matches` | GET | Get match information |
| `/players` | GET | Retrieve players list |
| `/playerStats` | GET | Get player statistics |
| `/series` | GET | Fetch cricket series |

### API Response Handling

```python
from api.cricbuzz_client import cricbuzz_client

# Get live matches
matches = cricbuzz_client.get_current_matches()

# Get player stats
stats = cricbuzz_client.get_player_stats(player_id='123')
```

### Error Handling

The application includes:
- Automatic retry logic (3 attempts)
- Rate limit handling
- Timeout management
- Mock data fallback for offline testing

## 🚀 Deployment

### Streamlit Community Cloud

1. Push code to GitHub
2. Go to [share.streamlit.io](https://share.streamlit.io)
3. Connect GitHub repository
4. Select `app/main.py` as entry point
5. Configure environment variables
6. Deploy!

### Docker Deployment

```dockerfile
FROM python:3.9-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 8501

CMD ["streamlit", "run", "app/main.py"]
```

### Cloud Platforms

- **Streamlit Cloud** - Easiest, free tier available
- **Heroku** - Traditional Python hosting
- **AWS EC2** - Full control and scalability
- **Google Cloud Platform** - Enterprise solution
- **Azure** - Microsoft cloud integration

See `documentation/DEPLOYMENT.md` for detailed instructions.

## 🔧 Troubleshooting

### Database Connection Issues

```python
# Test database connection
from database.connection import db_connection

try:
    db_connection.create_tables()
    print("✅ Database connected successfully!")
except Exception as e:
    print(f"❌ Connection error: {e}")
```

### API Key Not Working

1. Verify API key is set in `.env`
2. Check API key validity at [cricapi.com](https://www.cricapi.com/)
3. Review API rate limits and usage
4. Check internet connection

### Streamlit Cache Issues

```bash
# Clear Streamlit cache
streamlit cache clear
```

### Missing Dependencies

```bash
# Reinstall dependencies
pip install -r requirements.txt --force-reinstall
```

## 📝 Common Issues

| Issue | Solution |
|-------|----------|
| "ModuleNotFoundError" | Install dependencies: `pip install -r requirements.txt` |
| Database connection fails | Check `.env` database configuration |
| API returns empty data | Verify API key is valid and has remaining quota |
| Streamlit page doesn't load | Clear cache: `streamlit cache clear` |
| Permission denied on logs | Check folder permissions: `chmod 755 logs/` |

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📚 Learning Resources

### SQL Concepts Covered
- Basic SELECT, WHERE, GROUP BY, ORDER BY
- JOINs (INNER, LEFT, RIGHT, FULL)
- Subqueries and CTEs (Common Table Expressions)
- Window Functions (ROW_NUMBER, RANK, LAG, LEAD)
- Aggregate Functions (COUNT, SUM, AVG, STDDEV)
- String and Date Functions

### Python Concepts Covered
- Object-Oriented Programming (OOP)
- Design Patterns (Singleton, Service Layer)
- Error Handling and Logging
- API Integration and HTTP Requests
- Database ORM with SQLAlchemy
- Web Development with Streamlit

### Streamlit Components Covered
- Page routing and navigation
- Form handling and input widgets
- Data visualization (charts, tables)
- Session state management
- Caching and performance optimization

## 📞 Support

- **Documentation**: See `/documentation` folder
- **Issues**: Create an issue on GitHub
- **Email**: support@cricbuzz-livestats.com

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Cricbuzz for the cricket API
- Streamlit for the amazing web framework
- SQLAlchemy for the ORM
- All contributors and users

---

**Made with ❤️ for cricket enthusiasts and developers**

**Last Updated**: 2024
**Version**: 1.0.0
