---
name: RMM
source_tool: "[[bioatmosphere_eca]]"
source_file: Figure_2/Fig_2_Spatial_analysis_by_day_Python.ipynb
source_lines: 1-6
source_language: jupyter
validated: false
inputs:
  - "[[substrate|Substrate]]"
  - "[[enzyme|Enzyme]]"
outputs:
  - "[[rate|Rate]]"
---

# RMM

## Pseudocode
_TODO: describe algorithm_

## Original Code
```jupyter
def RMM(Substrate,Enzyme):
    Vmax = 24.895
    K    = 1.595
    Rate = Enzyme*Vmax/(K+ Enzyme)
    
    return Rate
```