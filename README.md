
[![BailFacile](https://www.bailfacile.fr/img/logo_email.png)](https://www.bailfacile.fr)

[BailFacile](https://www.bailfacile.fr) is an online property management platform serving French landlords. We are building a super app for landlords assisting them in the daily management of long-term rentals : draft and e-sign compliant documents, record payments and outgoings and manage tenant relationships, 100% digitally and for a reasonable cost.
# BailFacile Laravel Challenge
## Some context...
### Why this challenge

This coding challenge is designed to assess skills of candidates in backend application development. It is language/framework agnostic, but some instructions are specific for [Laravel](https://www.laravel.com), since it is the technology we use (Laravel with PHP 8).

### How to proceed

Start from a [clean Laravel app](https://laravel.com/docs/8.x/installation) (or your framework of choice) and follow the instructions below.

Please attach a **read me** file with any relevant comments, instructions, explanations to your final submission.

Your code should be as clean as possible, tested and use Laravel conventions/building blocks. We are not testing your front-end skills here, so skip the views and focus on bulding models, API routes, middlewares, CLI commands, etc..

Your submission should include migrations and seeders with fake data (for users and documents) and existing data (document types provided below).

You are free (and even encouraged) to use third-party packages if relevant. If you do, you should explain in your notes why you think each specific package is the best available one for the job.

## Challenge

### 1. Documents and Document types

Design a system where users can own different types of documents each with specific properties. 
You should separate Documents (which can be owned by one user, is of a specific type) from DocumentTypes (which are unique and contain specific properties).

#### Documents

Documents belong to a user, are of a specific document_type and can usually be updated until they get esigned or sent via post.

#### Available DocumentTypes
  
| Name | Shortname | Type | Can be esigned | Can be sent via email | Can be sent via post | Can be updated
|--|--|--|--|--|--|--|
| **Rental agreement** | `rental_agreement` | `contract` | `true` | `true` | `false` | `true`
| **Rent guarantee agreement** | `rental_guarantee_agreement` | `contract` | `true` | `true` | `false` | `true`
| **Sub-letting agreement** | `subletting_agreement` | `contract` | `true` | `true` | `false` | `true`
| **Rental agreement amendment**| `rental_agreement_amendment` | `contract` | `true` | `true` | `false` | `true`
| **Rent receipt** | `rent_receipt` | `letter` | `false` | `true` | `true` | `true`
| **Rent invoice** | `rent_invoice` | `letter` | `false` | `true` | `true` | `true`
| **Late payment letter** | `late_payment_letter` | `letter` | `false` | `true` | `true` | `true`

### 2. API routes

Create RESTful API routes to :

#### **List documents**
-- Optional `user_id` filter
-- Optional `document_type` filter
-- Optional `created_at` and `updated_at` greated than filter
-- Limit to 10 results and support pagination
-- Each Document should return properties of its parent DocumentType along with the usual model columns.

#### **Create document**
-- Required `user_id` parameter
-- Required `document_type` parameter
-- Should return created Document

#### **ESign document**
-- Required `document_id` parameter
-- Make sure document can be Esigned
-- Once document is Esigned or Sent via post, it is locked and cannot be updated anymore
-- Should return updated Document

#### **Delete document**
-- Required `document_id` parameter
-- Only document that are not locked can be deleted
-- Return success or failure of request

## Bonus