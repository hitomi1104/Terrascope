

## ✅ Objective

# Estimate carbon emissions from each dataset by:
1. Mapping to GHG Scope and Category
2. Applying correct emission factors
3. Merging with organizational structure
4. Calculating total emissions per business unit
5. Documenting logic and results

---

## 🛠️ Tools Used

- Python 3.x
- pandas
- Jupyter Notebook
- Excel input files (.xlsx)
- DEFRA 2021 emissions factor database

---

## 🔁 Process Overview

### Step-by-Step Workflow (Biodiesel Example – Scope 1)

1. **Load Data**
    ```python
    biodiesel_df = pd.read_excel("biodiesel.xlsx")
    org_map_df = pd.read_excel("org_mapping.xlsx")
    ```

2. **Apply Emission Factor**
    ```python
    EMISSION_FACTOR = 0.00249  # tCO₂e per liter for Biodiesel 30%
    biodiesel_df["Emissions (tCO2e)"] = biodiesel_df["Total quantity"] * EMISSION_FACTOR
    ```

3. **Merge with Org Mapping**
    ```python
    org_map_df = org_map_df.rename(columns={"Unit mapping": "Plant"})
    merged_df = pd.merge(biodiesel_df, org_map_df, on="Plant", how="left")
    ```

4. **Map to Business Unit**
    ```python
    merged_df["Business Unit"] = merged_df["Level 1"].combine_first(merged_df["Level 2"])
    ```

5. **Summarize Emissions by BU**
    ```python
    summary = merged_df.groupby("Business Unit")["Emissions (tCO2e)"].sum().reset_index()
    ```

6. **Generate Report Tables**
    - GHG Inventory Table
    - Data Transformation Documentation

---

## 📌 Notes

- The emission factor used (`0.00249 tCO₂e/L`) is sourced from DEFRA 2021 for Biodiesel B30 under Scope 1 mobile combustion.
- All outputs are reproducible and can be extended to additional datasets (e.g., electricity, travel, waste) using the same pattern.

---

## ✍️ Author

Built by [Your Name], based on Terrascope Carbon Analyst case study instructions.