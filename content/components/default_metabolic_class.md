---
name: default_metabolic_class
source_tool: "[[econetoolbox_ecologicalnetworksdynamics.jl]]"
source_file: src/Internals/inputs/foodwebs.jl
source_lines: 436-440
source_language: julia
validated: false
inputs:
  - "[[food_web|food-web]]"
outputs:
  - "[[metabolic_class|metabolic-class]]"
---

# default_metabolic_class

## Pseudocode
_TODO: describe algorithm_

## Original Code
```julia
function default_metabolic_class(A)
    metabolic_class = repeat(["invertebrate"], richness(A))
    metabolic_class[producers(A)] .= "producer"
    metabolic_class
end
```