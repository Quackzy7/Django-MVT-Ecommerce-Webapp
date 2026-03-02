# MyShop — Django MVT E-Commerce Web App

A fully functional marketplace built with Django, demonstrating core web framework concepts including MVT architecture, ORM, session-based cart, email authentication, Stripe payments, and custom middleware.

## Overview

MyShop is a dual-role e-commerce marketplace where **Buyers** can browse, search, and purchase products, and **Sellers** can manage their own product listings and incoming orders. Built as a Django lab project to demonstrate real-world application of the MVT pattern, Django ORM, sessions, middleware, and authentication.

---

## Architecture

MyShop follows Django's **MVT** pattern:

```
Browser Request
    ↓
Middleware Stack  (Logging → Security → Session → CSRF → Auth)
    ↓
URL Dispatcher   urls.py → matches path → calls View function
    ↓
View Function    queries Model via ORM → builds context dict
    ↓
Template Engine  renders HTML with context data
    ↓
Middleware Stack (reverse — adds security headers)
    ↓
HTTP Response → Browser
```

## Project Structure 

```
MyShop-DjangoWebapp/
│
├── manage.py
├── requirements.txt
├── .env.example
├── readme.md
│
├── ecommerce/                  # Core Django project config
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── accounts/                   # User auth & profiles
│   ├── models.py
│   ├── views.py
│   ├── forms.py
│   ├── backends.py
│   ├── urls.py
│   └── migrations/
│
├── store/                      # Product & category management
│   ├── models.py
│   ├── views.py
│   ├── forms.py
│   ├── admin.py
│   ├── urls.py
│   └── migrations/
│
├── cart/                       # Shopping cart
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   └── migrations/
│
├── orders/                     # Order processing & payments
│   ├── models.py
│   ├── views.py
│   ├── services.py
│   ├── urls.py
│   └── migrations/
│
├── theme/                      # Tailwind CSS theme
│   ├── static/css/dist/styles.css
│   └── static_src/src/styles.css
│
├── templates/                  # HTML templates
│   ├── base.html
│   ├── navbar.html
│   ├── footer.html
│   ├── accounts/  (login, signup)
│   ├── store/     (home, products, product_detail, seller_dashboard, etc.)
│   ├── cart/      (cart)
│   └── orders/    (checkout, order_detail, order_list, stripe_checkout, etc.)
│
└── static/
    ├── css/index.css
    └── images/logo.webp
```

### Prerequisites

- Python 3.11+
- pip
- A Stripe account (for payment testing)

### Installation

```bash
# 1. Clone the repository
git clone git@github.com:Quackzy7/MyShop-DjangoWebapp
cd MyShop-DjangoWebapp

# 2. Create and activate a virtual environment
python -m venv venv
Windows: venv\Scripts\activate #source venv/bin/activate   

# 3. Install dependencies
pip install -r requirements.txt

# 4. Apply database migrations
python manage.py makemigrations
python manage.py migrate

# 5. Create a superuser for the admin panel(optional)
python manage.py createsuperuser

# 6. Run the development server
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` in your browser.


### Resetting the Database

```bash
# Wipe all data but keep the schema 
python manage.py flush 
```



