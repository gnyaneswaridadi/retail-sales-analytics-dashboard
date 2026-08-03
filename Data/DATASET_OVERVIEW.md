# 📋 Dataset Overview

`data/cleaned_retail_sales.csv` — the cleaned, feature-engineered dataset used throughout this project (produced by `notebooks/Retail_Sales_Performance.ipynb`).

## At a Glance

| | |
|---|---|
| **Rows** | 100,000 orders |
| **Columns** | 38 |
| **Date range** | January 1, 2019 – December 31, 2023 |
| **Geography** | 10 Indian states, 4 regions |
| **File size** | ~31 MB |

## Column Reference

### Customer Info
| Column | Type | Description |
|---|---|---|
| `customer_id` | text | Unique customer identifier |
| `customer_name`, `last_name` | text | Customer name |
| `date_of_birth` | date | Customer date of birth |
| `customer_age` | integer | Derived age at time of order |
| `is_valid_age` | boolean | Flags whether age passed validation (e.g., not under 18) |
| `age_group` | text | Binned age bracket: `<20`, `20-30`, `30-40`, `40-50`, `50-60`, `60+` |
| `segment` | text | `Consumer` or `Corporate` |

### Order Info
| Column | Type | Description |
|---|---|---|
| `order_id` | text | Unique order identifier |
| `order_date` | date | Date the order was placed |
| `sales_date`, `record_year` | date / int | Additional recorded date fields |
| `ship_date` | date | Date the order shipped |
| `ship_mode` | text | `Same Day`, `First Class`, `Second Class`, `Standard Class` |
| `shipping_days` | integer | Days between order and ship date |
| `quantity` | integer | Units ordered |

### Product Info
| Column | Type | Description |
|---|---|---|
| `product_id`, `product_name` | text | Product identifier and name |
| `category_of_goods` | text | One of 6 categories (see below) |
| `sub_category` | text | 24 sub-categories nested under the 6 categories |

### Financials
| Column | Type | Description |
|---|---|---|
| `sales` | float | Order revenue ($) |
| `profit` | float | Order profit ($) |
| `discount` | float | Discount applied (0.0–0.5) |
| `discount_band` | text | Binned discount: `0-10%`, `10-20%`, `20-30%`, `30-40%`, `40-50%` |
| `profit_margin_percent` | float | Profit as a % of sales |

### Geography & Outlet
| Column | Type | Description |
|---|---|---|
| `country`, `state`, `postal_code` | text / int | Location fields (all India) |
| `region` | text | `East`, `North`, `South`, `West` |
| `city_type` | text | `Tier 1`, `Tier 2`, `Village` |
| `outlet_type` | text | `Large`, `Medium`, `Small` |

### Time Helpers (derived)
| Column | Type | Description |
|---|---|---|
| `month`, `month_name` | int / text | Order month (numeric and name) |
| `order_year`, `order_month_year` | int / text | Order year and combined year-month |

### Customer Segmentation (RFM)
| Column | Type | Description |
|---|---|---|
| `recency_days` | integer | Days since the customer's order (recency) |
| `monetary` | float | Customer's monetary value (spend) |
| `customer_segment` | text | `Best Customers`, `Loyal / High Value`, `At Risk`, `Lost / Low Value` |

## Category Breakdown

**category_of_goods** (6): Dairy Products, Electric Appliances, Fast Food, Furniture, Household Items, Sessional Fruits & Vegetables

**state** (10): Delhi, Gujarat, Karnataka, Madhya Pradesh, Maharashtra, Punjab, Rajasthan, Tamil Nadu, Uttar Pradesh, West Bengal

## A Note on File Size

This file is ~31 MB, which is under GitHub's hard 100 MB limit but over the 25 MB limit for the browser's drag-and-drop upload button. Push it via `git add` / `git commit` / `git push` from the command line instead — see the main [README](README.md) for the exact steps.
