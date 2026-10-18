ExpenseWise — Personal Expense Tracker
ExpenseWise is a responsive personal finance dashboard built with PHP, MySQL, HTML, CSS, and vanilla JavaScript. It helps users record income and expenses, review monthly cash flow, and understand spending by category.
This project complements a task-management app by focusing on financial records, date-based aggregation, category reporting, and data visualization.
Features
- Record income and expenses with title, amount, category, date, payment method, and notes
- Edit and delete transactions
- Monthly dashboard with income, expenses, net balance, and transaction totals
- Spending breakdown by category using a doughnut chart
- Monthly reports for income sources and expense categories
- Search and filter transaction history by month and type
- Server-side input validation and positive amount checks
- PDO prepared statements, output escaping, and CSRF protection
- Responsive desktop and mobile layout
Technology
- PHP 8.1+
- MySQL 8+ or compatible MariaDB
- PDO MySQL extension
- HTML5, CSS3, vanilla JavaScript
- Chart.js (loaded from a public CDN)
- XAMPP for local development
Run locally with XAMPP
1. Install XAMPP and start Apache and MySQL.
2. Place the expensewise folder inside XAMPP's htdocs directory.
3. Open http://localhost/phpmyadmin.
4. Import database/schema.sql.
5. Check config/database.php. Defaults are host 127.0.0.1, database expensewise, user root, and an empty password for a typical local XAMPP setup.
6. Open http://localhost/expensewise/ in your browser.
7. Add sample income and expenses to populate the dashboard and charts.
If your MySQL credentials differ, update local configuration or set EXPENSEWISE_DB_HOST, EXPENSEWISE_DB_NAME, EXPENSEWISE_DB_USER, and EXPENSEWISE_DB_PASS. Never commit real credentials.
Project structure
expensewise/
├── index.php                 # Monthly dashboard and category chart
├── create.php                # Create income or expense records
├── edit.php                  # Update a transaction
├── delete.php                # POST-only deletion with CSRF validation
├── transactions.php          # Searchable and filterable transaction list
├── reports.php               # Monthly category/source summaries
├── config/database.php       # PDO connection configuration
├── includes/
│   ├── bootstrap.php         # Shared helpers and CSRF functions
│   ├── header.php
│   ├── sidebar.php
│   └── footer.php
├── assets/css/style.css      # Responsive dashboard design
├── assets/js/app.js          # Category switching, chart and delete confirmation
├── database/schema.sql       # Database schema and indexes
├── .gitignore
├── LICENSE
└── README.md
Data model
All records are stored in a transactions table. The type field distinguishes income from expenses, while category supports grouped reports. DECIMAL(12,2) stores currency values without using floating-point storage in the database. Date, type/date, and category indexes support common queries.
Security and scope
- Server-side validation checks transaction fields.
- PDO prepared statements are used for SQL operations.
- Rendered user data is escaped with htmlspecialchars.
- Session-based CSRF tokens protect create, update, and delete actions.
- Delete requests use POST.
- This is a single-workspace portfolio demo without authentication or per-user ownership. Do not store sensitive real financial data or deploy publicly without adding authentication, authorization, HTTPS, secure production configuration, logging, and backups.
- Chart.js is loaded from a CDN, so the chart requires an internet connection.
Manual test checklist
- [ ] Add an income transaction.
- [ ] Add an expense with a category and date.
- [ ] Edit a transaction and verify dashboard totals update.
- [ ] Delete a transaction after confirming.
- [ ] Change the dashboard month.
- [ ] Search and filter transaction history.
- [ ] Compare report totals with transaction records.
- [ ] Test missing titles and invalid amounts.
- [ ] Test the layout on desktop and mobile.
- Screenshots
- <img width="1312" height="1199" alt="ExpenseWise Finance Dashboard Montage" src="https://github.com/user-attachments/assets/72d0585f-9104-4941-9993-42466a6a418b" />

Future improvements
- Authentication and separate user accounts
- Budgets and spending limits
- CSV export
- Automated tests and GitHub Actions
- Recurring transactions and configurable currencies
- Accessibility audit
Author
[Your Name] — BS Computer Science graduate, University of Wah, Pakistan.ing.
