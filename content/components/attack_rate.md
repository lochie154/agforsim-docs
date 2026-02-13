---
name: attack_rate
source_tool: "[[econetoolbox_ecologicalnetworksdynamics.jl]]"
source_file: src/Internals/inputs/functional_response.jl
source_lines: 654-665
source_language: julia
validated: false
inputs:
  - "[[food_web|food-web]]"
  - "[[body_mass|body-mass]]"
outputs:
  - "[[attack_rate|attack-rate]]"
assumes:
  - "[[consumers_always_mobile|consumers always mobile]]"
  - "[[producers_always_sessile|producers always sessile]]"
---

# attack_rate

## Pseudocode
_TODO: describe algorithm_

## Original Code
```julia
function attack_rate(network::EcologicalNetwork)
    S = richness(network)
    aᵣ = spzeros(Float64, S, S)
    M = network.M # vector of species body mass
    A = get_trophic_adjacency(network)
    # Define sessile species as producers, consumers are always mobile
    # This assumption could be changed in the future
    mobility = map(i -> !isproducer(i, A), 1:S) # 0 = sessile, 1 = mobile
    predator, prey = findnz(A)
    for (i, j) in zip(predator, prey)
        aᵣ[i, j] = attack_rate(i, j, M, mobility)
    end
```