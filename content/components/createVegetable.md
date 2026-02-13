---
name: createVegetable
source_tool: "[[hdoro_gororobas]]"
source_file: next-version-experiments/006-effect-schema-and-arbitraries.ts
source_lines: 126-139
source_language: typescript
validated: false
inputs:
  - "[[scientific_name|scientific-name]]"
  - "[[origin|origin]]"
  - "[[gender|gender]]"
outputs:
  - "[[vegetable|vegetable]]"
---

# createVegetable

## Pseudocode
_TODO: describe algorithm_

## Original Code
```typescript
function createVegetable(vegetable: typeof VegetableCreation.Type) {
	const initialDoc = new LoroDoc()
	const loroBlob = initialDoc.export({ mode: 'snapshot' })
	insertVegetable.run({
		$loro_crdt: loroBlob,
		$handle: vegetable.handle,
		$scientific_names: JSON.stringify(vegetable.scientific_names),
		$common_names: JSON.stringify(vegetable.common_names),
		$content: JSON.stringify(vegetable.content),
		$origin: vegetable.origin,
		$gender: vegetable.gender,
	})
}
```