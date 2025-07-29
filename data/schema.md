# Suture – Submission Schema

This document defines the fields we collect for each storage rent report. Submissions may be in JSON, YAML, or entered through a future web form.

---

## 🗃️ Core Fields

| Field             | Type     | Description |
|------------------|----------|-------------|
| `brand`          | string   | Name of the storage company (e.g. Extra Space, CubeSmart) |
| `city`           | string   | City where the unit is located |
| `state`          | string   | State abbreviation (e.g. GA, TX) |
| `zip_code`       | string   | Optional – ZIP code (only first 5 digits) |
| `unit_size`      | string   | Size of the unit (e.g. 5x5, 10x20) |
| `climate_control`| boolean  | Whether the unit has climate control |
| `indoor_access`  | boolean  | Whether the unit is accessed from inside the building |
| `drive_up`       | boolean  | Whether the unit has direct drive-up vehicle access |
| `floor_level`    | string   | "ground", "upper", "basement", or "unknown" |
| `elevator_access`| boolean  | Whether the unit requires or is reachable via elevator |

---

## 💵 Pricing Lifecycle

| Field         | Type    | Description |
|--------------|---------|-------------|
| `is_promo`    | boolean | Whether the unit was originally rented at a promotional rate |
| `promo_rate`  | number  | Optional – the initial discounted or advertised rate |
| `base_rate`   | number  | The standard rate after promo ends (contractual starting rate) |
| `last_rate`   | number  | The rate most recently paid before the current hike |
| `new_rate`    | number  | The newly announced rate after the hike |

---

## 📅 Timing & Notice

| Field               | Type    | Description |
|--------------------|---------|-------------|
| `hike_notice_date` | date    | Date the price increase notice was received (YYYY-MM-DD) |
| `effective_date`   | date    | Date the new price takes effect (YYYY-MM-DD) |
| `notice_type`      | string  | How the hike was delivered (e.g. email, letter, portal) |
| `was_warned`       | boolean | Whether the customer received meaningful advance notice |
| `account_duration` | number  | Months the unit was rented before the hike |

---

## 🧾 Optional Notes

| Field      | Type    | Description |
|------------|---------|-------------|
| `comments` | string  | Free-form notes about the experience or pricing history |

---  

## Planned Schema Note

Promo rates are collected for transparency but are not used in pricing trend comparisons, since they reflect temporary marketing discounts, not true long-term costs.  


---  

## 🔒 Redaction Reminder

All uploaded files must have PII (personally identifiable info) redacted before sharing:

- ❌ Name, address, unit number, phone, email, account/barcode  
- ✔️ City, state, brand, unit details, dates, and pricing should remain

A redaction tool is planned, but users should currently blur or block data manually.

---

## 🛠 Sample JSON Entry

```json
{
  "brand": "Extra Space",
  "city": "Buford",
  "state": "GA",
  "zip_code": "30518",
  "unit_size": "10x10",
  "climate_control": true,
  "indoor_access": true,
  "drive_up": false,
  "floor_level": "upper",
  "elevator_access": true,

  "is_promo": true,
  "promo_rate": 1.00,
  "base_rate": 75.00,
  "last_rate": 75.00,
  "new_rate": 175.00,

  "hike_notice_date": "2025-07-01",
  "effective_date": "2025-08-01",
  "notice_type": "email",
  "was_warned": false,
  "account_duration": 3,

  "comments": "Initial promo was $1. Then jumped from $75 to $175 in just 90 days."
}
