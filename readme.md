# 🚀 GrayLemonTech WordPress Project - Local Setup Instructions

This guide will help you and your team set up the **GrayLemonTech WordPress project** on your local machines, regardless of the development environment used (**Laragon, XAMPP, MAMP, LocalWP, Docker**).

---

## ✅ Prerequisites

Please ensure the following are installed:

| Requirement         | Version (Recommended)  |
| ------------------- | ---------------------- |
| PHP                 | 8.3.16 or higher       |
| MySQL               | 8.4.3 or higher        |
| Apache/Nginx        | Any compatible server  |
| WordPress           | 6.x.x or latest stable |
| Composer (optional) | Latest stable          |

*Any local server stack (Laragon, XAMPP, MAMP, LocalWP, Docker) may be used, as long as compatible versions are maintained.*

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

* Create a new **MySQL database** (example: `graylemontech_db`).
* Use **phpMyAdmin**, **Adminer**, or **command-line MySQL**.
* Keep track of:

  * Database name
  * Database username & password

### 4. Configure WordPress

* Duplicate `wp-config-sample.php` → rename to `wp-config.php`.
* Update these lines in `wp-config.php`:

```php
define( 'DB_NAME', 'graylemontech_db' );
define( 'DB_USER', 'your_mysql_username' );
define( 'DB_PASSWORD', 'your_mysql_password' );
define( 'DB_HOST', 'localhost' );
```

* Optional: Generate and insert unique security salts from [https://api.wordpress.org/secret-key/1.1/salt/](https://api.wordpress.org/secret-key/1.1/salt/)

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

## ✅ Environment Notes & Version Consistency

| Component | Required Version |
| --------- | ---------------- |
| PHP       | 8.3.16+          |
| MySQL     | 8.4.3+           |
| WordPress | Latest Stable    |

* All teammates should align their environments to minimize compatibility issues.
* Use `.env` files or local server settings to manage sensitive credentials.

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
