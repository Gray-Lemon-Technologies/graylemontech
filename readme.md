# 🍋 GrayLemonTech WordPress Project - Local Setup Instructions

This guide will help you set up the **GrayLemonTech WordPress project** on your local machines, regardless of the development environment used (**Laragon, XAMPP, MAMP, LocalWP, Docker**).

---

## ✅ Installed Versions (Reference & Recommendation)

To ensure consistency across the team, the following versions were used to develop and test this project locally:

| Component    | Installed Version (Used) | Recommended Minimum Version |
| ------------ | ------------------------ | --------------------------- |
| PHP          | 8.3.16                   | 8.0 or higher               |
| MySQL        | 8.4.3                    | 8.0 or higher               |
| Apache/Nginx | Apache 2.4+              | Any compatible version      |
| WordPress    | 6.x.x (latest stable)    | 6.0 or higher               |
| Composer     | Latest Stable (optional) | Latest Stable               |

📌 **Note:** Older versions such as **PHP 8.0** and **MySQL 8.0** should still work without major issues for this project. However, aligning with the versions above is recommended for compatibility and feature parity.

📜 Check the official WordPress server requirements and PHP/MySQL compatibility here:
[https://wordpress.org/about/requirements/](https://wordpress.org/about/requirements/)

---

## ✅ Installation Steps

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/graylemontech.git
cd graylemontech
```

### 2. Set Up the Web Root

* Place the project folder inside your web server's **document root**:

  * **Laragon:** `C:/laragon/www/`
  * **XAMPP:** `C:/xampp/htdocs/`
  * **MAMP:** `/Applications/MAMP/htdocs/`
  * **LocalWP/Docker:** Follow tool-specific instructions to map the project folder.

### 3. Install WordPress Core (Required for Ignored Files)

* Since the repository **ignores WordPress core files** (`wp-admin/`, `wp-includes/`) to avoid bloating, you need to:

  1. Download WordPress from [https://wordpress.org/download/](https://wordpress.org/download/)
  2. Extract and copy **everything except `wp-content`** into your project folder.
  3. Keep the repository's `wp-content` folder intact.

### 4. Create and Configure the Database

* Create a new **MySQL database** (example: `graylemontech_db`).
* Use **phpMyAdmin**, **Adminer**, or **MySQL CLI**.

### 5. Configure WordPress

* Duplicate `wp-config-sample.php` and rename it to `wp-config.php`.
* Update:

```php
define( 'DB_NAME', 'graylemontech_db' );
define( 'DB_USER', 'your_mysql_username' );
define( 'DB_PASSWORD', 'your_mysql_password' );
define( 'DB_HOST', 'localhost' );
```

### 6. Import the Database (If Provided)

*  `.sql` file will be provided by your backend developer, import it into your database:

```bash
mysql -u your_mysql_username -p graylemontech_db < graylemontech.sql
```

### 7. Access the WordPress Site

* Open your browser:

  * **Laragon:** `http://graylemontech.test`
  * **XAMPP/MAMP:** `http://localhost/graylemontech`

---

## ✅ Troubleshooting Guide

| Issue                      | Solution                                                    |
| -------------------------- | ----------------------------------------------------------- |
| Database connection error  | Check credentials in `wp-config.php`.                       |
| White screen or PHP errors | Verify PHP version; enable WP\_DEBUG in `wp-config.php`.    |
| Broken images or links     | Update `siteurl` and `home` in database `wp_options`.       |
| Can't login to admin       | Verify database integrity or reset password via phpMyAdmin. |

---

## ✅ Keeping the Team Updated

* **Code Changes:** Commit and push custom theme/plugin files.
* **Content/Admin Changes:** Export database `.sql` file when necessary.
