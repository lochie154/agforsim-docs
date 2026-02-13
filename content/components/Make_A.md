---
name: Make_A
source_tool: "[[cirtwill_etal_2019]]"
source_file: simulation_example.R
source_lines: 9-23
source_language: r
validated: false
inputs:
  - "[[n_plants|n_plants]]"
  - "[[n_gallers|n_gallers]]"
  - "[[connectance|connectance]]"
outputs:
  - "[[result|result]]"
---

# Make_A

## Pseudocode
_TODO: describe algorithm_

## Mathematical Form
_TODO: add equations_

## Scales
- Temporal: unknown
- Spatial: unknown

## Original Code
```r
Make_A<-function(n_plants,n_gallers,connectance){
	# Randomly assign links among species 
	links=c(rep(1,connectance*n_plants*n_gallers),rep(0,(1-connectance)*n_plants*n_gallers))
	# Create a matrix with links randomly assigned to give our desired connectance
	A=matrix(nrow=n_plants,ncol=n_gallers,data=0)
	# At this stage, all plants and gallers must have at least one interaction
	zero_r=length(which(rowSums(A)==0))
	zero_c=length(which(colSums(A)==0))
	while(zero_r+zero_c>0){
		A=matrix(nrow=n_plants,ncol=n_gallers,data=sample(links,replace=FALSE))
		zero_r=length(which(rowSums(A)==0))
		zero_c=length(which(colSums(A)==0))
	}	
	return(A)
}
```