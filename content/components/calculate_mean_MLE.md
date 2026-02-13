---
name: calculate_mean_MLE
source_tool: "[[cirtwill_etal_2019]]"
source_file: R_code.R
source_lines: 21-32
source_language: r
validated: false
inputs:
  - "[[priordata|priordata]]"
  - "[[n|n]]"
  - "[[k|k]]"
outputs:
  - "[[result|result]]"
---

# calculate_mean_MLE

## Pseudocode
_TODO: describe algorithm_

## Mathematical Form
_TODO: add equations_

## Scales
- Temporal: unknown
- Spatial: unknown

## Original Code
```r
calculate_mean_MLE<-function(priordata,n,k){
  library(MASS)
  pars=fitdistr(x=priordata,"beta",start=list(shape1=1,shape2=1),lower=c(0,0))$estimate
  # The lower=c(0,0) prevents R from fitting invalid (negative) parameters
  alpha=pars[[1]]
  beta=pars[[2]]

  numerator=alpha+k
  denominator=alpha+beta+n
  MLE=numerator/denominator
  return(MLE)
}
```