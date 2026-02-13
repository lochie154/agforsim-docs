---
name: Make_B
source_tool: "[[cirtwill_etal_2019]]"
source_file: simulation_example.R
source_lines: 31-48
source_language: r
validated: false
inputs:
  - "[[a|A]]"
  - "[[n_samples|n_samples]]"
outputs:
  - "[[result|result]]"
---

# Make_B

## Pseudocode
_TODO: describe algorithm_

## Mathematical Form
_TODO: add equations_

## Scales
- Temporal: unknown
- Spatial: unknown

## Original Code
```r
Make_B<-function(A,n_samples){
	B=matrix(nrow=nrow(A),ncol=ncol(A))
	for(plant in 1:nrow(A)){
		for(galler in 1:ncol(A)){
			process=runif(1) # Choose a random process uncertainty for each interaction
			cooccur=round(runif(n=1,min=0,max=n_samples))
			# Assuming the interaction was feasible, how often would it be observed based on the number of co-occurrences?
			n_local_occurrances=rbinom(1,cooccur,process)
			# If the interaction was feasible and occurred at least once, it is included in B
			if(A[plant,galler]==1 && n_local_occurrances>0){
				B[plant,galler]=1
			} else {
				B[plant,galler]=0
			}
		}
	}
	return(B)
}
```