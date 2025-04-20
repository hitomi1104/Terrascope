# 🌱 Carbon Emissions Case Study (Terrascope)

This project is a full end-to-end GHG emissions analysis using real-world raw activity data, emission factor databases (e.g., DEFRA, BioGrace), and Python-based data processing. It covers Scope 1, 2, and 3 emissions categories and outputs structured emissions summaries and documentation for reporting and presentation.

---

## 🎯 Objective

To calculate the carbon footprint across different emissions scopes using provided datasets and standard methodology. The project:
- Identifies which Scope (1, 2, or 3) each activity belongs to
- Applies appropriate emission factors
- Aggregates emissions by business unit
- Documents methodology and outputs in a reproducible, auditable format

---

## 📦 Data Structure

📁 raw_data/
│   ├── biodiesel.xlsx
│   ├── natural_gas_and_electricity.xlsx
│   ├── upstream_transportation.xlsx
│   ├── business_travel.xlsx
│   └── …
📁 guides_and_dbs/
│   ├── DEFRA_conversion-factors-2021.xlsm
│   ├── BioGrace_standard_values.xlsm
│   └── Technical Guidance for Scope 3 Emissions.pdf
📁 outputs/
│   ├── ghg_inventory_table.xlsx
│   ├── transformation_steps.xlsx
│   └── presentation_slides.pptx
📁 notebooks/
│   ├── 01_scope1_biodiesel.ipynb
│   ├── 02_scope2_energy.ipynb
│   └── 03_scope3_upstream_transport.ipynb

---

## 🧪 Methodology

### Step-by-Step Process

#### 1. Understand the Raw Data
- Review each `.xlsx` file for structure, units, and completeness.
- Determine what type of activity the data represents.

#### 2. Map to Scope and Category
- Scope 1: Direct emissions (e.g., fuel combustion)
- Scope 2: Indirect emissions (e.g., electricity use)
- Scope 3: All other indirect emissions (e.g., transport, travel, waste)

#### 3. Apply Emission Factors
- Use DEFRA or equivalent database
- Align factors with unit (e.g., liters, kWh, km, kg)

#### 4. Merge with Org Mapping
- Use `org_mapping.xlsx` to assign business units
- Derive final BU using `Level 1` or fallback to `Level 2`

#### 5. Calculate Emissions
```python
Emissions = Activity Data × Emission Factor