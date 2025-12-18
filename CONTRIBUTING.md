# Contributing to Library Management System

First off, thank you for considering contributing to the Library Management System! It's people like you that make this project better for everyone.

## 🤝 How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check the existing issues to avoid duplicates. When you create a bug report, include as many details as possible:

- **Use a clear and descriptive title**
- **Describe the exact steps to reproduce the problem**
- **Provide specific examples** (SQL queries, screenshots, error messages)
- **Describe the behavior you observed** and what you expected to see
- **Include your PostgreSQL version** and operating system

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion:

- **Use a clear and descriptive title**
- **Provide a detailed description** of the suggested enhancement
- **Explain why this enhancement would be useful**
- **List some examples** of how it would be used

### Pull Requests

1. **Fork the repository** and create your branch from `main`
2. **Make your changes** following our coding standards
3. **Test your changes** thoroughly
4. **Update documentation** if needed
5. **Write clear commit messages**
6. **Submit a pull request**

## 📝 Coding Standards

### SQL Style Guide

#### Naming Conventions

```sql
-- Tables: lowercase with underscores
CREATE TABLE book_categories;

-- Columns: lowercase with underscores
member_id, issued_date, book_title

-- Stored Procedures: verb_noun format
issue_book, add_return_records

-- Views: descriptive names with _view suffix
active_members_view
```

#### Formatting

```sql
-- Use uppercase for SQL keywords
SELECT, FROM, WHERE, JOIN

-- Indent subqueries
SELECT *
FROM (
    SELECT column1
    FROM table1
    WHERE condition
) AS subquery;

-- Align JOIN conditions
SELECT 
    t1.column1,
    t2.column2
FROM table1 t1
JOIN table2 t2 ON t1.id = t2.id
LEFT JOIN table3 t3 ON t2.id = t3.id;
```

#### Comments

```sql
-- Single-line comment for brief explanations

/*
 * Multi-line comment for:
 * - Complex query explanations
 * - Stored procedure documentation
 * - Important notes
 */

-- Example:
/*
 * Calculate overdue fines for members
 * Fine rate: $0.50 per day
 * Grace period: 30 days
 */
SELECT 
    member_id,
    (CURRENT_DATE - issued_date - 30) * 0.50 AS fine
FROM issue_date
WHERE CURRENT_DATE - issued_date > 30;
```

### Documentation Standards

- Update README.md if you add new features
- Add inline comments for complex logic
- Document stored procedures with parameter descriptions
- Include usage examples for new queries

## 🧪 Testing Guidelines

Before submitting a pull request:

1. **Test all queries** against a test database
2. **Verify foreign key constraints** are maintained
3. **Check for SQL injection vulnerabilities** in dynamic queries
4. **Ensure backward compatibility** with existing data
5. **Test edge cases** (NULL values, empty results, etc.)

### Example Test Cases

```sql
-- Test Case 1: Issue book to valid member
CALL issue_book('IS_TEST_001', 'C101', '978-0-330-25864-8', 'E104');
-- Expected: SUCCESS

-- Test Case 2: Issue unavailable book
CALL issue_book('IS_TEST_002', 'C101', '978-0-330-25864-8', 'E104');
-- Expected: ERROR - Book unavailable

-- Test Case 3: Issue non-existent book
CALL issue_book('IS_TEST_003', 'C101', '978-9-999-99999-9', 'E104');
-- Expected: ERROR - Book not found
```

## 📋 Commit Message Guidelines

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- **feat**: A new feature
- **fix**: A bug fix
- **docs**: Documentation only changes
- **style**: Formatting, missing semicolons, etc.
- **refactor**: Code change that neither fixes a bug nor adds a feature
- **test**: Adding missing tests
- **chore**: Maintain tasks, package updates, etc.

### Examples

```bash
feat(queries): add revenue analysis query

Added query to calculate revenue by branch and category.
Includes filtering by date range and sorting options.

Closes #123

---

fix(procedures): handle null book quality in return

Modified add_return_records to handle NULL book_quality values.
Now defaults to 'Unknown' if quality not specified.

Fixes #456

---

docs(readme): update installation instructions

Added troubleshooting section for common PostgreSQL issues.
Improved clarity of setup steps.
```

## 🏷️ Pull Request Process

1. **Update the README.md** with details of changes if applicable
2. **Update the version number** in relevant files (if versioning is implemented)
3. **Ensure all tests pass** and documentation is updated
4. **Request review** from maintainers
5. **Address feedback** promptly and professionally

### PR Checklist

- [ ] Code follows the style guidelines
- [ ] Self-review of code performed
- [ ] Comments added for complex sections
- [ ] Documentation updated
- [ ] No new warnings generated
- [ ] Tests added for new features
- [ ] All tests passing
- [ ] Commit messages follow guidelines

## 💡 Contribution Ideas

### For Beginners

- Fix typos in documentation
- Improve code comments
- Add more examples to README
- Create test data scenarios
- Write tutorial blog posts

### Intermediate

- Optimize existing queries
- Add new analytical queries
- Improve error handling in procedures
- Create data validation scripts
- Add indexes for performance

### Advanced

- Implement advanced features (reservation system, fines, etc.)
- Create database migration scripts
- Develop API endpoints
- Build web dashboard
- Add comprehensive test suite

## 📚 Resources

- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [SQL Style Guide](https://www.sqlstyle.guide/)
- [GitHub Flow](https://guides.github.com/introduction/flow/)
- [Writing Good Commit Messages](https://chris.beams.io/posts/git-commit/)

## ❓ Questions?

Feel free to:
- Open an issue with the `question` label
- Reach out to maintainers directly
- Join community discussions

## 📜 Code of Conduct

### Our Pledge

We pledge to make participation in our project a harassment-free experience for everyone, regardless of age, body size, disability, ethnicity, gender identity and expression, level of experience, nationality, personal appearance, race, religion, or sexual identity and orientation.

### Our Standards

**Positive behavior includes:**
- Using welcoming and inclusive language
- Being respectful of differing viewpoints
- Gracefully accepting constructive criticism
- Focusing on what is best for the community

**Unacceptable behavior includes:**
- Trolling, insulting/derogatory comments
- Public or private harassment
- Publishing others' private information
- Other conduct which could reasonably be considered inappropriate

### Enforcement

Instances of abusive, harassing, or otherwise unacceptable behavior may be reported by contacting the project team. All complaints will be reviewed and investigated promptly and fairly.

---

## 🎉 Recognition

Contributors will be recognized in the README.md file and release notes.

Thank you for contributing! 🙏

---

**Questions about contributing?** Open an issue with the `question` label!
