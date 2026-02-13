---
name: homogeneous_preference
source_tool: "[[econetoolbox_ecologicalnetworksdynamics.jl]]"
source_file: src/Internals/inputs/functional_response.jl
source_lines: 86-93
source_language: julia
validated: false
inputs:
  - "[[food_web|food-web]]"
outputs:
  - "[[food_preferences|food-preferences]]"
---

# homogeneous_preference

## Pseudocode
_TODO: describe algorithm_

## Original Code
```julia
function homogeneous_preference(net::EcologicalNetwork)
    S = richness(net)
    num_resource = number_of_resource(net) # num_resource[i] = nb. of resource(s) of i
    A = get_trophic_adjacency(net)
    ω = spzeros(S, S)
    for (i, j, _) in zip(findnz(A)...)
        ω[i, j] = 1 / num_resource[i]
    end
```