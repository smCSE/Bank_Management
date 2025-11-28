# 🏦 Bank Management System

![PHP](https://img.shields.io/badge/PHP-7.4%2B-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-00000f?style=for-the-badge&logo=mysql&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

A robust web-based application for managing bank accounts, handling transactions, and administering user data. Built using **PHP** and **MySQL**, this system features secure authentication, role-based access control (Admin vs. Customer), and dynamic account management.

---

## 📋 Table of Contents

- [Features](#-features)
- [Technology Stack](#-technology-stack)
- [Prerequisites](#-prerequisites)
- [Installation & Setup](#-installation--setup)
- [Database Configuration](#-database-configuration)
- [Usage Guide](#-usage-guide)
- [Project Structure](#-project-structure)
- [Future Improvements](#-future-improvements)

---

## ✨ Features

### 🔐 Authentication & Security
- **Secure Login/Registration:** Users can register and login securely.
- **Password Hashing:** Passwords are encrypted using `password_hash()` for security.
- **Role-Based Access Control (RBAC):** Distinct functionality for **Admins** and **Customers**.
- **Session Management:** Protected pages redirect unauthorized users to the login screen.

### 👤 Admin Capabilities
- **Create Accounts:** Create new bank accounts with initial balance, contact info, and address.
- **View All Accounts:** specific dashboard to view all registered bank accounts in a table format.
- **Edit/Delete Accounts:** Full CRUD (Create, Read, Update, Delete) capabilities.
- **Add Money:** Exclusive ability to deposit funds into user accounts.
- **Search:** Filter accounts by Name, Email, or Phone number.

### 🏦 Customer Capabilities
- **View Accounts:** Access to account lists.
- **Withdraw Money:** Capability to withdraw funds with validation (checks for sufficient balance).
- **Edit Profile:** Update personal account details.

---

## 🛠 Technology Stack

- **Backend:** Native PHP
- **Database:** MySQL
- **Frontend:** HTML5, CSS3 (Custom styling, Responsive design)
- **Server:** Apache (via XAMPP/WAMP/MAMP)

---

## ⚙️ Prerequisites

Before running this project, ensure you have the following installed:
* [XAMPP](https://www.apachefriends.org/index.html) (or WAMP/MAMP) for a local server and MySQL database.
* A Web Browser (Chrome, Firefox, Edge).

---

## 🚀 Installation & Setup

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/yourusername/bank-management-system.git](https://github.com/yourusername/bank-management-system.git)
    ```
    *Or download the ZIP file and extract it.*

2.  **Move to Server Directory**
    * Copy the project folder to your local server directory.
    * **XAMPP:** `C:\xampp\htdocs\bank_management`
    * **WAMP:** `C:\wamp64\www\bank_management`

3.  **Start Services**
    * Open your XAMPP/WAMP Control Panel.
    * Start **Apache** and **MySQL**.

4.  **Import Database**
    * (See the [Database Configuration](#-database-configuration) section below to set up the SQL).

5.  **Configure Connection**
    * Open `connect.php` and ensure the credentials match your local setup (default is usually User: `root`, Password: ``).

6.  **Run the Application**
    * Open your browser and navigate to:
        `http://localhost/bank_management/auth.php`

---

## 🗄 Database Configuration

1.  Go to `http://localhost/phpmyadmin`.
2.  Create a new database named **`bank_management`**.
3.  Click on the SQL tab and execute the following SQL commands to create the necessary tables:

```sql
-- Create Users Table (For Login)
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('admin', 'customer') DEFAULT 'customer'
);

-- Create Accounts Table (For Bank Data)
CREATE TABLE accounts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(20) NOT NULL,
    address TEXT NOT NULL,
    balance DECIMAL(10, 2) DEFAULT 0.00,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
