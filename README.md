# 🇧🇪 Belgium Energy Scenario – PATHS2050 (PREMISE)

This repository contains a **user-defined prospective energy scenario for Belgium** implemented in the https://github.com/polca/premise framework. It is based on the Belgian **PATHS2050 energy transition scenarios** and enables their integration into prospective life cycle assessment (pLCA). PATHS2050 is an energy system study developed by **EnergyVille**, based on the **TIMES-Be model**, which computes **cost-optimal pathways to a near carbon-neutral Belgium by 2050**. This repository is build on the Main edition from 2022 (https://perspective2050.energyville.be/results/main-edition-2022).

The scenarios:
- are **not forecasts**, but exploratory pathways  
- enforce **net-zero emissions by 2050** (with small residual emissions)  
- differ in technology choices and resource availability  

## 🔀 Scenarios

### Central
Balanced pathway using a mix of electrification, clean fuels (e.g. hydrogen), and carbon capture.

### Electrification
Stronger electrification with:
- large offshore wind expansion  
- optional new nuclear (SMRs)  

### Clean Molecules
Higher reliance on imported synthetic fuels (e.g. hydrogen), with limited CO₂ storage capacity.

## 📈 Key insights

- Final energy demand decreases (~−33%)  
- Electricity demand more than doubles  
- Fossil fuels are largely phased out  
- Different trade-offs between electrification, fuels, and costs  

## 📊 Overview

The goal of this repository is to generate **future background databases** reflecting Belgium’s energy transition pathways up to 2050.

The implementation builds on:
- The **PATHS2050 scenarios** developed by EnergyVille  
  https://perspective2050.energyville.be/
- The **premise-community-scenarios** approach  
  https://github.com/premise-community-scenarios/energy-perspective-2050-switzerland

## ⚙️ Features

- Integration of **Belgian national energy scenarios** into *premise*
- Custom **electricity mix evolution** over time
- Scenario-dependent **background database modifications**
- Compatibility with **prospective Life Cycle Assessment (pLCA)** workflows

## 📁 Repository Structure

.
├── configuration_file      # Scenario configuration files for premise  
├── scenario_data           # Processed scenario inputs  
├── VITO_PATHS_raw_data     # Raw input data from PATHS2050 (VITO/EnergyVille)  
├── inventories            # Modified or additional inventory data  
├── databases              # Saved premise output databases  
├── export                 # Exported datasets / results  
├── PLCA_SLB.ipynb         # Main notebook for scenario generation and analysis  
├── datapackage.json       # Data package definition  
└── README.md  

## Getting Started

## 🚀 Usage with premise

This repository is designed to be used as an external scenario datapackage in `premise`.

### Example workflow

```python
import bw2data, bw2io
from premise import NewDatabase
from datapackage import Package

# Load datapackage (local or remote)
fp = "path/to/datapackage.json"
paths2050 = Package(fp)

# Set your Brightway project
bw2data.projects.set_current("your_project_name")

# Define scenarios
ndb = NewDatabase(
    scenarios=[
        {"model": "remind", "pathway": "SSP2-NPi", "year": 2023},
        {"model": "remind", "pathway": "SSP2-NPi", "year": 2032},
        {"model": "remind", "pathway": "SSP2-NPi", "year": 2044},
        {"model": "remind", "pathway": "SSP2-NPi", "year": 2047},
        {"model": "remind", "pathway": "SSP2-PkBudg1150", "year": 2023},
        {"model": "remind", "pathway": "SSP2-PkBudg1150", "year": 2032},
        {"model": "remind", "pathway": "SSP2-PkBudg1150", "year": 2044},
        {"model": "remind", "pathway": "SSP2-PkBudg1150", "year": 2047},
    ],
    source_db="cutoff391",
    source_version="3.9.1",
    key="your_premise_key",
    external_scenarios=[paths2050],
)

# Apply all transformations
ndb.update_all()

# Write databases
ndb.write_db_to_brightway(name=[
    "cutoff_3.9.1_remind_SSP2-NPi_2023",
    "cutoff_3.9.1_remind_SSP2-NPi_2032",
    "cutoff_3.9.1_remind_SSP2-NPi_2044",
    "cutoff_3.9.1_remind_SSP2-NPi_2047",
    "cutoff_3.9.1_remind_SSP2-PkBudg1150_2023",
    "cutoff_3.9.1_remind_SSP2-PkBudg1150_2032",
    "cutoff_3.9.1_remind_SSP2-PkBudg1150_2044",
    "cutoff_3.9.1_remind_SSP2-PkBudg1150_2047",
])
```

### Notes

- Replace `"path/to/datapackage.json"` with your local path or raw GitHub link  
- Ensure `source_db` matches your Brightway setup  
- Provide your own ecoinvent `key`  
``

## Use case and application

The updated Belgian electricity mix was used to model the use stage of second-life batteries charged in Belgium in the future. The study is published here:

Huber, D. et al. (2024). *Powering the circular future: Climate change and economic perspectives on second-life batteries in the Belgian context.* Journal of Industrial Ecology, 28(6), 1940–1951. doi: https://doi.org/10.1111/jiec.13566  

## Author

Dominik Huber

Anne Van Den Oever

## Acknowledgements

- EnergyVille / VITO for the exchange and providing the underlying data of the PATHS2050 scenarios  
- premise developers and community  
- Contributors to the Swiss reference implementation 
