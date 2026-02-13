---
name: getpH
source_tool: "[[hisafe_hisafe]]"
source_file: jar/cstability/src/context/EnvironmentRecord.java
source_lines: 121-126
source_language: java
validated: false
inputs:
  - "[[environment_record|environment-record]]"
outputs:
  - "[[ph|pH]]"
---

# getpH

## Pseudocode
_TODO: describe algorithm_

## Original Code
```java
public double getpH() throws Exception {
		if (Double.isNaN(pH))
			throw new Exception ("EnvironmentRecord.getpH(), error, date: "+date+", pH: NaN");
		return pH;
	}
```