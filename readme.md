# 🚀 GrayLemonTech WordPress Project - Local Setup Instructions

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

👉 **Note:** Older versions such as **PHP 8.0** and **MySQL 8.0** should still work without major issues for this project. However, aligning with the versions above is recommended for compatibility and feature parity.

📌 Check the official WordPress server requirements and PHP/MySQL compatibility here:
[https://wordpress.org/about/requirements/](https://wordpress.org/about/requirements/](https://make.wordpress.org/hosting/handbook/compatibility/))

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

### 3. Create and Configure the Database

* Create a new **MySQL database** (example: `graylemontech_db or just graylemontech`).
* Use **phpMyAdmin**, **Adminer**, or **command-line MySQL**.

### 4. Configure WordPress

* Duplicate `wp-config-sample.php` → rename to `wp-config.php`.
* Update these lines in `wp-config.php`:

```php
define( 'DB_NAME', 'graylemontech_db' );
define( 'DB_USER', 'your_mysql_username' );
define( 'DB_PASSWORD', 'your_mysql_password' );
define( 'DB_HOST', 'localhost' );
```

### 5. Import the Database (If Provided)

* If an exported database `.sql` file is provided (example: `graylemontech.sql`), import it into your new database via **phpMyAdmin** or command-line:

```bash
mysql -u your_mysql_username -p graylemontech_db < graylemontech.sql
```

### 6. Access the WordPress Site

* Open your browser:

  * **Laragon:** `http://graylemontech.test`
  * **XAMPP/MAMP:** `http://localhost/graylemontech`
  * **LocalWP/Docker:** Check the assigned local domain.

---

## ✅ Connecting to the Git Repository

* All **custom theme and plugin code** should be committed to the **GitHub repository**.

* Typical files to commit:

  * Custom themes: `/wp-content/themes/your-theme/`
  * Custom plugins: `/wp-content/plugins/your-plugin/`

* Do **not** commit:

  * WordPress core files (`wp-admin`, `wp-includes`)
  * Media uploads (`wp-content/uploads`)
  * `wp-config.php` (if sensitive)
  * Database files (`.sql`)

### Git Workflow:

1. Make code changes (themes/plugins).
2. Stage changes:

```bash
git add .
```

3. Commit:

```bash
git commit -m "Describe your changes here"
```

4. Push:

```bash
git push origin main
```

---

## ✅ Troubleshooting Guide

| Issue                      | Solution                                                           |
| -------------------------- | ------------------------------------------------------------------ |
| Database connection error  | Check credentials in `wp-config.php`.                              |
| White screen or PHP errors | Verify PHP version; enable debug in `wp-config.php`.               |
| Broken images or links     | Check WordPress Address & Site Address in database (`wp_options`). |
| Can't login to admin       | Confirm database integrity or reset password via MySQL.            |

---

## ✅ Keeping the Team Updated

* **Code Changes:** Push to GitHub → teammates pull updates.
* **Content/Admin Changes:** Export database (`.sql`) if necessary → share via GitHub, Drive, or other tools.

---

For any setup issues or assistance, please contact the project maintainer or team lead.
