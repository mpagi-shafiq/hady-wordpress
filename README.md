# Hady Snacks: WordPress + WooCommerce with a Custom Order Tracker

BIT 2103 Internet Technologies & Advanced Website Development: end-of-semester exam project.
Mountains of the Moon University, Faculty of Science, Technology & Innovations.

## About the client
Hady Snacks is a small snack supply business in Kampala. It supplies local shops daily and takes phone orders from customers further away. It had no website. Customers pay in different ways: before, on delivery, or on credit.

**Live site:** https://[your-domain] (added after deployment)

## Stack
| Layer | Choice |
|---|---|
| CMS | WordPress |
| Shop | WooCommerce (payments in test mode) |
| Page builder | Elementor (free) |
| Customisation | Child theme (`hady-child`) |
| Custom module | Plugin `hady-order-tracker` (PHP, MySQL, PDO prepared statements) |
| Local development | WAMP (PHP, MySQL) |
| Hosting | cPanel, with SSL and business email |

## Why this stack
The client's staff are not technical, so WordPress gives an admin they can manage without code. WooCommerce covers the public shop. Tracking shop customers, credit and payments needs a database design of its own, so that is built as a custom plugin.

## What this repository contains
This repository holds only the custom code, not WordPress core.

```
wp-content/
  themes/hady-child/            Child theme: branding, templates, light PHP/CSS/JS
  plugins/hady-order-tracker/   Custom module: customers, products, orders, payments
docs/                           Client brief, proposal, quotation, security report
README.md
```

## Custom module: Order Tracker
Admin-only module with full CRUD and JOINs, using prepared statements throughout.

Tables: `customers`, `products`, `orders`, `order_items`, `payments`.

Features:
- Customers have a payment term: prepaid, on delivery, or credit
- Orders carry a status (received, preparing, delivered) and a payment status (unpaid, partly paid, paid)
- Multiple payments can be recorded against one order
- Dashboard shows balances owed, overdue credit and low stock

## Running locally
1. Install WAMP and create a database.
2. Install WordPress and activate the `hady-child` theme.
3. Copy `hady-order-tracker` into `wp-content/plugins/` and activate it.
4. Import any sample data supplied in `docs/` (sample data only, no real customer records).

## Security notes
- No credentials or `wp-config.php` are committed.
- The live site uses HTTPS, login attempt limits, and file editing disabled.
- Real customer data is never stored in this repository.

## Author
[Your full name], Reg No [your reg no], BIT 2103.
