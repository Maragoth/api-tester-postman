## 🐞 Bugs Found During Testing

### 1. No validation on /products/add
- Sending POST /products/add with an empty JSON body (or no required fields) results in HTTP 201 Created.
- The response contains a generated product ID despite no data being provided.
- This indicates a missing validation layer in the backend.
- Status: Confirmed. Reproducible.


## 📁 Saved Results

The full test run report is saved in:
docs/results/collection_run_2025-05-08.json
