---
name: shannon_diversity
source_tool: "[[econetoolbox_ecologicalnetworksdynamics.jl]]"
source_file: src/Internals/measures/functioning.jl
source_lines: 167-171
source_language: julia
validated: false
inputs:
  - "[[num_of_species|num-of-species]]"
  - "[[relative_species_abundance|relative-species-abundance]]"
outputs:
  - "[[shannon_diversity|shannon-diversity]]"
assumes:
  - "[[all_species_in_community_represented_in_sample|all species in community represented in sample]]"
  - "[[species_sampleed_randomly|species sampleed randomly]]"
  - "[[individuals_are_independent_of_one_another|individuals are independent of one another]]"
---

# shannon_diversity

## Pseudocode
_TODO: describe algorithm_

## Original Code
```julia
function shannon_diversity(solution; threshold = 0, kwargs...)
    measure_on = extract_last_timesteps(solution; kwargs...)
    shan = shannon_diversity.(eachcol(measure_on); threshold)
    mean(shan)
end
```