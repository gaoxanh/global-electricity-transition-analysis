# Global Electricity Transition Analysis

## Overview

This project investigates how changes in the electricity generation mix are associated with changes in carbon outcomes across countries.

The analysis follows the transition from:

**Electricity Generation Structure → Structural Shifts → Country Transition Profiles → Carbon Intensity → Decoupling → Vietnam Case Study**

The project is developed as a sequence of nine Jupyter notebooks, with intermediate results stored as checkpoint files so that later analyses can reuse validated outputs without rerunning the entire pipeline.

---

## Research Question

> **How does the transition in electricity generation mix relate to changes in carbon emissions across countries?**

### Vietnam Case Study

> **How does Vietnam's electricity transition fit the global pathway, especially around the 2021–2022 turning point?**

---

## Dataset

**Source:** Ember – Global Electricity Data

**File:** `data/raw/release_generation_yearly_global.csv`

Main dataset characteristics:

- **104,203 rows**
- **24 columns**
- **1985–2025**
- **224 areas**
- **17 electricity sources**

The dataset contains electricity generation, generation change, generation share, capacity, emissions, emissions intensity, geographic information, and country-group membership indicators.

### Main Electricity Sources

- Coal
- Gas
- Hydro
- Solar
- Wind
- Bioenergy
- Other renewables
- Nuclear
- Other fossil

The dataset also contains aggregate categories such as Renewables, Fossil, Clean, Wind and solar, and Hydro/bioenergy/other renewables.

> Aggregate and component rows are not summed together in the analysis to avoid double counting.

---

## Quick Start

1. Clone or download the repository.
2. Open the `notebooks/` directory.
3. Install the required Python packages from `requirements.txt`.
4. Run the notebooks in order from **01 → 09**.
5. Keep the `checkpoints/` directory available because later notebooks load validated intermediate results from these files.
6. The final synthesis is `notebooks/09_Final_Synthesis.ipynb`.

The notebooks use relative paths to `data/` and `checkpoints/`, so they should be run from the project structure rather than as isolated files.

---

## Analytical Scope

The core country-level comparison focuses primarily on **2012–2022** because this period provides consistent country coverage for the main transition indicators.

The longer **2000–2025** period is used for selected global and Vietnam trend analysis.

The year **2025** is not used as the primary full-country comparison because country coverage is incomplete.

---

## Project Workflow

```text
01 Data Understanding
        ↓
02 Data Quality & Structure
        ↓
03 Global EDA
        ↓
04 Anomaly & Event Detection
        ↓
05 Event Validation & Comparative Interpretation
        ↓
06 Country Energy Transition Profiles
        ↓
07 Relationship / Deeper Analysis
        ↓
08 Carbon, Capacity & Transition Analysis
        ↓
09 Final Synthesis
```

### Final Evidence Chain

```text
Global Transition
      ↓
Structural Shift
      ↓
Country Pathway
      ↓
Carbon Outcome
      ↓
Decoupling
      ↓
Strong vs Bad Outcomes
      ↓
International Spotlight
      ↓
Vietnam Turning Point
      ↓
Source Replacement
      ↓
Vietnam vs Global
      ↓
Conclusion
```

---

## Notebook Structure

### Note 01 — Data Understanding

`notebooks/01_data_understanding.ipynb`

Introduces the dataset, identifies the analytical structure, defines the electricity-source categories, and establishes the interpretation rules used throughout the project.

### Note 02 — Data Quality & Structure

`notebooks/02_data_quality.ipynb`

Checks missing values, duplicates, logical keys, data coverage, negative values, aggregate consistency, and other structural properties.

### Note 03 — Global EDA

`notebooks/03_eda_global.ipynb`

Explores global electricity generation and electricity-source shares over time.

Key outputs include:

- Global generation trends
- Electricity mix evolution
- Source-level changes
- Long-term transition patterns

### Note 04 — Anomaly & Event Detection

`notebooks/04_anomaly_event.ipynb`

Identifies unusual changes in electricity-source shares using a statistical event-detection approach.

The analysis focuses on structural shifts rather than treating every unusual observation as an error.

### Note 05 — Event Validation & Comparative Interpretation

`notebooks/05_Event_Validation_Comparative_Interpretation.ipynb`

Validates selected events and compares their magnitude and context.

Vietnam's 2021 solar expansion is one of the highlighted cases.

### Note 06 — Country Energy Transition Profiles

`notebooks/06_Country_Energy_Transition_Profiles.ipynb`

Constructs country-level transition features for 2012–2022 and classifies countries into transition profiles based on changes in Fossil share.

The analysis also examines differences in carbon-intensity change between transition profiles using one-way ANOVA and Tukey HSD.

### Note 07 — Relationship / Deeper Analysis

`notebooks/07_Relationship_Deeper_Analysis.ipynb`

Examines relationships between electricity-mix changes and carbon intensity.

The analysis includes:

- Correlation screening
- Spearman relationships
- Transition-pattern comparisons
- System-size robustness checks
- Good vs bad transition comparisons

These results are interpreted as **associations**, not causal effects.

### Note 08 — Carbon, Capacity & Transition Analysis

`notebooks/08_Carbon_Capacity_Geographic_Transition.ipynb`

Extends the analysis to direct carbon outcomes.

The notebook classifies country-year observations according to changes in generation and emissions, including:

- Generation ↑ / Emissions ↑
- Generation ↑ / Emissions ↓
- Generation ↓ / Emissions ↓
- Generation ↓ / Emissions ↑
- No material change

It then compares electricity-mix changes between favorable and unfavorable outcomes and examines strong decoupling cases.

### Note 09 — Final Synthesis

`notebooks/09_Final_Synthesis.ipynb`

Synthesizes the evidence from Notes 01–08 into a single storyline.

The notebook connects:

- Global electricity transition
- Structural shifts
- Country transition profiles
- Carbon-intensity outcomes
- Decoupling patterns
- International examples
- Vietnam's 2020–2022 turning point
- Source replacement
- Vietnam vs global transition pathway

No new analytical branch is introduced in the final synthesis.

---

## Key Findings

### 1. Global Electricity Transition

Between 2000 and 2025:

- Global electricity generation increased substantially.
- Renewables' share increased from approximately **18.71% to 33.48%**.
- Fossil generation share decreased from approximately **64.71% to 57.69%**.
- Solar and wind experienced the strongest growth in generation share.

The transition is therefore characterized by a changing electricity mix rather than a simple replacement of all fossil generation.

### 2. Country Transition Profiles

Countries do not follow a single transition pathway.

The country-level analysis identifies three broad profiles:

- **Fossil decline**
- **Stable / moderate**
- **Fossil growth**

The profiles are associated with substantially different changes in carbon intensity.

### 3. Transition and Carbon Intensity

The relationship analysis shows strong associations between changes in Fossil/Renewables shares and changes in carbon intensity.

Countries with declining Fossil share and increasing Renewables share tend to have more favorable carbon-intensity outcomes.

The analysis does not establish causality.

### 4. Decoupling

Among country-year observations with increasing electricity generation, both favorable and unfavorable carbon outcomes are observed.

A key distinction is:

- **Generation ↑ / Emissions ↓**: favorable decoupling outcome
- **Generation ↑ / Emissions ↑**: unfavorable outcome

The favorable group is characterized primarily by stronger decreases in Fossil share and increases in Renewables share, with Hydro also showing an important source-level difference.

> The term **Strong Decoupling** is reserved for the threshold-based subset identified in the analysis and is not used interchangeably with all Generation ↑ / Emissions ↓ observations.

### 5. Vietnam

Vietnam shows a major electricity transition over the long term.

The **2020–2022 period** represents an important turning point:

- Coal share decreased substantially.
- Gas share decreased.
- Hydro share increased.
- Solar and Wind expanded rapidly.
- Electricity generation increased.
- Emissions decreased.
- Carbon intensity decreased.

However, when comparing the broader **2012–2022** period with the global pathway, Vietnam's carbon-intensity trend was less favorable than the global trend.

This distinction is important: Vietnam's **2020–2022 turning point** should not be generalized to the entire 2012–2022 period.

---

## Statistical Methods

The project uses methods appropriate for exploratory and comparative data analysis:

- Descriptive statistics
- Missing-value and duplicate checks
- Distribution and outlier analysis
- Time-series aggregation
- Electricity-mix decomposition
- Z-score based anomaly/event screening
- Pearson correlation
- Spearman correlation
- One-way ANOVA
- Tukey HSD
- Effect size analysis
- Robustness checks
- Comparative group analysis
- Decoupling classification

Statistical results are interpreted in terms of **association and group differences**, not causal inference.

---

## Checkpoint Pipeline

Intermediate results are stored under:

`checkpoints/`

Current checkpoint stages include:

```text
note01_initial.pkl
note02_data_quality.pkl
note03_eda_overview.pkl
note04_anomaly_event.pkl
note05_event_validation.pkl
note06_country_transition_profiles.pkl
note06_anova_carbon_intensity.pkl
note07_relationship_deeper_analysis.pkl
note08_carbon_transition_rq4.pkl
note09_final_synthesis.pkl
```

This allows later notebooks to reuse validated analytical objects without rerunning every previous notebook.

---

## Reproducibility

### Recommended Environment

- Python 3.x
- Jupyter Notebook / JupyterLab
- pandas
- NumPy
- Matplotlib
- SciPy
- statsmodels
- scikit-learn

Install the dependencies with:

```bash
pip install -r requirements.txt
```

Then run the notebooks sequentially from Note 01 to Note 09.

---

## Important Data Interpretation Rules

### Avoid Double Counting

Component sources and aggregate source rows are both present in the dataset.

For example:

```text
Solar + Wind
Renewables
Fossil
Clean
```

should not be summed together with their component sources.

### Missing Values

Missing values are not automatically converted to zero.

A missing observation means that the value is unavailable, not that generation or capacity is zero.

### Negative Generation

Negative values are not automatically removed.

They are interpreted according to the electricity-source definition and data structure, with Net imports treated as a system-flow variable rather than a generation component.

### Country Coverage

The analysis prioritizes periods with sufficient country coverage. In particular, 2025 is not treated as a complete cross-country comparison.

---

## Limitations

1. The analysis is observational and does not establish causal relationships.
2. Electricity-source categories include both component and aggregate rows, requiring careful aggregation rules.
3. Country coverage varies by year.
4. Carbon-emissions and carbon-intensity fields contain missing values.
5. Some transition relationships may be influenced by extreme country cases.
6. Electricity transition is analyzed primarily through generation mix and related carbon indicators; other factors such as economic structure, demand-side efficiency, policy interventions, and fuel prices are outside the main scope of this project.
7. Vietnam is used as a case study and should not be interpreted as representative of all countries.

---

## Repository Structure

```text
global-electricity-transition-analysis/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── raw/
│       └── release_generation_yearly_global.csv
│
├── checkpoints/
│   ├── note01_initial.pkl
│   ├── note02_data_quality.pkl
│   ├── note03_eda_overview.pkl
│   ├── note04_anomaly_event.pkl
│   ├── note05_event_validation.pkl
│   ├── note06_country_transition_profiles.pkl
│   ├── note06_anova_carbon_intensity.pkl
│   ├── note07_relationship_deeper_analysis.pkl
│   ├── note08_carbon_transition_rq4.pkl
│   └── note09_final_synthesis.pkl
│
└── notebooks/
    ├── 01_data_understanding.ipynb
    ├── 02_data_quality.ipynb
    ├── 03_eda_global.ipynb
    ├── 04_anomaly_event.ipynb
    ├── 05_Event_Validation_Comparative_Interpretation.ipynb
    ├── 06_Country_Energy_Transition_Profiles.ipynb
    ├── 07_Relationship_Deeper_Analysis.ipynb
    ├── 08_Carbon_Capacity_Geographic_Transition.ipynb
    └── 09_Final_Synthesis.ipynb
```

---

## Conclusion

The project provides a structured data-analysis framework for examining how electricity-generation transitions are associated with carbon outcomes across countries.

The overall evidence suggests that countries with stronger declines in Fossil share and stronger growth in Renewables tend to exhibit more favorable carbon-intensity outcomes. Decoupling cases further demonstrate that electricity generation can increase while emissions decrease, although this outcome is not universal.

Vietnam illustrates this transition through a pronounced **2020–2022 turning point**, when rapid growth in Hydro, Solar and Wind coincided with declining Fossil share, emissions, and carbon intensity.

Overall:

> **The composition of electricity generation is an important factor associated with differences in carbon outcomes across countries, while the evidence does not establish causality.**
