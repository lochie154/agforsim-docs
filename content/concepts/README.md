# Concepts

This directory contains concept notes that form the semantic layer of AGFORSIM.

## Types

- **input** - Data required by components
- **output** - Data produced by components  
- **assumption** - Constraints or simplifications made by components

## Sources

- **code_extraction** - Derived from scanned codebases
- **indigenous_knowledge** - Traditional ecological knowledge
- **permaculture** - Permaculture design principles
- **traditional_ecological_knowledge** - TEK from various sources

## Usage

Concepts appear as wikilinks in component frontmatter:

```yaml
inputs:
  - "[[body_mass|body_mass]]"
outputs:
  - "[[attack_rate_matrix|attack_rate_matrix]]"
assumes:
  - "[[consumers_always_mobile|consumers always mobile]]"
```

In the Obsidian graph, concepts become hub nodes connecting components that share them.
