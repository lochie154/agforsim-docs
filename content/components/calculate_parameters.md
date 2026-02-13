---
name: calculate_parameters
source_tool: "[[cirtwill_etal_2019]]"
source_file: R_code.R
source_lines: 4-16
source_language: r
validated: false
inputs:
  - "[[priordata|priordata]]"
  - "[[n|n]]"
  - "[[k|k]]"
outputs:
  - "[[result|result]]"
---

# calculate_parameters

## Pseudocode
_TODO: describe algorithm_

## Mathematical Form
_TODO: add equations_

## Scales
- Temporal: unknown
- Spatial: unknown

## Original Code
```r
calculate_parameters<-function(priordata,n,k){
  library(MASS)
  # Calculate prior parameters
  pars=fitdistr(x=priordata,"beta",start=list(shape1=1,shape2=1),lower=c(0,0))$estimate
  # The lower=c(0,0) prevents R from fitting invalid (negative) parameters
  alpha=pars[[1]]
  beta=pars[[2]]
  # Update parameters with data. If n=0 and k=0, no change.
  alpha_prime=alpha+k
  beta_prime=beta+n-k
  pars2=c(alpha_prime,beta_prime)
  return(pars2)
}
```