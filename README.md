# -Library-Management-System-Database
# 📚 Library Management System

A comprehensive Library Management System built with Microsoft Access to efficiently manage books, authors, members, staff, and loan transactions. This project demonstrates relational database design principles with full normalization up to Third Normal Form (3NF).



---

## 🎯 Overview

This system provides a complete solution for library operations including:
- Book inventory management
- Member registration and tracking
- Loan processing and return handling
- Overdue book monitoring
- Staff management

---

## ✨ Features

- **Book Management** - Add, update, and track books with author and category information
- **Member Management** - Register members and maintain their contact details
- **Loan Processing** - Track book loans, due dates, and returns
- **Staff Tracking** - Manage library staff roles and responsibilities
- **Overdue Reports** - Identify overdue books and notify members
- **Data Entry Forms** - User-friendly forms for easy data input
- **Complex Queries** - Pre-built queries for comprehensive data analysis
- **Reports** - Generate detailed reports for library operations

---

## 🗄️ Database Schema

The database consists of 6 normalized tables:

| Table | Description |
|-------|-------------|
| **Authors** | Stores author information (AuthorID, FirstName, LastName) |
| **Categories** | Book categories/genres (CategoryID, CategoryName) |
| **Books** | Book inventory with foreign keys to Authors and Categories |
| **Members** | Library member registration and contact info |
| **Staff** | Library staff details and roles |
| **Loans** | Loan transactions linking Members, Books, and Staff |

### Entity Relationships

```
Authors ──────< Books >────── Categories
                  │
                  │
Members ──────< Loans >────── Staff
```

### Normalized Relations (3NF)

```
Authors(AuthorID, FirstName, LastName)
Categories(CategoryID, CategoryName)
Books(BookID, Title, AuthorID, CategoryID, YearPublished, ISBN)
Members(MemberID, FirstName, LastName, Email, Phone, JoinDate)
Staff(StaffID, FirstName, LastName, Role, Email)
Loans(LoanID, MemberID, BookID, StaffID, LoanDate, DueDate, ReturnDate)
```

---

## 🛠️ Technologies Used

- **Microsoft Access** - Database management system
- **SQL** - Query language for data manipulation
- **ERD Tools** - Entity Relationship Diagram design

---

## 📁 Project Structure

```
Library-Management-System/
│
├── Library_Management_System.accdb    # Main Access database file
├── Library_Management_System_Final_Report.docx    # Project documentation
├── Library_Management_System_Presentation.pptx    # Project presentation
├── ERD.png                            # Entity Relationship Diagram
├── demo.mp4                           # System demo video
└── README.md                          # This file
```

---

## 🚀 Getting Started

### Prerequisites

- Microsoft Access 2016 or later (or Microsoft 365)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/Library-Management-System.git
   ```

2. Open `Library_Management_System.accdb` with Microsoft Access

3. Enable content if prompted by Access security settings

### Usage

1. **Adding Books** - Navigate to the Books form to add new books to the inventory
2. **Registering Members** - Use the Members form to register new library members
3. **Processing Loans** - Create loan records when members borrow books
4. **Recording Returns** - Update the ReturnDate field when books are returned
5. **Viewing Reports** - Run pre-built queries and reports for analysis

---

## 📊 Sample Queries

### Find Overdue Books
```sql
SELECT Members.FirstName, Members.LastName, Books.Title, Loans.DueDate
FROM (Loans 
INNER JOIN Members ON Loans.MemberID = Members.MemberID)
INNER JOIN Books ON Loans.BookID = Books.BookID
WHERE Loans.ReturnDate IS NULL AND Loans.DueDate < Date();
```

### Books by Category
```sql
SELECT Categories.CategoryName, COUNT(Books.BookID) AS TotalBooks
FROM Categories 
LEFT JOIN Books ON Categories.CategoryID = Books.CategoryID
GROUP BY Categories.CategoryName;
```

### Active Loans Report
```sql
SELECT Members.FirstName & " " & Members.LastName AS MemberName,
       Books.Title, Loans.LoanDate, Loans.DueDate,
       Staff.FirstName & " " & Staff.LastName AS ProcessedBy
FROM ((Loans 
INNER JOIN Members ON Loans.MemberID = Members.MemberID)
INNER JOIN Books ON Loans.BookID = Books.BookID)
INNER JOIN Staff ON Loans.StaffID = Staff.StaffID
WHERE Loans.ReturnDate IS NULL;
```

---



---

## 📈 Future Enhancements

- [ ] Web-based interface using HTML/CSS/JavaScript
- [ ] Email notifications for overdue books
- [ ] Barcode scanning integration
- [ ] Online book reservation system
- [ ] Mobile application

---

## 👨‍💻 Author

**Saim** - *Data Science & Analytics Graduate Student*

- GitHub: [@yourusername](https://github.com/mahmuds02)
- LinkedIn: (www.linkedin.com/in/saimmahmude)

---


---

## 🙏 Acknowledgments

- Buffalo State University
- CIS Department Faculty
- Database Design Course Materials

---

⭐ If you found this project helpful, please give it a star!
