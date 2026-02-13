---
name: samples_for_threshold
source_tool: "[[cirtwill_etal_2019]]"
source_file: R_code.R
source_lines: 70-78
source_language: r
validated: false
inputs:
  - "[[threshold|threshold]]"
  - "[[confidence|confidence]]"
  - "[[pars|pars]]"
outputs:
  - "[[result|result]]"
---

# samples_for_threshold

## Pseudocode
_TODO: describe algorithm_

## Mathematical Form
_TODO: add equations_

## Scales
- Temporal: unknown
- Spatial: unknown

## Original Code
```r
samples_for_threshold<-function(threshold,confidence,pars){
  alpha=pars[[1]]
  beta=pars[[2]]
  n=seq(0,1000,1)
  k=0
  cdf=pbeta(threshold,shape1=alpha,shape2=beta+n)
  samples=length(which(cdf<confidence))
  return(samples)
}
```