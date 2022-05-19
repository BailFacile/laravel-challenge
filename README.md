
[![BailFacile](https://www.bailfacile.fr/img/logo_email.png)](https://www.bailfacile.fr)

*[BailFacile](https://www.bailfacile.fr) is an online property management platform serving French landlords. We are building a super app for landlords assisting them in the daily management of long-term rentals : draft and e-sign compliant documents, record payments and outgoings, manage tenant relationships and much more, 100% digitally and for a reasonable cost.*
# BailFacile Laravel Challenge
## ❓ Why this challenge

This coding challenge is designed to assess the skills of candidates in backend application development. It is language/framework agnostic, but some instructions are specific for [Laravel](https://www.laravel.com), since it is the technology we use (Laravel with PHP 8).

## 🧑‍💻 Instructions for candidates

Depending on the role you are being interviewed for, the instructions are a bit different.
### 1. For a fullstack role

For fullstack developers, please only complete section 1 (Documents and DocumentTypes) and routes 1 and 2 of section 2 (API routes).
### 2. For a backend role

For backend developers, you are encouraged to complete as much as possible of this test to demonstrate your backend skills.
## 🏁 Challenge

### 1. Documents and DocumentTypes

#### Documents

Design a system where users can own different types of documents, each document having a specific document type.
Documents can be updated until they are esigned or sent via post.
#### Available DocumentTypes
  
| Name | Slug | Format | Can be esigned | Can be sent via email | Can be sent via post | Can be updated
|--|--|--|--|--|--|--|
| **Rental agreement** | `rental_agreement` | `contract` | ✅ | ✅ | ❌ | ✅
| **Rent guarantee agreement** | `rental_guarantee_agreement` | `contract` | ✅ | ✅ | ❌ | ✅
| **Sub-letting agreement** | `subletting_agreement` | `contract` | ✅ | ✅ | ❌ | ✅
| **Rental agreement amendment**| `rental_agreement_amendment` | `contract` | ✅ | ✅ | ❌ | ✅
| **Rent receipt** | `rent_receipt` | `letter` | ❌ | ✅ | ✅ | ✅
| **Rent invoice** | `rent_invoice` | `letter` | ❌ | ✅ | ✅ | ✅
| **Late payment letter** | `late_payment_letter` | `letter` | ❌ | ✅ | ✅ | ✅

### 2. API routes

Create RESTful API routes to :

#### 1. List documents

**⚙️ Parameters**

- Optional `user_id` filter
- Optional DocumentType `slug` filter
- Optional `created_at` and `updated_at` greater than filter
- Limit to 10 results and support pagination

**➡️ Response**

An array of documents and pagination information. Each Document should return properties of its parent DocumentType along with the usual model columns

#### 2. Create document

**⚙️ Parameters**

- Required `user_id` parameter
- Required DocumentType `slug` parameter

**➡️ Response**

Should return created Document

#### 3. ESign document

**⚙️ Parameters**

- Required `document_id` parameter
- Make sure Document can be Esigned
- Once Document is Esigned or Sent via post, it is locked and cannot be updated anymore

**➡️ Response**

Should return updated Document on success or failure if document is locked

#### 4. Delete document

**⚙️ Parameters**

- Required `document_id` parameter
- Only documents that are not locked can be deleted

**➡️ Response**

Should return deleted Document on success or failure of request
## ⭐ Bonus

#### Each DocumentType should have corresponding blade template (view)

Each DocumentType should have a specific blade template (view) linked to it. Insert random HTML in each template.
Have a function where you return the corresponding view (in HTML) for each document.
#### PDF generation

Every time a Document is saved, a PDF of the view should be generated and stored in a user specific folder.
We suggest using [Browsershot](https://github.com/spatie/browsershot) or [Laravel DomPDF](https://github.com/barryvdh/laravel-dompdf).

## 🧪 How to proceed

- Start from a [clean Laravel app](https://laravel.com/docs/8.x/installation) and follow the instructions below.

- Your code should be as clean as possible, tested and use Laravel conventions/building blocks.

- We are not testing your front-end skills here, so skip the views and focus on building models, tests, service providers, API routes, middlewares, CLI commands, etc..

- You are free (and even encouraged) to use third-party packages if relevant. If you do, you should explain in your notes why you think each specific package is the best available one for the job.

- **Your submission should include unit tests, migrations and seeders with fake data (for users and documents) and existing data (document types provided above).**

- **Please attach a read me file with any relevant comments, instructions, explanations to your final submission.**
