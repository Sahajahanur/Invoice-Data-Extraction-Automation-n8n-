# Invoice-Data-Extraction-Automation-n8n-

## 📌 Project Overview

This project automates the end-to-end invoice data extraction process using n8n, Google Drive, OCR API, and Google Sheets.

It allows you to:

* Scan invoices stored in Google Drive
* Extract structured data (invoice number, date, items, billing info)
* Upload the cleaned data to Google Sheets
* Avoid manual data entry mistakes
* Operate fully no-code with reusable workflows

This workflow can be extended to accounting, ERP, finance, and business analytics use cases.

## ⭐ Features

✔ Input invoices from Google Drive
✔ Automatic OCR extraction
✔ Data validation & error handling
✔ Duplicate invoice prevention
✔ Structured dataset creation
✔ Google Sheets integration
✔ Easily scalable for large datasets

## 🏗️ System Architecture
    
    +-------------------+
    | Google Drive      |
    | (Invoice PDF)     |
    +---------+---------+
    
              |
              v
    +-------------------+
    | n8n Trigger       |
    | When clicked      |
    +-------------------+
              |
              v
    +-------------------+
    | List files        |
    | Loop over items   |
    +-------------------+
              |
       Validation Stage
     +--------+--------+
     | Download file   |
     | Switch          |
     | Extract from PDF|
     | IF Valid        |
     +--------+--------+
              |
              v
    +-----------------------+
    | OCR API Request       |
    | (AI/LLM extraction)   |
    +-----------------------+
              |
              v
    +-----------------------+
    | Extract JSON Output   |
    | Clean & Map fields    |
    +-----------------------+
              |
              v
    +-----------------------+
    | Google Sheets Write   |
    | Append/Update Row     |
    +-----------------------+

## 🧰 Tech Stack

| Component       | Technology           |
| --------------- | -------------------- |
| Workflow engine | n8n                  |
| Storage         | Google Drive         |
| OCR             | OCR Space API        |
| Database        | Google Sheets        |
| LLM Processing  | Gemini (Google PaLM) |
| Code            | No-code Automation   |


## 🔄 Workflow Steps

### 1️⃣ Trigger

When user clicks Execute workflow

### 2️⃣ Validation Block

* Google Drive — search files
* Loop through invoices
* Download PDF
* Check file type
* Extract data using OCR
* Filter valid invoices

### 3️⃣ OCR & Data Extraction

* Send base64 PDF to OCR API
* Parse JSON response
* Map fields:

    * Invoice number
    * Date
    * Billing company details
    * Customer information
    * Line items

 ### 4️⃣ Upload to Google Sheets

 * Append or update invoice rows
 * Insert line items in separate sheet
 * Use invoice_number as primary key

  ## 📂 Google Sheets Structure


Sheet 1 — invoice_details

| invoice_number | date | billing_company | billing_company_address | billing_company_email | customer_name | … |

Sheet 2 — invoice_items

| invoice_number | item_name | quantity | price | tax | total |


## 🚀 How to Run

### Prerequisites

* n8n cloud account
* Google Drive with sample invoices
* Google Sheets with 2 sheets
* OCR API key (OCR.Space)

## 🛠️ Setup Instructions

### Step 1: Connect Accounts

In n8n → Credentials:

* Google Drive OAuth2
* Google Sheets OAuth2
* OCR HTTP Request

### Step 2: Import Workflow  

* Import JSON file into n8n
* Replace spreadsheet ID
* Replace OCR API key
* Save workflow

### Step 3: Test Run

* Click Execute Workflow
* Check Google Sheets auto fill

## 🛑 Error Handling

This workflow handles:

* Invalid PDF
* Missing invoice number
* Duplicate invoice rows
* OCR extraction failure

## 📈 Performance

* Extraction speed: ~2s per invoice
* Zero manual entry
* 100% consistent schema

<img width="1918" height="832" alt="image" src="https://github.com/user-attachments/assets/3557762c-f76b-4318-be79-9e2a93005111" />

































  
