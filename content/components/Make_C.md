---
name: Make_C
source_tool: "[[cirtwill_etal_2019]]"
source_file: simulation_example.R
source_lines: 57-74
source_language: r
validated: false
inputs:
  - "[[b|B]]"
  - "[[n_samples|n_samples]]"
outputs:
  - "[[result|result]]"
---

# Make_C

## Pseudocode
_TODO: describe algorithm_

## Mathematical Form
_TODO: add equations_

## Scales
- Temporal: unknown
- Spatial: unknown

## Original Code
```r

Make_C<-function(B,n_samples){
	C=matrix(nrow=nrow(B),ncol=ncol(B))
	for(plant in 1:nrow(B)){
		for(galler in 1:ncol(B)){
			cooccur=round(runif(n=1,min=0,max=n_samples)) # Number of co-occurrences is a random integer
			detection=rbeta(1,2,10) # Intrinsic probability of detecting an interaction is uniformly distributed
			detections_if_occurring=rbinom(1,cooccur,detection) # Is the interaction detectable?
			# If the interaction occurred during sampling and is detectable in at least one sample, it is included in C
			if(B[plant,galler]==1 && detections_if_occurring>0){
				C[plant,galler]=1
			} else {
				C[plant,galler]=0
			}
		}
	}
	return(C)
}
```