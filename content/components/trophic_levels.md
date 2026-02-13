---
name: trophic_levels
source_tool: "[[econetoolbox_ecologicalnetworksdynamics.jl]]"
source_file: src/Internals/measures/structure.jl
source_lines: 251-261
source_language: julia
validated: false
inputs:
  - "[[food_web|food-web]]"
outputs:
  - "[[trophic_levels|trophic-levels]]"
assumes:
  - "[[food_web_matrix_is_invertible|food web matrix is invertible]]"
---

# trophic_levels

## Pseudocode
_TODO: describe algorithm_

## Original Code
```julia
function trophic_levels(A::AbstractMatrix)
    A = Matrix(A) # Ensure A is dense for inversion.
    S = size(A, 1) # Species richness.
    out_degree = sum(A; dims = 2)
    D = -(A ./ out_degree) # Diet matrix.
    D[isnan.(D)] .= 0.0
    D[diagind(D)] .= 1.0 .- D[diagind(D)]
    # Solve with the inverse matrix.
    inverse = iszero(det(D)) ? pinv : inv
    inverse(D) * ones(S)
end
```