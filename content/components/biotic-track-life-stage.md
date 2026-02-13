---
name: biotic-track-life-stage
source_tool: "[[blasbenito_palaeofiremodeling]]"
source_file: PalaeoFireModel_R.nlogo
source_lines: 948-966
source_language: netlogo
validated: false
inputs:
  - "[[vegetation_traits_current_age|vegetation-traits-current-age]]"
  - "[[vegetation_traits_sexual_maturity_age|vegetation-traits-sexual-maturity-age]]"
outputs:
  - "[[vegetation_life_stage|vegetation-life-stage]]"
---

# biotic-track-life-stage

## Pseudocode
_TODO: describe algorithm_

## Original Code
```netlogo
to biotic-track-life-stage

  ;IF AGE IS 0
  ifelse vegetation-traits-current-age = 0

  ;IS SEED
  [set vegetation-life-stage "seed"]

  ;NOT SEED
  [
    ifelse vegetation-traits-current-age < vegetation-traits-sexual-maturity-age

    ;IS SEEDLING
    [set vegetation-life-stage "seedling"]

    ;IS ADULT
    [set vegetation-life-stage "adult"]
  ]
end
```