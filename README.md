# 🇧🇪 Belgium Energy Scenario – PATHS2050 (PREMISE)

This repository contains a **user-defined prospective energy scenario for Belgium** implemented in the https://github.com/polca/premise framework. It is based on the Belgian **PATHS2050 energy transition scenarios** and enables their integration into prospective life cycle assessment (pLCA).

---

## 📊 Overview

The goal of this repository is to generate **future background databases** reflecting Belgium’s energy transition pathways up to 2050.

The implementation builds on:
- The **PATHS2050 scenarios** developed by EnergyVille  
  https://perspective2050.energyville.be/
- The **premise-community-scenarios** approach  
  https://github.com/premise-community-scenarios/energy-perspective-2050-switzerland

---

## ⚙️ Features

- Integration of **Belgian national energy scenarios** into *premise*
- Custom **electricity mix evolution** over time
- Scenario-dependent **background database modifications**
- Compatibility with **prospective Life Cycle Assessment (pLCA)** workflows

---

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

---

## Getting Started

### 1. Requirements

- Python (>= 3.9 recommended)
- premise
- brightway2
- numpy, pandas, and standard scientific Python packages

Install premise:

pip install premise

---

### 2. Running the scenario

The main workflow is implemented in:

PLCA_SLB.ipynb

This notebook:
1. Loads PATHS2050 scenario data  
2. Configures the Belgian scenario  
3. Generates prospective databases using premise  
4. Applies transformations (e.g., electricity mixes)

Note: The function update_all() has been modified for this implementation.

---

## Electricity Mix

A customized Belgian electricity mix was developed based on PATHS2050 projections and integrated into the scenario.

This electricity mix was used in the following publication:

Huber, D. et al. (2024)  
Powering the circular future: Climate change and economic perspectives on second-life batteries in the Belgian context  
Journal of Industrial Ecology, 28(6), 1940–1951  
https://doi.org/10.1111/jiec.13566  

Key contributions:
- Time-dependent electricity mix evolution for Belgium  
- Integration into prospective LCA databases  
- Application to second-life battery systems  

---

## Contributing

Contributions, suggestions, and improvements are welcome.

If you would like to reference or include this scenario in  
premise-community-scenarios, feel free to open an issue or pull request.

---

## License

Please add a license (e.g., MIT, GPL-3.0) to clarify reuse conditions.

---

## 👤 Author

Dominik Huber

Anne Van Den Oever

---

## 🙏 Acknowledgements

- EnergyVille / VITO for the PATHS2050 scenarios  
- premise developers and community  
- Contributors to the Swiss reference implementation 
