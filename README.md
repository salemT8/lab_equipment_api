# Lab Equipment API

## Project Description

The Lab Equipment API is a RESTful backend system built with Ruby on Rails that manages laboratory equipment, categories, and maintenance records. It supports full CRUD operations, business rule validations, and structured error handling for edge cases. The system is designed to ensure data integrity through database-level constraints and validated API responses.

---

## Setup Instructions

Follow these steps to run the project locally:

```bash
git clone <repo-url>
cd <project-directory>
bundle install
bin/rails db:create db:migrate db:seed
bin/rails server
```

The server will run on:

```
http://localhost:3000
```

---

## API Endpoints

### Categories

* `GET /categories` → List all categories
* `POST /categories` → Create category
* `GET /categories/:id` → Get single category
* `PATCH /categories/:id` → Update category
* `DELETE /categories/:id` → Delete category (protected if equipment exists)

### Equipment

* `GET /equipment` → List equipment (supports filtering)
* `POST /equipment` → Create equipment
* `GET /equipment/:id` → Get equipment details
* `PATCH /equipment/:id` → Update equipment
* `DELETE /equipment/:id` → Delete equipment

### Maintenance Records

* `GET /maintenance_records` → List maintenance records (supports filtering)
* `POST /maintenance_records` → Create record
* `GET /maintenance_records/:id` → Get record
* `PATCH /maintenance_records/:id` → Update record
* `DELETE /maintenance_records/:id` → Delete record

---

## Task Assignment Table

| Task                                       | Owner          | Branch             | Status      |
| ------------------------------------------ | -------------- | ------------------ | ----------- |
| 1 - Data model and migrations              | @YOUR_USERNAME | task-1-data-model  | Done        |
| 2 - Seed data                              | @TEAM_MEMBER   | task-2-seeds       | Done        |
| 3 - Category CRUD with delete protection   | @TEAM_MEMBER   | task-3-categories  | Done        |
| 4 - Equipment CRUD with filtering          | @TEAM_MEMBER   | task-4-equipment   | Done        |
| 5 - MaintenanceRecord CRUD with filtering  | @TEAM_MEMBER   | task-5-maintenance | Done        |
| 6 - Business rules (validations)           | @TEAM_MEMBER   | task-6-rules       | Done        |
| 7 - Edge case testing & curl documentation | @YOUR_USERNAME | task-7-edge-cases  | In Progress |

---

## Business Rules

* Equipment must belong to a valid category.
* Categories cannot be deleted if equipment exists under them.
* Maintenance records must belong to valid equipment.
* All required fields are validated at both model and database level.

---

## Edge Case Testing (Task 7)

The following scenarios are tested using curl:

* Invalid IDs return `404 Not Found`
* Validation failures return `422 Unprocessable Entity`
* Duplicate or conflicting data returns `409 Conflict`
* Missing required fields return structured error messages

All responses follow a consistent JSON error format.

---

## Notes

* All features were implemented using feature branches.
* Pull Requests were used for merging into `main`.
* Database constraints include foreign keys, indexes, and uniqueness rules.
