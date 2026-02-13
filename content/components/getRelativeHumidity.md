---
name: getRelativeHumidity
source_tool: "[[hisafe_hisafe]]"
source_file: jar/cstability/src/context/EnvironmentRecord.java
source_lines: 127-132
source_language: java
validated: false
inputs:
  - "[[environment_record|environment-record]]"
outputs:
  - "[[relative_humidity|relative-humidity]]"
---

# getRelativeHumidity

## Pseudocode
_TODO: describe algorithm_

## Original Code
```java
public double getRelativeHumidity() throws Exception {
		if (Double.isNaN(relativeHumidity))
			throw new Exception ("EnvironmentRecord.getRelativeHumidity(), error, date: "+date+", relativeHumidity: NaN");
		return relativeHumidity;
	}
```