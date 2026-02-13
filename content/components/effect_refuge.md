---
name: effect_refuge
source_tool: "[[econetoolbox_ecologicalnetworksdynamics.jl]]"
source_file: src/Internals/model/effect_nti.jl
source_lines: 28-42
source_language: julia
validated: false
inputs:
  - "[[attack_rate|attack-rate]]"
  - "[[biomass|biomass]]"
  - "[[refuge_network|refuge-network]]"
outputs:
  - "[[attack_rate|attack-rate]]"
assumes:
  - "[[refuge_reduces_attack_rate|refuge reduces attack rate]]"
  - "[[refuge_scales_with_biomass|refuge scales with biomass]]"
---

# effect_refuge

## Pseudocode
_TODO: describe algorithm_

## Original Code
```julia
function effect_refuge(aᵣ, B, network::MultiplexNetwork)
    r0 = network.layers[:refuge].intensity
    r0 > 0 || return aᵣ # r0 = 0 ⇒ no effect of refuge
    A_refuge = network.layers[:refuge].A
    n_links(A_refuge) > 0 || return aᵣ # no refuge links ⇒ no effect of refuge
    f_refuge = network.layers[:refuge].f
    S = richness(A_refuge)
    prey = preys(aᵣ)
    aᵣ_refuge = zeros(eltype(B), S, S)
    for i in prey
        providing_refuge = A_refuge[:, i] # species providing a refuge to 'prey'
        δaᵣ = r0 * sum(providing_refuge .* B)
        for j in aᵣ[:, i].nzind
            aᵣ_refuge[j, i] = f_refuge(aᵣ[j, i], δaᵣ)
        end
```