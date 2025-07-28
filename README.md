# 🍰 Cake Shop Ecommerce Website

This is a full-featured Ecommerce Website for a Cake Shop built with Django, Django REST Framework, MySQL, HTML, CSS, and Bootstrap. It supports multiple user roles (Admin, Seller, Buyer), advanced product management, order flow, online/COD payments (Razorpay), review/rating moderation, coupons, PDF invoice generation, and much more.

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Setup & Installation](#setup--installation)
- [Usage Guide](#usage-guide)
- [Folder Structure](#folder-structure)
- [Roles & Functionalities](#roles--functionalities)
- [Security & Best Practices](#security--best-practices)
- [License](#license)

---

## Features

- Multiple user roles: **Admin, Seller, Buyer**
- **Category hierarchy** (e.g. "Birthday > Kids/Adults")
- **Product variants** (0.5kg / 1kg / 2kg), multi-image carousel
- **Persistent cart** per user (login required)
- **Order management:** Place, track, cancel (pre-shipping)
- **Online payment** (Razorpay) & **Cash on Delivery**
- **Coupon system** (global/product-specific, seller-specific, usage limits)
- **PDF invoice auto-generation** on payment
- **Email notifications:** registration, order status, review approval, etc.
- **Review/rating system** (buyers after delivery, admin-approved)
- **Admin dashboard:** Orders, sales, top sellers, statistics
- **Seller dashboard:** Product/revenue/order tracking, no inter-seller data leaks
- **Login/logout audit tracking**
- **Contact Us** form
- **100% responsive**—built with Bootstrap


---

## Tech Stack

- **Backend:** Python, Django, Django REST Framework (DRF)
- **Database:** MySQL
- **Frontend:** HTML, CSS, [Bootstrap 5](https://getbootstrap.com/)
- **Media & Images:** Django local media folder (S3-ready)
- **Payments:** Razorpay (test/live key ready, online), COD
- **PDF Generation:** ReportLab (lightweight)
- **Email:** SMTP (Gmail, or any SMTP provider)
- **OS:** Compatible with Windows or Linux

---

## Setup & Installation

**Requires:** Python 3.8+, MySQL, Git, pip

1. **Clone the repository**

    ```
    git clone <your-repository-url>
    cd cakeshop_ecommerce
    ```

2. **Setup virtual environment**

    ```
    python -m venv venv
    venv\Scripts\activate  # On Windows
    ```

3. **Install dependencies**

    ```
    pip install -r requirements.txt
    ```
    *(if `requirements.txt` not provided, see below for package list)*

4. **Configure environment variables**

    - Create a `.env` file in the root:

        ```
        SECRET_KEY=your-django-secret
        DEBUG=True
        DB_NAME=cakeshop_db
        DB_USER=root
        DB_PASSWORD=your_mysql_password
        DB_HOST=localhost
        DB_PORT=3306
        EMAIL_HOST_USER=your_email@gmail.com
        EMAIL_HOST_PASSWORD=your_app_password
        RAZORPAY_KEY_ID=your_razorpay_key_id
        RAZORPAY_KEY_SECRET=your_razorpay_key_secret
        ```

5. **Database setup**

    - Create a MySQL database named `cakeshop_db`
    - Ensure your MySQL user and password match those in your `.env`

6. **Run migrations**

    ```
    python manage.py makemigrations
    python manage.py migrate
    ```

7. **Create a superuser**

    ```
    python manage.py createsuperuser
    ```

8. **Collect static files**

    ```
    python manage.py collectstatic
    ```

9. **Start the application**

    ```
    python manage.py runserver
    ```

10. **Initial Data**

    - You can add initial users/cakes/categories via the Django admin panel (`/admin/`) or use the provided shell commands to populate data.

---

## Usage Guide

- **Homepage:** `/` or `/cakes/`
- **Admin panel:** `/admin/`
- **Login/Register:** `/accounts/login/`, `/accounts/register/`
- **Product browsing:** `/cakes/`, `/cakes/<cake_id>/`
- **Cart:** `/orders/cart/`
- **Checkout:** `/orders/checkout/`
- **Order tracking:** `/orders/orders/`, `/orders/orders/<order_id>/`
- **Invoice/PDF:** download after payment
- **Admin dashboard:** `/dashboard/admin-dashboard/`
- **Seller dashboard:** `/dashboard/seller-dashboard/`

See [previous conversation](#) for a full URL guide.

---

## Folder Structure
```
cakeshop_ecommerce/
│
├── cakeshop/ # Main settings, wsgi, urls, etc.
├── accounts/ # Custom user model, roles, authentication
├── products/ # Cakes, categories, images, variants
├── orders/ # Cart, order, coupon models and views
├── payments/ # Razorpay and COD logic, PDF/email utils
├── reviews/ # Review and rating system
├── dashboard/ # Admin and seller dashboard views
├── templates/
│ ├── base.html # Sitewide layout
│ ├── products/
│ ├── orders/
│ ├── ...
├── static/
│ ├── css/
│ │ └── custom.css
│ └── ...
├── media/ # Uploaded images, invoices
├── requirements.txt
└── .env
```


---

## User Roles & Capabilities

### Admin
- Approve sellers & reviews
- Manage categories, cakes, promos/coupons
- View all orders, revenue, and dashboard statistics
- Can download any invoice

### Seller
- Register and get approved manually
- Manage only their own cakes (add, edit, delete—if not ordered)
- Set delivery estimate per order
- Track their orders and revenue via dashboard

### Buyer
- Register/login to add to cart and order cakes
- Browse/search cakes
- Address management for shipping
- Payments: COD & Razorpay online
- Apply coupons
- Download invoice after payment
- Leave reviews after delivery (approval needed)
- Can cancel pre-shipping

---

## Security & Best Practices

- No Docker, Celery, Redis, or heavy/paid third-party dependencies
- Uses environment variables for all sensitive data
- ORM to guard against SQL injection
- All authentication and role-based actions secure by decorator checks
- File upload security (only images allowed for cakes)
- CSRF protection, XSS prevention with Django templating

---

## Requirements

- `django`
- `djangorestframework`
- `mysqlclient`
- `razorpay`
- `python-decouple`
- `reportlab`
- `pillow`
- `bootstrap5` (Django bootstrap loader, or just use static files)
- *(see your project's `requirements.txt` for the full list)*

---

## License

This project is for learning and demonstration only. Please check all third-party dependencies for their respective licenses before production/commercial use.

---

*Made with ❤️ using Django and Bootstrap.*


