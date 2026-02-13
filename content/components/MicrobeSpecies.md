---
name: MicrobeSpecies
source_tool: "[[hisafe_hisafe]]"
source_file: jar/cstability/src/parameter/MicrobeSpecies.java
source_lines: 74-78
source_language: java
validated: false
inputs:
  - "[[signature|signature]]"
  - "[[enzyme_production|enzyme-production]]"
  - "[[assimilation|assimilation]]"
outputs:
  - "[[microbe|microbe]]"
assumes:
  - "[[a_microbe_is_made_from_only_a_signature|a microbe is made from only a signature]]"
  - "[[enzyme_production_and_assimilation|enzyme production and assimilation]]"
---

# MicrobeSpecies

## Pseudocode
_TODO: describe algorithm_

## Original Code
```java
public MicrobeSpecies() {
		signatureMap = new HashMap<>();
		enzymeProductionMap = new HashMap<String, Function>();
		assimilationMap = new HashMap<>();
	}
```