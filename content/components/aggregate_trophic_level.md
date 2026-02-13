---
name: aggregate_trophic_level
source_tool: "[[econetoolbox_ecologicalnetworksdynamics.jl]]"
source_file: src/Internals/measures/functioning.jl
source_lines: 496-502
source_language: julia
validated: false
inputs:
  - "[[op_name|op_name]]"
  - "[[aggregate_function|aggregate_function]]"
outputs:
  - "[[trophic_level|trophic-level]]"
assumes:
  - "[[species_have_discrete_trophic_levels|species have discrete trophic levels]]"
---

# aggregate_trophic_level

## Pseudocode
_TODO: describe algorithm_

## Original Code
```julia
function aggregate_trophic_level(op_name, aggregate_function)
    op_trophic_level = Symbol(op_name, :_trophic_level)
    if isnothing(aggregate_function)
        from_matrices_code = :()
    else
        from_matrices_code = from_matrices(op_name, aggregate_function)
    end
```