# Ensemble Interface

An ensemble is a higher-level object that:

- accepts a list of models (all exposing the standard interface)
- prepares all models with a shared config
- runs all models
- aggregates their outputs via some rule (average, weighted average, rule-based, etc.)

Use this note to define:

- common aggregation schemes
- how to handle conflicting outputs
- how to represent uncertainty or disagreement between models
