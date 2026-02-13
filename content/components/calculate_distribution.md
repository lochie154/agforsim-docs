---
name: calculate_distribution
source_tool: "[[cirtwill_etal_2019]]"
source_file: R_code.R
source_lines: 36-51
source_language: r
validated: false
inputs:
  - "[[pars|pars]]"
outputs:
  - "[[result|result]]"
---

# calculate_distribution

## Pseudocode
_TODO: describe algorithm_

## Mathematical Form
_TODO: add equations_

## Scales
- Temporal: unknown
- Spatial: unknown

## Original Code
```r
calculate_distribution<-function(pars){
  alpha=pars[[1]]
  beta=pars[[2]]
  # Mean
  mu_num=alpha
  mu_den=alpha+beta
  mu=mu_num/mu_den
  # Variance
  sig_num=alpha*beta
  den1=alpha+beta
  den2=den1**2
  sig_den=den1*den2
  sigma2=sig_num/sig_den

  return(c(mu,sigma2))
}
```