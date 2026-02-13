---
name: calculateBelowgroundResources
source_tool: "[[pymanga_pymanga]]"
source_file: ResourceLib/BelowGround/Individual/OGSWithoutFeedback/OGSWithoutFeedback.py
source_lines: 75-86
source_language: python
validated: false
inputs:
  - "[[soil_salinity|soil-salinity]]"
  - "[[root_zone_cells|root-zone-cells]]"
  - "[[salinity_tolerance|salinity-tolerance]]"
outputs:
  - "[[belowground_resources|belowground-resources]]"
assumes:
  - "[[salinity_effect_linear|salinity effect linear]]"
  - "[[root_zone_salinity_averaged|root zone salinity averaged]]"
---

# calculateBelowgroundResources

## Pseudocode
_TODO: describe algorithm_

## Original Code
```python
def calculateBelowgroundResources(self):
        super().getCellSalinity()
        for plant_id in range(len(self._plant_constant_contribution)):
            ids = self._plant_cell_ids[plant_id]
            mean_salinity_for_plant = np.mean(self._salinity[ids])
            belowground_resource = (
                (self._plant_constant_contribution[plant_id] +
                 mean_salinity_for_plant *
                 self._plant_salinity_prefactor[plant_id]) /
                self._plant_constant_contribution[plant_id])
            self.belowground_resources.append(belowground_resource)
```