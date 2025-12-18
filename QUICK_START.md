# 🚀 Quick Start Guide - Library Management System

Get your Library Management System up and running in **5 minutes**!

---

## ⚡ Fast Track Setup

### 1️⃣ Prerequisites Check

```bash
# Check PostgreSQL installation
psql --version
# Expected: psql (PostgreSQL) 13.x or higher

# Check Git installation
git --version
```

✅ **Have both?** Continue to step 2  
❌ **Missing something?** Install from:
- PostgreSQL: https://www.postgresql.org/download/
- Git: https://git-scm.com/downloads

---

### 2️⃣ Clone & Navigate

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/Library-Management-System.git

# Navigate into the project
cd Library-Management-System
```

---

### 3️⃣ Create Database

```sql
-- Open PostgreSQL (psql or pgAdmin)
CREATE DATABASE library_project;

-- Verify creation
\l  -- Lists all databases, should see library_project
```

---

### 4️⃣ Run Schema

```bash
# Method 1: Using psql command line
psql -U postgres -d library_project -f database/schema.sql

# Method 2: Using pgAdmin
# 1. Open pgAdmin
# 2. Connect to your server
# 3. Right-click library_project → Query Tool
# 4. File → Open → Select database/schema.sql
# 5. Click Execute (⚡ icon)
```

---

### 5️⃣ Verify Setup

```sql
-- Check if all tables exist
SELECT table_name 
FROM information_schema.tables 
WHERE table_schema = 'public';

-- Expected output: books, members, employees, branch, issue_date, return_status
```

✅ **See all 6 tables?** You're ready to go!

---

## 🎯 Try Your First Query

```sql
-- Add your first book
INSERT INTO books(isbn, book_title, category, rental_price, status, author, publisher)
VALUES ('978-1-60129-456-2', 'To Kill a Mockingbird', 'Classic', 6.00, 'yes', 'Harper Lee', 'J.B. Lippincott & Co.');

-- View all books
SELECT * FROM books;
```

---

## 📊 Run Sample Queries

```sql
-- Find all available books
SELECT book_title, author, category
FROM books
WHERE status = 'yes'
ORDER BY book_title;

-- List all members
SELECT member_id, member_name, reg_date
FROM members
ORDER BY reg_date DESC;

-- Check branch information
SELECT * FROM branch;
```

---

## 🔧 Test Stored Procedures

```sql
-- Make sure a book is available
UPDATE books SET status = 'yes' WHERE isbn = '978-0-330-25864-8';

-- Issue a book (make sure member C101 and employee E104 exist)
CALL issue_book('IS1500', 'C101', '978-0-330-25864-8', 'E104');

-- Check the book status (should now be 'no')
SELECT isbn, book_title, status FROM books WHERE isbn = '978-0-330-25864-8';
```

---

## 📁 Project Structure Overview

```
Library-Management-System/
├── README.md                 ← Start here for full documentation
├── database/
│   ├── schema.sql           ← Database tables creation
│   └── queries.sql          ← All 19 project tasks
├── docs/
│   └── Project_Requirements.md  ← Detailed requirements
└── QUICK_START.md           ← You are here!
```

---

## 🎓 Learning Path

### Beginners (Start Here)
1. Read the [README.md](../README.md)
2. Review [Project_Requirements.md](docs/Project_Requirements.md)
3. Run Tasks 1-5 (Basic CRUD Operations)
4. Experiment with simple SELECT queries

### Intermediate
1. Complete Tasks 6-12 (Advanced Queries)
2. Study JOIN operations
3. Practice aggregation functions
4. Create your own analytical queries

### Advanced
1. Complete Tasks 13-19 (Complex Operations)
2. Study stored procedures
3. Implement triggers
4. Optimize query performance

---

## 💡 Common Issues & Solutions

### Issue: "psql: command not found"

**Solution**: Add PostgreSQL to your PATH
```bash
# Windows
set PATH=%PATH%;C:\Program Files\PostgreSQL\13\bin

# Mac/Linux
export PATH=/usr/local/pgsql/bin:$PATH
```

### Issue: "permission denied for database"

**Solution**: Use superuser or adjust permissions
```sql
-- Grant permissions
GRANT ALL PRIVILEGES ON DATABASE library_project TO your_username;
```

### Issue: "relation does not exist"

**Solution**: Make sure you're connected to the correct database
```sql
-- Check current database
SELECT current_database();

-- Connect to library_project
\c library_project
```

### Issue: "duplicate key value violates unique constraint"

**Solution**: Use different IDs or delete existing records
```sql
-- Check existing IDs
SELECT issued_id FROM issue_date ORDER BY issued_id DESC LIMIT 5;

-- Use next available ID
```

---

## 🤝 Need Help?

1. **Check the [README.md](../README.md)** - Most questions are answered there
2. **Review docs/** - Detailed documentation available
3. **Open an Issue** - If stuck, create a GitHub issue
4. **Ask the Community** - Use GitHub Discussions

---

## 🎯 Next Steps

After completing the setup:

1. ✅ **Complete all 19 tasks** in `database/queries.sql`
2. 📊 **Explore the analytics queries** in the README
3. 🔧 **Modify and extend** the system
4. 📝 **Document your additions**
5. 🌟 **Share your improvements** via Pull Requests

---

## 📚 Additional Resources

- [PostgreSQL Tutorial](https://www.postgresqltutorial.com/)
- [SQL Practice](https://www.sql-practice.com/)
- [pgAdmin Documentation](https://www.pgadmin.org/docs/)
- [Database Design Guide](https://www.guru99.com/database-design.html)

---

## ⏱️ Quick Reference Commands

```sql
-- Connect to database
\c library_project

-- List all tables
\dt

-- Describe table structure
\d books

-- Show all databases
\l

-- Quit psql
\q

-- Execute SQL file
\i path/to/file.sql

-- Show query execution time
\timing on
```

---

## ✅ Success Checklist

- [ ] PostgreSQL installed and running
- [ ] Repository cloned to local machine
- [ ] Database `library_project` created
- [ ] Schema executed successfully
- [ ] All 6 tables visible
- [ ] Sample query executed
- [ ] First book added
- [ ] Stored procedure tested

**All checked?** 🎉 **You're ready to master SQL!**

---

<div align="center">

**Questions?** Open an issue on GitHub!

**Ready to learn more?** Check out the [full README](../README.md)

</div>
