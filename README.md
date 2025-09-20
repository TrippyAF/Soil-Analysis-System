# 🌱 Soil Analysis System Database

This project provides the **database schema** for a Soil Analysis System.  
It is designed to manage farmers’ details, soil samples, soil health card reports, laboratory records, crop recommendations, and fertilizer recommendations in an organized relational database.

---

## 📋 Features
- Store **farmer details** with contact information and location.
- Record **soil samples** with collection details and link them to farmers.
- Manage **soil testing labs** and their assigned samples.
- Maintain **soil health cards** with important parameters like pH, EC, Organic Carbon, Nitrogen, Phosphorus, and Potassium.
- Provide **crop recommendations** based on soil test results.
- Generate **fertilizer recommendations** linked to farmers, crops, and soil health cards.

---

## 🗄️ Database Schema

### 1. **Farmer**
| Column        | Type           | Description |
|---------------|---------------|-------------|
| id            | int (PK)      | Unique farmer ID |
| name_         | varchar(255)  | Farmer’s name |
| phone_no      | bigint        | Contact number |
| email_id      | varchar(255)  | Email (optional) |
| village       | varchar(255)  | Village name |
| sub_district  | varchar(255)  | Sub-district name |
| district      | varchar(255)  | District name |
| house_no      | int           | House number |

---

### 2. **Soil Sample**
| Column           | Type           | Description |
|------------------|---------------|-------------|
| id               | int (PK)      | Unique sample ID |
| date_of_collection | varchar(255) | Collection date |
| farm_area        | int           | Farm size (acres/hectares) |
| geo_position     | varchar(255)  | GPS coordinates |
| irrigation_status| varchar(255)  | Irrigation details |
| khasra_no        | int           | Khasra number (land record) |
| village          | varchar(255)  | Village name |
| farmer_id        | int (FK)      | References **farmer(id)** |

---

### 3. **Soil Test Lab**
| Column               | Type           | Description |
|-----------------------|---------------|-------------|
| id                   | int (PK)      | Lab ID |
| district             | varchar(255)  | District location |
| subdistrict          | varchar(255)  | Sub-district location |
| contact_person_name  | varchar(255)  | Contact person’s name |
| contact_person_phone_no | bigint      | Contact phone number |
| sample_id            | int (FK)      | References **soil_sample(id)** |

---

### 4. **Soil Health Card**
| Column                  | Type           | Description |
|--------------------------|---------------|-------------|
| id                       | int (PK)      | Health card ID |
| soil_type                | varchar(255)  | Soil type |
| ph_value                 | int           | pH value |
| electrical_conductivity  | int           | Electrical conductivity |
| organic_carbon           | int           | Organic carbon level |
| nitrogen                 | int           | Nitrogen level |
| phosphorus               | int           | Phosphorus level |
| potassium                | int           | Potassium level |
| lab_id                   | int (FK)      | References **soil_test_lab(id)** |
| sample_id                | int (FK)      | References **soil_sample(id)** |

---

### 5. **Crop Recommendation**
| Column                | Type           | Description |
|------------------------|---------------|-------------|
| id                     | int (PK)      | Crop recommendation ID |
| crop_name              | varchar(255)  | Crop name |
| recommended_nitrogen   | int           | Suggested nitrogen |
| recommended_phosphorus | int           | Suggested phosphorus |
| recommended_potassium  | int           | Suggested potassium |

---

### 6. **Fertilizer Recommendation**
| Column      | Type           | Description |
|-------------|---------------|-------------|
| id          | int (PK)      | Fertilizer recommendation ID |
| nitrogen    | int           | Fertilizer nitrogen content |
| phosphorus  | int           | Fertilizer phosphorus content |
| potassium   | int           | Fertilizer potassium content |
| manure      | varchar(255)  | Type of manure |
| health_id   | int (FK)      | References **_soil_health_card(id)** |
| crop_id     | int (FK)      | References **crop_recommendation(id)** |
| farmer_id   | int (FK)      | References **farmer(id)** |

---
