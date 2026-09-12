# 🚀 QUICK START GUIDE

## ⏱️ 5 Minutes to Running Application

### Step 1: Install Dependencies (2 minutes)
```bash
# Create virtual environment
python -m venv venv

# Activate it
# On Windows:
venv\Scripts\activate
# On Mac/Linux:
source venv/bin/activate

# Install packages
pip install -r requirements.txt
```

### Step 2: Configure Environment (1 minute)
```bash
# Copy environment file
cp .env.example .env

# Edit .env and add your API key
# Get free API key from: https://www.cricapi.com/
CRICBUZZ_API_KEY=your_key_here
```

### Step 3: Initialize Database (1 minute)
```bash
# Creates tables automatically
python -c "from database.connection import db_connection; db_connection.create_tables()"
```

### Step 4: Run Application (1 minute)
```bash
streamlit run app/main.py
```

**That's it! 🎉** Application opens at `http://localhost:8501`

---

## 📱 What to Do First

1. **Home Page** - Overview and quick start buttons
2. **Live Matches** - View current cricket matches
3. **Top Players** - See best batsmen and bowlers
4. **Analytics** - Try running SQL queries
5. **CRUD** - Create test data
6. **Settings** - Check configuration

---

## 🐛 Troubleshooting

### "ModuleNotFoundError"
```bash
pip install -r requirements.txt
```

### "No module named 'streamlit'"
```bash
pip install streamlit==1.28.1
```

### Database error
```bash
# Delete old database and reinitialize
rm cricbuzz_data.db
python -c "from database.connection import db_connection; db_connection.create_tables()"
```

### API not working
- Get API key from: https://www.cricapi.com/
- Add to `.env` file as `CRICBUZZ_API_KEY=your_key`
- Check internet connection

---

## 📂 Important Files

| File | Purpose |
|------|---------|
| `app/main.py` | Application entry point |
| `app/config.py` | Configuration management |
| `.env` | API keys and settings |
| `requirements.txt` | Python dependencies |
| `database/models.py` | Database schema |
| `services/crud_service.py` | Data operations |
| `sql/queries/all_queries.sql` | 25 SQL queries |

---

## 💡 Key Features to Explore

✅ **Live Matches** - Real-time cricket data
✅ **Player Stats** - Top batsmen and bowlers
✅ **SQL Queries** - 25 advanced analytics queries
✅ **CRUD Operations** - Create/Read/Update/Delete data
✅ **Database** - SQLite (no setup needed)
✅ **Visualizations** - Charts and tables

---

## 🎓 Learning Path

1. Understand the **folder structure** (see README.md)
2. Explore **database schema** (database/models.py)
3. Try **CRUD operations** (services/crud_service.py)
4. Run **SQL queries** (sql/queries/all_queries.sql)
5. Customize **Streamlit pages** (pages/ folder)
6. Deploy to **cloud** (documentation/DEPLOYMENT.md)

---

## 📞 Need Help?

- Check `README.md` for full documentation
- See `documentation/` folder for guides
- Review `sql/queries/all_queries.sql` for query examples
- Check logs in `logs/app.log`

---

**Happy Cricket Analytics! 🏏**
