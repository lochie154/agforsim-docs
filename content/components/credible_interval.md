---
name: credible_interval
source_tool: "[[cirtwill_etal_2019]]"
source_file: R_code.R
source_lines: 57-63
source_language: r
validated: false
inputs:
  - "[[pars|pars]]"
  - "[[p_lower|p_lower]]"
  - "[[p_upper|p_upper]]"
outputs:
  - "[[result|result]]"
---

# credible_interval

## Pseudocode
_TODO: describe algorithm_

## Mathematical Form
_TODO: add equations_

## Scales
- Temporal: unknown
- Spatial: unknown

## Original Code
```r
credible_interval<-function(pars,p_lower,p_upper){
  alpha=pars[[1]]
  beta=pars[[2]]
  lowCI=qbeta(p=p_lower,shape1=alpha,shape2=beta)
  highCI=qbeta(p=p_upper,shape1=alpha,shape2=beta)
  return(c(lowCI,highCI))
}
```