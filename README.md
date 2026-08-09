# 🧪 Manual & API Testing Assessment
### Shoe-Selling E-Commerce Platform — Dynamic Search Feature (EverShop)

<div align="center">

![Testing](https://img.shields.io/badge/Type-Manual%20%26%20API%20Testing-blue?style=for-the-badge&logo=testinglibrary&logoColor=white)
![API](https://img.shields.io/badge/API%20Testing-Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-EverShop%20Demo-orange?style=for-the-badge&logo=shopify&logoColor=white)
![Status](https://img.shields.io/badge/Pass%20Rate-77.27%25-brightgreen?style=for-the-badge)
![Bugs](https://img.shields.io/badge/Bugs%20Found-4-red?style=for-the-badge&logo=bugsnag&logoColor=white)
![Test Cases](https://img.shields.io/badge/Test%20Cases-22-purple?style=for-the-badge)
![Course](https://img.shields.io/badge/Course-SQA%20%40%20Ostad-blueviolet?style=for-the-badge)

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
- [Project Structure](#-project-structure)
- [Tools Used](#️-tools-used)
- [Tester Information](#-tester-information)

---

## 🧾 Overview

This repository contains the complete **Manual & API Testing Assessment** for the dynamic **Search Feature** of a shoe-selling e-commerce platform built on **EverShop**.

The assessment is structured around four graded questions, covering every stage of the QA lifecycle — from requirements elicitation to test execution and defect reporting.

| Question | Topic | Marks |
|----------|-------|-------|
| Q1 | Client requirements questions for the Search feature | 20 |
| Q2 | Test cases derived from the client questions | 20 |
| Q3 | Test execution on demo.evershop.io + Bug Reports | 20 |
| Q4 | Happy Path (UI + API) for "Nike React" → Cart → Verify | 40 |

### 📊 Test Summary at a Glance

| Metric | Value |
|--------|-------|
| Total Test Cases | 22 |
| ✅ Passed | 17 |
| ❌ Failed | 4 |
| 🚫 Blocked | 0 |
| 🐛 Bugs Found | 4 |
| 📈 Pass Rate | **77.27%** |
| 🌐 Browser | Google Chrome (Latest) |
| 🖥️ OS | Windows 11 |

---

## ❓ Q1 — Client Questions [Mark: 20]

> Ordered by priority — most business-critical first.

### 🔴 Must Know (Business Critical)

| # | Question | Why It's Priority |
|---|----------|------------------|
| Q1 | **What fields/data should be searched?** (name, SKU, description, brand, tags?) | Defines core search scope — must be decided before any dev work |
| Q2 | **Real-time (live) search or submit-on-Enter?** (autocomplete dropdown?) | Determines entire UX pattern and backend architecture |
| Q3 | **What happens when no results are found?** ("No results" page / suggestions / popular products?) | Edge case critical for UX completeness and acceptance criteria |
| Q4 | **Should results be filtered, sorted, and paginated?** (by size, color, price; default sort order?) | Defines the full post-search experience |

### 🟡 Important (UX & Correctness)

| # | Question | Why It's Priority |
|---|----------|------------------|
| Q5 | **Handle typos and misspellings?** ("Did you mean: Nike?" / fuzzy search?) | Directly impacts conversion rates for misspelled queries |
| Q6 | **Case-insensitive and special character handling?** ("NIKE" = "nike" = "Nike"?) | Data normalization requirement before building search indexing |
| Q7 | **Partial / substring matching?** (typing "react" shows "Nike React"?) | Defines the matching algorithm — prefix vs full-text vs substring |
| Q8 | **Save search history / recent keywords?** (per-session or persistent / login-based?) | Personalization feature — secondary to core functionality |

### 🟢 Nice to Know (Advanced)

| # | Question | Why It's Priority |
|---|----------|------------------|
| Q9 | **Any blocked keywords or search redirects?** (competitor names → sale page?) | Business rules — can be addressed after core search works |
| Q10 | **Performance expectations?** (load time SLA, concurrent users, caching?) | Non-functional — critical for production, not initial testing |

---

## 📝 Q2 — Test Cases [Mark: 20]

> 22 structured test cases covering all areas of the Search feature.

<details>
<summary><b>🔽 Click to expand all 22 test cases</b></summary>

| TC-ID | Test Case Title | Precondition | Steps | Expected Result | Priority |
|-------|----------------|--------------|-------|-----------------|----------|
| TC-001 | Search by exact product name | Homepage open | 1. Click search icon 2. Type "Nike React" 3. Press Enter | Products matching "Nike React" displayed | 🔴 High |
| TC-002 | Search by brand name only | Homepage open | 1. Type "Nike" 2. Submit | All Nike-branded products displayed | 🔴 High |
| TC-003 | Search by partial keyword | Homepage open | 1. Type "react" 2. Submit | Products containing "react" in name appear | 🔴 High |
| TC-004 | Search by SKU code | Homepage open | 1. Type SKU "NJC90842" 2. Submit | Exact product matching that SKU returned | 🔴 High |
| TC-005 | Search with no results | Homepage open | 1. Type "xyzabc123" 2. Submit | "No products found" message shown | 🔴 High |
| TC-006 | Real-time autocomplete dropdown | Homepage open | 1. Type "Nike R" slowly 2. Pause | Dropdown suggestions appear in real-time | 🔴 High |
| TC-007 | Case-insensitive (mixed case) | Homepage open | 1. Search "NIKE REACT" 2. Search "nike react" 3. Compare | Both return identical results | 🔴 High |
| TC-008 | Lowercase search input | Homepage open | 1. Type "nike react" 2. Submit | Same results as "Nike React" | 🔴 High |
| TC-009 | UPPERCASE search input | Homepage open | 1. Type "NIKE REACT" 2. Submit | Same results as "Nike React" | 🔴 High |
| TC-010 | Typo tolerance / spell check | Homepage open | 1. Type "Nikke React" 2. Submit | "Did you mean: Nike React?" OR fuzzy results | 🟡 Medium |
| TC-011 | Extra whitespace in query | Homepage open | 1. Type "  Nike  React  " 2. Submit | Trimmed query returns correct results | 🟡 Medium |
| TC-012 | Special characters in query | Homepage open | 1. Type "Nike-React" 2. Submit | Correct results; no error thrown | 🟡 Medium |
| TC-013 | Default sort by relevance | Results visible | 1. Search "Nike React" 2. Observe order | Exact match appears first | 🟡 Medium |
| TC-014 | Sort results by price | Results visible | 1. Search "Nike" 2. Apply "Price: Low to High" | Results reorder lowest to highest | 🟡 Medium |
| TC-015 | Filter results by Size | Results visible | 1. Search "Nike" 2. Apply Size: Large | Only Large-sized products shown | 🟡 Medium |
| TC-016 | Filter results by Color | Results visible | 1. Search "Nike React" 2. Apply Color: Black | Only Black products shown | 🟡 Medium |
| TC-017 | Pagination on search results | 10+ results exist | 1. Search "shoes" 2. Scroll to bottom | Pagination controls visible and functional | 🟡 Medium |
| TC-018 | Empty search submission | Homepage open | 1. Press Enter with empty field | Graceful handling; no crash | 🔴 High |
| TC-019 | Spaces-only search | Homepage open | 1. Type "     " 2. Submit | Treated as empty; no crash | 🟡 Medium |
| TC-020 | Recent search history | User searched before | 1. Click search bar without typing | Recent searches shown in dropdown | 🟢 Low |
| TC-021 | Result count displayed | Results visible | 1. Search "Nike" 2. Check UI header | Total count shown e.g. "24 products found" | 🟢 Low |
| TC-022 | Product image in result card | Results visible | 1. Search "Nike React" 2. Observe cards | Image, name, and price visible per card | 🔴 High |
| TC-023 | Click result navigates to product page | Results visible | 1. Search "Nike React" 2. Click first result | Correct product detail page loads | 🔴 High |
| TC-024 | Keyboard accessibility (Tab) | Homepage open | 1. Tab to search field 2. Type 3. Press Enter | Search works fully via keyboard | 🟢 Low |
| TC-025 | Mobile viewport (375px) | Browser at 375px | 1. Open site 2. Tap search 3. Search "Nike React" | Search functional on mobile screen | 🔴 High |

</details>

---

## 📊 Q3 — Test Execution Report [Mark: 20]

**Executed on:** [https://demo.evershop.io](https://demo.evershop.io)  
**Browser:** Google Chrome (Latest) | **OS:** Windows 11 | **Date:** 2026-08-08

### Results at a Glance

```
Total: 22  |  ✅ Pass: 17  |  ❌ Fail: 4  |  🚫 Blocked: 0  |  📈 Pass Rate: 77.27%
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
| Step 8 | Verify cart contents & total | ✅ $255.00 total confirmed |

### 🛒 Cart Verification

| # | Product | Size | Color | Qty | Unit Price | Subtotal |
|---|---------|------|-------|-----|------------|----------|
| 1 | Nike React Miler 2 | Small | Black | 1 | $85.00 | $85.00 |
| 2 | Nike React Miler 2 | Medium | White | 1 | $85.00 | $85.00 |
| 3 | Nike React Miler 2 | Large | Green | 1 | $85.00 | $85.00 |
| | | | | | **Grand Total** | **$255.00** |

✅ Cart total correct: 3 × $85.00 = **$255.00**  
✅ All size/color variants correctly stored  
✅ Remove buttons present for each item  
✅ "Proceed to Checkout" button visible  

---

### Part B — API Test Journey

**Base URL:** `https://demo.evershop.io`

#### 🔍 Request 1 — Search Products (GET)

```http
GET /search?keyword=stainless&ajax=true
Host: demo.evershop.io
```

**Expected:** `200 OK` — Returns matching products with name, SKU, price, and URL key.

---

#### 📦 Request 2 — View Item Details

```http
GET /accessories/stainless-steel-thermos-yellow?ajax=true
Host: demo.evershop.io
```

**Expected:** `200 OK` — Returns full product details including available variants.

---

#### 🎨 Request 3 — View Item with Color Variant

```http
GET /accessories/stainless-steel-thermos-yellow?color=2&ajax=true
Host: demo.evershop.io
```

**Expected:** `200 OK` — Returns product detail for the specified color variant.

---

#### 🛒 Request 4 — Add Item to Cart (POST)

```http
POST /api/cart/mine/items
Content-Type: application/json
```

```json
{
  "sku": "THERMO-005-BLK",
  "qty": 3
}
```

**Expected:** `200 OK` — Returns updated cart with item count and subtotal.

---

#### 👁️ Request 5 — View Cart

```http
GET /cart?ajax=true
Host: demo.evershop.io
```

**Expected:** `200 OK` — Cart with all added items, quantities, and total.

---

#### ➕ Request 6 — Increase Item Quantity (PATCH)

```http
PATCH /api/cart/{cartId}/items/{itemId}
Content-Type: application/json
```

```json
{
  "qty": 1,
  "action": "increase"
}
```

**Expected:** `200 OK` — Cart quantity incremented by 1.

---

#### ➖ Request 7 — Decrease Item Quantity (PATCH)

```http
PATCH /api/cart/{cartId}/items/{itemId}
Content-Type: application/json
```

```json
{
  "qty": 1,
  "action": "decrease"
}
```

**Expected:** `200 OK` — Cart quantity decremented by 1.

---

#### 🗑️ Request 8 — Remove Cart Item (DELETE)

```http
DELETE /api/cart/{cartId}/items/{itemId}
Host: demo.evershop.io
```

**Expected:** `200 OK` — Item removed from cart.

---

#### ✅ Request 9 — Verify Cart After Removal

```http
GET /cart?ajax=true
Host: demo.evershop.io
```

**Expected:** `200 OK` — Cart reflects the removal; item count and total updated correctly.

---

### 🔎 Test Analysis

**✅ What Works Well:**
- Search returns relevant results at the correct URL pattern
- Full case-insensitivity across all input formats
- Size and color filters correctly narrow search results
- Multiple cart variants (size + color) added without issues
- Cart math is accurate — $255.00 grand total
- Pagination, sort by price, and filtering — all functional
- Mobile-responsive at 375px viewport
- Keyboard accessible via Tab + Enter

**❌ What Needs Improvement:**
- No SKU-based search support
- No live autocomplete dropdown while typing
- No spell correction or fuzzy matching for typos
- No recent search history preserved between sessions

---

## 🐛 Defect Log

### BUG-001 — Search by SKU Returns No Results

| Field | Details |
|-------|---------|
| **Severity** | Medium |
| **Priority** | Medium |
| **URL** | `https://demo.evershop.io/catalog/search?q=THERMO-005-YEL` |
| **Steps** | 1. Go to homepage → 2. Type a valid SKU in search → 3. Press Enter |
| **Expected** | Product matching the searched SKU should appear in results |
| **Actual** | "No products found" — SKU-based lookup completely ignored |
| **Status** | 🔴 Open |

> **Screenshot:**
> ![BUG-001 — SKU Search Failure](All%20Bugs%20screenshort/Bug-1.png)

---

### BUG-002 — Autocomplete Shows "No Results" for Valid Partial Keywords

| Field | Details |
|-------|---------|
| **Severity** | High |
| **Priority** | High |
| **URL** | `https://demo.evershop.io/` |
| **Steps** | 1. Click search field → 2. Slowly type "stainles" → 3. Pause 2 seconds |
| **Expected** | Dropdown suggestions should appear matching "stainless steel" products |
| **Actual** | Dropdown appears but shows "No results found for stainles" even though the product exists |
| **Status** | 🔴 Open |

> **Screenshot:**
> ![BUG-002 — No Autocomplete](All%20Bugs%20screenshort/Bug-2.png)

---

### BUG-003 — No Spell Check / "Did You Mean?" for Misspellings

| Field | Details |
|-------|---------|
| **Severity** | Medium |
| **Priority** | Medium |
| **URL** | `https://demo.evershop.io/catalog/search?q=Nikke+Reactt` |
| **Steps** | 1. Click search → 2. Type "Nikke Reactt" → 3. Press Enter |
| **Expected** | "Did you mean: Nike React?" OR fuzzy-matched results shown |
| **Actual** | Zero results with no correction suggestion offered |
| **Status** | 🔴 Open |

> **Screenshot:**
> ![BUG-003 — No Spell Check](All%20Bugs%20screenshort/Bug-3.png)

---

### BUG-004 — No Recent Search History

| Field | Details |
|-------|---------|
| **Severity** | Low |
| **Priority** | Low |
| **URL** | `https://demo.evershop.io/` |
| **Steps** | 1. Search any keyword → 2. Return to homepage → 3. Click search bar |
| **Expected** | Previous searches shown as recent search suggestions |
| **Actual** | Search field is blank; no history shown whatsoever |
| **Status** | 🔴 Open |

> **Screenshot:**
> ![BUG-004 — No Search History](All%20Bugs%20screenshort/Bug-4.png)

---

## 📦 API Collection

A fully configured **Postman collection** for the complete Happy Path API journey is included in this repository.

```
Happy Path Api testing/
└── evershop.postman_collection.json
```

### Endpoints Covered

| # | Request Name | Method | Endpoint |
|---|-------------|--------|----------|
| 1 | Get Search Item | `GET` | `/search?keyword={keyword}&ajax=true` |
| 2 | View Item Details | `GET` | `/accessories/{product-slug}?ajax=true` |
| 3 | View Item with Color Variant | `GET` | `/accessories/{product-slug}?color={id}&ajax=true` |
| 4 | Add to Cart | `POST` | `/api/cart/mine/items` |
| 5 | View Cart | `GET` | `/cart?ajax=true` |
| 6 | Increase Item Quantity | `PATCH` | `/api/cart/{cartId}/items/{itemId}` |
| 7 | Decrease Item Quantity | `PATCH` | `/api/cart/{cartId}/items/{itemId}` |
| 8 | Remove Cart Item | `DELETE` | `/api/cart/{cartId}/items/{itemId}` |
| 9 | Verify Cart After Removal | `GET` | `/cart?ajax=true` |

### How to Import

1. Open **Postman**
2. Click `Import` → `File`
3. Select `evershop.postman_collection.json`
4. Run requests in order: **1 → 2 → 3 → 4 → 5 → 6 → 7 → 8 → 9**

> **Note:** Copy the `cartId` and `itemId` values from earlier responses and substitute them into the PATCH and DELETE request URLs.

---

## 📁 Project Structure

```
Shoe-Selling-E-Commerce-Platform-Manual-API-Testing-Assessment/
│
├── 📄 README.md                              ← This file
│
├── 📂 All Bugs screenshort/
│   ├── 🖼️  Bug-1.png                         ← BUG-001: SKU search returns no results
│   ├── 🖼️  Bug-2.png                         ← BUG-002: Autocomplete shows no results for valid keywords
│   ├── 🖼️  Bug-3.png                         ← BUG-003: No spell check / fuzzy matching
│   └── 🖼️  Bug-4.png                         ← BUG-004: No recent search history
│
├── 📂 All Test Reports/
│   ├── 📝 Q1_Client_Questions.docx           ← 10 prioritized client requirement questions
│   ├── 📝 Q2_Test_Cases.docx                 ← 25 structured manual test cases
│   ├── 📝 Q3_Test_Execution_Report.docx      ← Execution results + 4 bug reports
│   └── 📝 Q4_Happy_Path_Journey.docx         ← UI + API happy path documentation
│
└── 📂 Happy Path Api testing/
    └── 📮 evershop.postman_collection.json   ← Importable Postman collection (9 requests)
```

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| 🌐 Google Chrome | Primary test execution browser |
| 📮 Postman | API collection authoring and execution |
| 📄 Microsoft Word | Test case and report documentation |
| 🛒 EverShop Demo | Application Under Test (AUT) |
| 🖼️ Snipping Tool | Bug screenshot capture |

---


---

<div align="center">



</div>
