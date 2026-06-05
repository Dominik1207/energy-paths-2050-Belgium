# 🇧🇪 Belgium Energy Scenario – PATHS2050 (PREMISE)

This repository contains a **user-defined prospective energy scenario for Belgium** implemented in the https://github.com/polca/premise framework. It is based on the Belgian **PATHS2050 energy transition scenarios** and enables their integration into prospective life cycle assessment (pLCA).


## ⚡ About PATHS2050 – The Power of Perspective

The PATHS2050 platform is a large-scale energy system analysis developed by **EnergyVille**, involving more than 200 researchers. It aims to answer three key questions:

- What does the current Belgian energy system look like?
- What is required to reach a **climate-neutral Belgium by 2050**?
- Which **technological and policy pathways** can enable this transition?

To address these questions, EnergyVille developed the **TIMES-Be model**, a techno-economic optimization model that:

- Simulates the Belgian energy system from today to 2050  
- Minimizes total system costs while meeting energy service demand  
- Adapts to evolving **technology, policy, and resource constraints**  
- Produces **cost-optimal transition pathways** rather than forecasts  

All scenarios enforce **net-zero greenhouse gas emissions by 2050**, while allowing for:
- residual emissions (~2 Mt CO₂)  
- carbon removal technologies (e.g. CCS, DAC, BECCS)  

---

## 🔀 Scenario Design

PATHS2050 explores three internally consistent scenarios, each representing a **different strategic pathway toward decarbonization**.

### 1. Central Scenario (Balanced Transition)

A **technology-neutral pathway** with balanced deployment of:

- Energy efficiency improvements  
- Electrification  
- Clean fuels (hydrogen, synthetic molecules)  
- Carbon capture and storage (CCS)  

Key characteristics:
- Final energy demand decreases by ~1/3  
- Electricity demand roughly doubles  
- Clean molecules represent ~11% of final energy demand in 2050  
- CCS plays a major role in industry and energy supply  

---

### 2. Electrification Scenario (Power-driven Transition)

A pathway emphasizing **strong electrification and expansion of low-carbon electricity supply**.

Additional assumptions:
- +16 GW offshore wind capacity (North Sea)  
- Deployment of **Small Modular Reactors (SMRs)** by 2050  

Key characteristics:
- Electricity demand increases by factor ~2.3 (vs 2020)  
- Faster emissions reductions, especially in:
  - transport  
  - buildings  
  - power sector  
- Lowest total system cost among scenarios by 2050  
- Reduced reliance on imported fuels  

---

### 3. Clean Molecules Scenario (Fuel-based Transition)

A pathway relying more heavily on **imported synthetic fuels** (e.g. hydrogen and derivatives).

Additional assumptions:
- Low-cost access to clean molecules  
- Limited availability of CO₂ storage (max ~5 Mt/year)  

Key characteristics:
- Higher role of hydrogen and synthetic fuels (~14% in 2050)  
- Strong continued dependence on electricity  
- Higher short-term emissions in industry (2030–2040)  
- Similar long-term decarbonization outcome  

---

## 📈 Cross-cutting Insights

Across all scenarios:

- Final energy demand decreases by ~33%  
- Electricity demand **more than doubles**  
- Fossil fuels are phased out by 2050  
- Net-zero is achieved with residual emissions requiring removal  

Trade-offs exist between:
- electrification  
- fuel imports  
- infrastructure investments  
- system costs  

Estimated additional annual system costs:
- €11.7–21 billion by 2050 (~2–4% of GDP)

---


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

## Author

Dominik Huber

Anne Van Den Oever

---

## Acknowledgements

- EnergyVille / VITO for the PATHS2050 scenarios  
- premise developers and community  
- Contributors to the Swiss reference implementation 
