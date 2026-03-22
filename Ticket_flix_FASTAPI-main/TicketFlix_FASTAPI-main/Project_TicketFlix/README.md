# 🎬 Ticket_Flix— Movie Ticket Booking API

![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Python](https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge&logo=python)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=for-the-badge&logo=pydantic)
![Swagger](https://img.shields.io/badge/Swagger-UI-green?style=for-the-badge&logo=swagger)

A complete, fully functional **FastAPI backend** for a Movie Ticket Booking System — built as the **Final Project** for the FastAPI Internship Training (Days 1–6).

This project covers all 6 days of FastAPI concepts — from basic GET endpoints to advanced search, sorting, pagination, multi-step workflows, and full CRUD operations.

---

## 📁 Project Structure

```
fastapi-movie-ticket-booking/
├── main.py                  # All API endpoints and logic
├── requirements.txt         # Project dependencies
├── README.md                # Project documentation
└── screenshots/             # Swagger UI test screenshots
    ├── Q1_home_route.png
    ├── Q2_get_all_movies.png
    ├── Q3_get_movie_by_id.png
    ├── Q4_get_all_bookings.png
    ├── Q5_movies_summary.png
    ├── Q6_booking_validation.png
    ├── Q7_helper_functions.png
    ├── Q8_post_booking.png
    ├── Q9_promo_code.png
    ├── Q10_filter_movies.png
    ├── Q11_add_movie.png
    ├── Q12_update_movie.png
    ├── Q13_delete_movie.png
    ├── Q14_seat_hold.png
    ├── Q15_confirm_release_hold.png
    ├── Q16_search_movies.png
    ├── Q17_sort_movies.png
    ├── Q18_paginate_movies.png
    ├── Q19_bookings_search_sort_page.png
    └── Q20_browse_combined.png
```

---

## 🚀 How to Run the Project

### Step 1 — Clone the Repository
```bash
git clone githublink
cd fastapi-movie-ticket-booking
```

### Step 2 — Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3 — Start the Server
```bash
uvicorn main:app --reload
```

### Step 4 — Open Swagger UI
Open your browser and go to:
```
http://127.0.0.1:8000/docs
```

---

## 📦 Dependencies

```
fastapi
uvicorn
pydantic
```

---

## 🎯 Project Overview

**CineStar** is a REST API backend that simulates a real-world movie ticket booking system. Users can:

- Browse available movies
- Filter movies by genre, language, price, and seats
- Search movies by keyword
- Book tickets with seat type selection
- Apply promo codes for discounts
- Hold seats temporarily and confirm or release them
- Add, update, and delete movies (admin operations)
- Sort and paginate through movies and bookings

---

## 📌 All 20 API Endpoints

### 🟢 Day 1 — GET Endpoints

| # | Method | Route | Description |
|---|--------|-------|-------------|
| Q1 | GET | `/` | Welcome home route |
| Q2 | GET | `/movies` | List all movies with total and total seats |
| Q3 | GET | `/movies/{movie_id}` | Get a single movie by ID |
| Q4 | GET | `/bookings` | List all bookings with total revenue |
| Q5 | GET | `/movies/summary` | Stats — genres, most/cheapest ticket, total seats |

### 🟡 Day 2 — POST + Pydantic Validation

| # | Method | Route | Description |
|---|--------|-------|-------------|
| Q6 | POST | `/bookings` | Pydantic validation — test with seats=0 |
| Q8 | POST | `/bookings` | Create a booking using helper functions |
| Q9 | POST | `/bookings` | Apply promo codes SAVE10 / SAVE20 |

### 🟠 Day 3 — Helper Functions + Filter

| # | Method | Route | Description |
|---|--------|-------|-------------|
| Q7 | — | helpers | `find_movie()`, `calculate_ticket_cost()`, `filter_movies_logic()` |
| Q10 | GET | `/movies/filter` | Filter by genre, language, max_price, min_seats |

### 🔵 Day 4 — CRUD Operations

| # | Method | Route | Description |
|---|--------|-------|-------------|
| Q11 | POST | `/movies` | Add new movie — returns 201, duplicate check |
| Q12 | PUT | `/movies/{movie_id}` | Update ticket price or seats — 404 if not found |
| Q13 | DELETE | `/movies/{movie_id}` | Delete movie — blocked if bookings exist |

### 🟣 Day 5 — Multi-Step Workflow

| # | Method | Route | Description |
|---|--------|-------|-------------|
| Q14 | POST | `/seat-hold` | Hold seats temporarily |
| Q14 | GET | `/seat-hold` | View all active holds |
| Q15 | POST | `/seat-confirm/{hold_id}` | Confirm hold — convert to booking |
| Q15 | DELETE | `/seat-release/{hold_id}` | Release hold — return seats to movie |

### 🔴 Day 6 — Search, Sort, Pagination

| # | Method | Route | Description |
|---|--------|-------|-------------|
| Q16 | GET | `/movies/search` | Search by keyword across title, genre, language |
| Q17 | GET | `/movies/sort` | Sort by ticket_price, title, duration, seats |
| Q18 | GET | `/movies/page` | Paginate movies with page and limit |
| Q19 | GET | `/bookings/search` | Search bookings by customer name |
| Q19 | GET | `/bookings/sort` | Sort bookings by total_cost or seats |
| Q19 | GET | `/bookings/page` | Paginate bookings |
| Q20 | GET | `/movies/browse` | Combined — search + filter + sort + paginate |

---

## 🧠 Concepts Covered (All 6 Days)

| Day | Concept | What Was Built |
|-----|---------|---------------|
| Day 1 | GET Endpoints + JSON | Home route, list all movies, get by ID, bookings list, summary stats |
| Day 2 | POST + Pydantic Models | `BookingRequest` with min_length, gt, le constraints. `NewMovie` model |
| Day 3 | Helper Functions + Filter | `find_movie()`, `calculate_ticket_cost()`, `filter_movies_logic()` with is not None checks |
| Day 4 | CRUD Operations | POST /movies (201), PUT update, DELETE with 404 + business rule protection |
| Day 5 | Multi-Step Workflow | Seat-Hold → Seat-Confirm → Seat-Release (3 connected endpoints) |
| Day 6 | Search + Sort + Pagination | Keyword search, multi-field sort, page/limit pagination, combined /browse |

---

## 🎟️ Seat Types

| Seat Type | Price Multiplier |
|-----------|-----------------|
| `standard` | 1× base price |
| `premium` | 1.5× base price |
| `recliner` | 2× base price |

---

## 🏷️ Promo Codes

| Promo Code | Discount |
|------------|----------|
| `SAVE10` | 10% off total cost |
| `SAVE20` | 20% off total cost |

The API returns both `original_cost` and `total_cost` (after discount) in the booking response.

---

## 🎬 Sample Movie Dataset

The project comes pre-loaded with 8 movies:

| ID | Title | Genre | Language | Price | Seats |
|----|-------|-------|----------|-------|-------|
| 1 | Inception | Action | English | 250 | 80 |
| 2 | The Dark Knight | Action | English | 300 | 60 |
| 3 | Kal Ho Naa Ho | Drama | Hindi | 150 | 100 |
| 4 | Munnabhai MBBS | Comedy | Hindi | 120 | 120 |
| 5 | Conjuring | Horror | English | 200 | 50 |
| 6 | 3 Idiots | Comedy | Hindi | 130 | 90 |
| 7 | RRR | Action | Telugu | 180 | 70 |
| 8 | Tumbbad | Horror | Hindi | 160 | 40 |

---

## 🔁 Multi-Step Workflow (Day 5)

The seat-hold workflow connects 3 endpoints:

```
POST /seat-hold         →  Hold seats temporarily (reduces seats_available)
POST /seat-confirm/{id} →  Confirm hold → creates a real booking
DELETE /seat-release/{id} → Cancel hold → returns seats back to movie
```

---

## 🔍 Combined Browse Endpoint (Day 6)

`GET /movies/browse` supports all these optional parameters:

| Parameter | Default | Description |
|-----------|---------|-------------|
| `keyword` | None | Search in title, genre, language |
| `genre` | None | Filter by genre |
| `language` | None | Filter by language |
| `sort_by` | `ticket_price` | Sort field |
| `order` | `asc` | Sort direction |
| `page` | `1` | Page number |
| `limit` | `3` | Items per page |

**Order of operations:** keyword filter → genre/language filter → sort → paginate

---


## 📸 API Testing

All 20 endpoints have been tested using **Swagger UI** at `http://127.0.0.1:8000/docs`

Screenshots for every question are available in the `screenshots/` folder.

---


**Tech Stack:** Python · FastAPI · Pydantic · Uvicorn · Swagger UI

---

#FastAPI #Python #BackendDevelopment #APIDevelopment 
