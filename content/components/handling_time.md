---
name: handling_time
source_tool: "[[econetoolbox_ecologicalnetworksdynamics.jl]]"
source_file: src/Internals/inputs/functional_response.jl
source_lines: 626-634
source_language: julia
validated: false
inputs:
  - "[[food_web|food-web]]"
  - "[[body_mass|body-mass]]"
outputs:
  - "[[handling_time|handling-time]]"
---

# handling_time

## Pseudocode
_TODO: describe algorithm_

## Original Code
```julia
function handling_time(network::EcologicalNetwork)
    S = richness(network)
    hₜ = spzeros(Float64, S, S)
    M = network.M # vector of species body mass
    A = get_trophic_adjacency(network)
    predator, prey = findnz(A)
    for (i, j) in zip(predator, prey)
        hₜ[i, j] = handling_time(i, j, M)
    end
```