# 🧪 Manual & API Testing Assessment
### Shoe-Selling E-Commerce Platform — Dynamic Search Feature (EverShop)

<div align="center">

![Testing](https://img.shields.io/badge/Type-Manual%20%26%20API%20Testing-blue?style=for-the-badge&logo=testinglibrary&logoColor=white)
![API](https://img.shields.io/badge/API%20Testing-Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-EverShop%20Demo-orange?style=for-the-badge&logo=shopify&logoColor=white)
![Status](https://img.shields.io/badge/Pass%20Rate-84%25-green?style=for-the-badge)
![Bugs](https://img.shields.io/badge/Bugs%20Found-4-red?style=for-the-badge&logo=bugsnag&logoColor=white)
![Test Cases](https://img.shields.io/badge/Test%20Cases-25-purple?style=for-the-badge)

**Platform Under Test:** [https://demo.evershop.io](https://demo.evershop.io)  
**Feature Under Test:** Dynamic Search Functionality  
**Test Date:** 2026-08-08  

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Q1 — Client Questions](#-q1--client-questions-mark-20)
- [Q2 — Test Cases](#-q2--test-cases-mark-20)
- [Q3 — Test Execution Report](#-q3--test-execution-report-mark-20)
- [Q4 — Happy Path Journey](#-q4--happy-path-journey-mark-40)
- [Defect Log](#-defect-log)
- [API Collection](#-api-collection)
- [Google Drive](#-google-drive)
- [Project Structure](#-project-structure)

---

## 🧾 Overview

This repository contains the complete **Manual Testing Assessment** for the dynamic **Search Feature** implementation on a shoe-selling e-commerce platform.

The testing was performed on the **EverShop Demo** site. The assessment covers:

| Question | Topic | Marks |
|----------|-------|-------|
| Q1 | Client requirements questions for the Search feature | 20 |
| Q2 | Test cases derived from the client questions | 20 |
| Q3 | Test execution on demo.evershop.io + Bug Reports | 20 |
| Q4 | Happy Path (UI + API) for "Nike React" search → Cart → Verify | 40 |

### 📊 Test Summary

| Metric | Result |
|--------|--------|
| Total Test Cases | 25 |
| Passed | 21 |
| Failed | 4 |
| Bugs Found | 4 |
| Pass Rate | **84%** |

---

## ❓ Q1 — Client Questions [Mark: 20]

> Ordered by priority — most business-critical first.

### Must Know (Business Critical)

| # | Question | Why It's Priority |
|---|----------|------------------|
| Q1 | **What fields/data should be searched?** (name, SKU, description, brand, tags?) | Defines core search scope — must be decided before any dev work |
| Q2 | **Real-time (live) search or submit-on-Enter?** (autocomplete dropdown?) | Determines entire UX pattern and backend architecture |
| Q3 | **What happens when no results are found?** ("No results" page / suggestions / popular products?) | Edge case critical for UX completeness and acceptance criteria |
| Q4 | **Should results be filtered, sorted, and paginated?** (by size, color, price; default sort order?) | Defines the full post-search experience |

### Important (UX & Correctness)

| # | Question | Why It's Priority |
|---|----------|------------------|
| Q5 | **Handle typos and misspellings?** ("Did you mean: Nike?" / fuzzy search?) | Directly impacts conversion rates for misspelled queries |
| Q6 | **Case-insensitive and special character handling?** ("NIKE" = "nike" = "Nike"?) | Data normalization requirement before building search indexing |
| Q7 | **Partial / substring matching?** (typing "react" shows "Nike React"?) | Defines the matching algorithm — prefix vs full-text vs substring |
| Q8 | **Save search history / recent keywords?** (per-session or persistent / login-based?) | Personalization feature — secondary to core functionality |

### Nice to Know (Advanced)

| # | Question | Why It's Priority |
|---|----------|------------------|
| Q9 | **Any blocked keywords or search redirects?** (competitor names → sale page?) | Business rules — can be addressed after core search works |
| Q10 | **Performance expectations?** (load time SLA, concurrent users, caching?) | Non-functional — critical for production, not initial testing |

---

## 📝 Q2 — Test Cases [Mark: 20]

> 25 structured test cases covering all areas of the Search feature.

<details>
<summary><b>Click to expand all 25 test cases</b></summary>

| TC-ID | Test Case Title | Precondition | Steps | Expected Result | Priority |
|-------|----------------|--------------|-------|-----------------|----------|
| TC-001 | Search by exact product name | Homepage open | 1. Click search icon 2. Type "Nike React" 3. Press Enter | Products matching "Nike React" displayed | High |
| TC-002 | Search by brand name only | Homepage open | 1. Type "Nike" 2. Submit | All Nike-branded products displayed | High |
| TC-003 | Search by partial keyword | Homepage open | 1. Type "react" 2. Submit | Products containing "react" in name appear | High |
| TC-004 | Search by SKU code | Homepage open | 1. Type SKU "NJC90842" 2. Submit | Exact product matching that SKU returned | High |
| TC-005 | Search with no results | Homepage open | 1. Type "xyzabc123" 2. Submit | "No products found" message shown | High |
| TC-006 | Real-time autocomplete dropdown | Homepage open | 1. Type "Nike R" slowly 2. Pause | Dropdown suggestions appear in real-time | High |
| TC-007 | Case-insensitive (mixed case) | Homepage open | 1. Search "NIKE REACT" 2. Search "nike react" 3. Compare | Both return identical results | High |
| TC-008 | Lowercase search input | Homepage open | 1. Type "nike react" 2. Submit | Same results as "Nike React" | High |
| TC-009 | UPPERCASE search input | Homepage open | 1. Type "NIKE REACT" 2. Submit | Same results as "Nike React" | High |
| TC-010 | Typo tolerance / spell check | Homepage open | 1. Type "Nikke React" 2. Submit | "Did you mean: Nike React?" OR fuzzy results | Medium |
| TC-011 | Extra whitespace in query | Homepage open | 1. Type "  Nike  React  " 2. Submit | Trimmed query returns correct results | Medium |
| TC-012 | Special characters in query | Homepage open | 1. Type "Nike-React" 2. Submit | Correct results; no error thrown | Medium |
| TC-013 | Default sort by relevance | Results visible | 1. Search "Nike React" 2. Observe order | Exact match appears first | Medium |
| TC-014 | Sort results by price | Results visible | 1. Search "Nike" 2. Apply "Price: Low to High" | Results reorder lowest to highest | Medium |
| TC-015 | Filter results by Size | Results visible | 1. Search "Nike" 2. Apply Size: Large | Only Large-sized products shown | Medium |
| TC-016 | Filter results by Color | Results visible | 1. Search "Nike React" 2. Apply Color: Black | Only Black products shown | Medium |
| TC-017 | Pagination on search results | 10+ results exist | 1. Search "shoes" 2. Scroll to bottom | Pagination controls visible and functional | Medium |
| TC-018 | Empty search submission | Homepage open | 1. Press Enter with empty field | Graceful handling; no crash | High |
| TC-019 | Spaces-only search | Homepage open | 1. Type "     " 2. Submit | Treated as empty; no crash | Medium |
| TC-020 | Recent search history | User searched before | 1. Click search bar without typing | Recent searches shown in dropdown | Low |
| TC-021 | Result count displayed | Results visible | 1. Search "Nike" 2. Check UI header | Total count shown e.g. "24 products found" | Low |
| TC-022 | Product image in result card | Results visible | 1. Search "Nike React" 2. Observe cards | Image, name, and price visible per card | High |
| TC-023 | Click result navigates to product page | Results visible | 1. Search "Nike React" 2. Click first result | Correct product detail page loads | High |
| TC-024 | Keyboard accessibility (Tab) | Homepage open | 1. Tab to search field 2. Type 3. Press Enter | Search works fully via keyboard | Low |
| TC-025 | Mobile viewport (375px) | Browser at 375px | 1. Open site 2. Tap search 3. Search "Nike React" | Search functional on mobile screen | High |

</details>

---

## 📊 Q3 — Test Execution Report [Mark: 20]

**Executed on:** [https://demo.evershop.io](https://demo.evershop.io)  
**Browser:** Google Chrome (Latest) | **OS:** Windows 11 | **Date:** 2026-08-08

### Results at a Glance

```
Total: 25   Pass: 21   Fail: 4   Blocked: 0   Pass Rate: 84%
```

### Execution Results

| TC-ID | Title | Status | Bug ID |
|-------|-------|--------|--------|
| TC-001 | Search by exact product name | ✅ PASS | — |
| TC-002 | Search by brand name only | ✅ PASS | — |
| TC-003 | Search by partial keyword | ✅ PASS | — |
| TC-004 | Search by SKU code | ❌ FAIL | BUG-001 |
| TC-005 | Search with no results | ✅ PASS | — |
| TC-006 | Real-time autocomplete dropdown | ❌ FAIL | BUG-002 |
| TC-007 | Case-insensitive (mixed case) | ✅ PASS | — |
| TC-008 | Lowercase search | ✅ PASS | — |
| TC-009 | UPPERCASE search | ✅ PASS | — |
| TC-010 | Typo / misspelling tolerance | ❌ FAIL | BUG-003 |
| TC-011 | Extra whitespace handling | ✅ PASS | — |
| TC-012 | Special characters | ✅ PASS | — |
| TC-013 | Default sort by relevance | ✅ PASS | — |
| TC-014 | Sort by price | ✅ PASS | — |
| TC-015 | Filter by Size | ✅ PASS | — |
| TC-016 | Filter by Color | ✅ PASS | — |
| TC-017 | Pagination | ✅ PASS | — |
| TC-018 | Empty search submission | ✅ PASS | — |
| TC-019 | Spaces-only search | ✅ PASS | — |
| TC-020 | Recent search history | ❌ FAIL | BUG-004 |
| TC-021 | Result count displayed | ✅ PASS | — |
| TC-022 | Product image in result card | ✅ PASS | — |
| TC-023 | Click result → Product page | ✅ PASS | — |
| TC-024 | Keyboard accessibility | ✅ PASS | — |
| TC-025 | Mobile viewport (375px) | ✅ PASS | — |

---

## 🚀 Q4 — Happy Path Journey [Mark: 40]

### Scenario
> Search **"Nike React"** → Select the **first product** → Add **Small/Black**, **Medium/White**, **Large/Green** to cart → Verify cart total = **$255.00**

---

### Part A — UI Test Journey

| Step | Action | Result |
|------|--------|--------|
| Step 1 | Navigate to `https://demo.evershop.io` | ✅ Homepage loads |
| Step 2 | Search `"Nike react"` — URL: `/catalog/search?q=Nike+react` | ✅ Results page loads |
| Step 3 | Click first product (Nike React Miler 2) | ✅ Product page with size & color options |
| Step 4 | Add **Small + Black**, Qty=1 → "Add to Cart" | ✅ Cart count = 1 |
| Step 5 | Add **Medium + White**, Qty=1 → "Add to Cart" | ✅ Cart count = 2 |
| Step 6 | Add **Large + Green**, Qty=1 → "Add to Cart" | ✅ Cart count = 3 |
| Step 7 | Navigate to Cart page | ✅ All 3 items visible |
| Step 8 | Verify cart contents & total | ✅ $255.00 total correct |

### Cart Verification

| # | Product | Size | Color | Qty | Price | Subtotal |
|---|---------|------|-------|-----|-------|---------|
| 1 | Nike React Miler 2 | Small | Black | 1 | $85.00 | $85.00 |
| 2 | Nike React Miler 2 | Medium | White | 1 | $85.00 | $85.00 |
| 3 | Nike React Miler 2 | Large | Green | 1 | $85.00 | $85.00 |
| | | | | | **Grand Total** | **$255.00** |

- ✅ Cart total correct: 3 x $85.00 = **$255.00**
- ✅ All size/color variants correctly stored
- ✅ Remove buttons present for each item
- ✅ "Proceed to Checkout" button visible

---

### Part B — API Test Journey

**Base URL:** `https://demo.evershop.io`

#### Request 1 — Search Products (GraphQL)

```http
POST /graphql
Content-Type: application/json
```

```json
{
  "query": "query SearchProducts($filters:[FilterInput]){ products(filters:$filters){ items{ name sku price{ regular{ value text }} url_key } total } }",
  "variables": {
    "filters": [
      { "key": "name",  "operation": "ilike", "value": "%Nike react%" },
      { "key": "limit", "operation": "eq",    "value": "10" },
      { "key": "page",  "operation": "eq",    "value": "1"  }
    ]
  }
}
```

**Expected:** `200 OK` — Returns Nike React products with name, SKU, price, url_key.

---

#### Request 2 — Create Cart with Small Black Variant

```http
POST /api/carts
Content-Type: application/json
```

```json
{
  "customer_full_name": "Test User",
  "customer_email": "testuser@example.com",
  "items": [
    { "sku": "NR-MILER2-BLK-S", "qty": 1 }
  ]
}
```

**Expected:** `200 OK` — Returns `cartId`, `product_price: 85`, `total: 85`

---

#### Request 3 — Add Medium White Variant

```http
POST /api/cart/mine/items
Content-Type: application/json
Cookie: cart_id={cartId}
```

```json
{ "sku": "NR-MILER2-WHT-M", "qty": 1 }
```

**Expected:** `200 OK` — Cart count = 2

---

#### Request 4 — Add Large Green Variant

```http
POST /api/cart/mine/items
Content-Type: application/json
Cookie: cart_id={cartId}
```

```json
{ "sku": "NR-MILER2-GRN-L", "qty": 1 }
```

**Expected:** `200 OK` — Cart count = 3

---

#### Request 5 — Verify Cart Contents

```http
GET /api/cart/mine
Cookie: cart_id={cartId}
```

**Expected Response:**

```json
{
  "data": {
    "count": 3,
    "sub_total": 255,
    "grand_total": 255,
    "items": [
      { "product_sku": "NR-MILER2-BLK-S", "product_price": 85, "qty": 1 },
      { "product_sku": "NR-MILER2-WHT-M", "product_price": 85, "qty": 1 },
      { "product_sku": "NR-MILER2-GRN-L", "product_price": 85, "qty": 1 }
    ]
  }
}
```

---

### Test Analysis

**What Works Well:**
- Search returns relevant results at the correct URL pattern
- Full case-insensitivity across all input formats
- Size and color filters correctly narrow search results
- Multiple cart variants (size + color) added without issues
- Cart math is accurate — $255.00 grand total
- Pagination, sort by price, and filtering — all functional
- Mobile-responsive at 375px viewport
- Keyboard accessible via Tab + Enter

**What Needs Improvement:**
- No SKU-based search support
- No live autocomplete dropdown while typing
- No spell correction or fuzzy matching for typos
- No recent search history preserved between sessions

---

## 🐛 Defect Log

### BUG-001 — Search by SKU Not Working

| Field | Details |
|-------|---------|
| **Severity** | Medium |
| **Priority** | Medium |
| **URL** | `https://demo.evershop.io/catalog/search?q=NJC90842` |
| **Steps** | 1. Go to homepage  2. Type "NJC90842" in search  3. Press Enter |
| **Expected** | Product matching SKU "NJC90842" should appear in results |
| **Actual** | "We're sorry, we can't find what you're looking for" — no results |
| **Status** | Open |

---

### BUG-002 — No Live Autocomplete While Typing

| Field | Details |
|-------|---------|
| **Severity** | High |
| **Priority** | High |
| **URL** | `https://demo.evershop.io/` |
| **Steps** | 1. Click search field  2. Slowly type "Nike R"  3. Pause 2 seconds |
| **Expected** | Dropdown of matching suggestions should appear in real-time |
| **Actual** | No dropdown; user must press Enter to see results |
| **Status** | Open |

---

### BUG-003 — No Spell Check / "Did You Mean?" for Misspellings

| Field | Details |
|-------|---------|
| **Severity** | Medium |
| **Priority** | Medium |
| **URL** | `https://demo.evershop.io/catalog/search?q=Nikke+Reactt` |
| **Steps** | 1. Click search  2. Type "Nikke Reactt"  3. Press Enter |
| **Expected** | "Did you mean: Nike React?" OR fuzzy-matched results |
| **Actual** | Zero results; no correction or suggestion offered |
| **Status** | Open |

---

### BUG-004 — No Recent Search History

| Field | Details |
|-------|---------|
| **Severity** | Low |
| **Priority** | Low |
| **URL** | `https://demo.evershop.io/` |
| **Steps** | 1. Search "Nike React"  2. Return to homepage  3. Click search bar |
| **Expected** | "Nike React" shown as a recent search suggestion |
| **Actual** | Search field blank; no history shown |
| **Status** | Open |

---

## 📦 API Collection

Postman collection for the Q4 API journey is included in this repository:

```
EverShop_NikeReact_Cart_Journey.postman_collection.json
```

**How to import:**
1. Open **Postman**
2. Click `Import` → `File`
3. Select the `.json` collection file
4. Run requests in order: **1 → 2 → 3 → 4 → 5**

> **Note:** Copy the `cartId` from Request 2's response and pass it as a Cookie for Requests 3, 4, and 5.

---

## ☁️ Google Drive

**[SQA_Assessment_2026 — Google Drive Folder](#)** *(replace with your actual link)*

### Folder Structure

```
SQA_Assessment_2026/
├── Q1_Client_Questions.docx
├── Q2_Test_Cases.docx
├── Q3_Test_Execution_Report.docx
├── Q4_Happy_Path_Journey.docx
├── Screenshots/
│   ├── TC001_search_nike_react_PASS.png
│   ├── TC004_sku_search_FAIL.png
│   ├── TC006_no_autocomplete_FAIL.png
│   ├── TC010_misspelling_FAIL.png
│   ├── TC020_no_search_history_FAIL.png
│   └── Cart_Verification_PASS.png
├── Bug_Reports/
│   ├── BUG-001_SKU_Search_Failure_2026-08-08.pdf
│   ├── BUG-002_No_Autocomplete_2026-08-08.pdf
│   ├── BUG-003_No_Spell_Check_2026-08-08.pdf
│   └── BUG-004_No_Search_History_2026-08-08.pdf
└── API_Collection/
    └── EverShop_NikeReact_Cart_Journey.postman_collection.json
```

> **Naming Convention for Bugs:** `BUG-[ID]_[Short_Title]_[YYYY-MM-DD].pdf`

---

## 📁 Project Structure

```
Manual-Testing-Assessment/
├── README.md
├── Q1_Client_Questions.docx
├── Q2_Test_Cases.docx
├── Q3_Test_Execution_Report.docx
├── Q4_Happy_Path_Journey.docx
└── EverShop_NikeReact_Cart_Journey.postman_collection.json
```

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Google Chrome | Test execution browser |
| Postman | API test collection and execution |
| Google Drive | Asset, screenshot and report storage |
| EverShop Demo | Application under test |
| Microsoft Word | Test documentation |

---

## 👤 Tester Information

| Field | Details |
|-------|---------|
| **Course** | Software Quality Assurance (SQA) |
| **Institute** | Ostad |
| **Assessment Date** | 2026-08-08 |
| **Feature Tested** | Dynamic Search — Shoe E-Commerce Platform |
| **Platform** | https://demo.evershop.io |

---

<div align="center">

**If this assessment was helpful, consider giving it a star!**

</div>
