# SkillLink — Freelance Marketplace System

A full-stack freelance marketplace system built as a semester project for
Database Management Systems (CSC 220) at Bahria University Islamabad.

SkillLink models the complete lifecycle of freelance work — user registration,
project posting, competitive bidding, contract creation, milestone-based
payment tracking, and mutual reviews — powered by a fully normalized
Oracle XE relational database.

---

## Live System Overview

| Layer | Technology | Details |
|-------|-----------|---------|
| Database | Oracle XE 21c | 15 tables, normalized to 3NF |
| Backend | Node.js + Express | 35 REST API endpoints |
| Frontend | React.js | 3 role-based interfaces |
| Auth | JWT | Client, Freelancer, Admin roles |
| DB Client | DBeaver | SQL editor and schema browser |

---

## How It Works

1. A **Client** registers and posts a project with budget and deadline
2. **Freelancers** browse open projects and submit bids
3. Client reviews bids and selects the best one
4. A **Contract** is automatically created via an atomic transaction
5. Client releases **Payment** on milestone completion
6. Both parties leave a **Review** after project completion
7. **Admin** monitors the entire platform from a read-only dashboard

---

## Database Design

- **15 Tables** covering all entities in the freelancing workflow
- **Specialization** — Users supertype splits into Client and Freelancer subtypes (disjoint, total)
- **Weak Entities** — Bids and Reviews depend on identifying entities
- **M:N Relationships** — Resolved through User\_Skills and Project\_Category junction tables
- **3NF Normalization** — No repeating groups, no partial dependencies, no transitive dependencies
- **3 Atomic Transactions** — User registration, bid acceptance, payment recording
- **Constraints** — PK, FK, UNIQUE, CHECK, NOT NULL, DEFAULT enforced throughout

---

## Key Features

- Role-based access control at three levels (route, navigation, page)
- JWT authentication with 7-day token validity
- Atomic bid acceptance: accepts winner, rejects all others, creates contract, sends notification in one transaction
- Milestone-based payments — multiple payments per contract supported
- Mutual review system — both client and freelancer can rate each other
- Dispute tracking with status management
- Admin panel with visibility into all 15 Oracle tables
- Connection pooling for efficient database access

---

## Project Structure
