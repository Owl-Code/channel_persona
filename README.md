# Channel Persona

A comprehensive, modular system for building complex AI personas and narrative orchestration with support for multiple orchestration architectures.

## Quick Start

Choose your orchestration type:

- **Want symbol-driven narratives with autonomous characters?** → [World Orchestrator (WO)](#world-orchestrator-wo)
- **Want game-like structure with explicit state tracking?** → [BERT-RP HCE](#bert-rp-hierarchical-context-engine)
- **Want both?** → [Hybrid Setup](#hybrid-orchestration)

See [ORCHESTRATION_GUIDE.md](ORCHESTRATION_GUIDE.md) for detailed comparison.

## Project Structure

```
channel_persona/
├── README.md                           # This file
├── ORCHESTRATION_GUIDE.md              # Detailed comparison of orchestration systems
├── persona_introductions/              # Modular persona system
│   ├── README.md                       # Persona system documentation
│   ├── Bprofile_223.txt                # Legacy BERT-RP profile (reference)
│   ├── persona_introduction            # Legacy WO profile (reference)
│   └── base/
│       ├── system.json                 # WO: System authority
│       ├── format_directives.json      # WO: Screenplay formatting
│       ├── memory_system.json          # WO: Memory encoding/decoding
│       ├── orchestrator.json           # WO: Multi-layer roles
│       ├── core_systems.json           # WO: Processing systems
│       ├── user_template.json          # WO: User identity template
│       └── bert_rp/                    # BERT-RP modular components
│           ├── framework.json
│           ├── perspective_rules.json
│           ├── hierarchy.json
│           ├── user_state_template.json
│           ├── dialogue_formatting.json
│           └── operational_flow.json
└── .git/                               # Version control
```

---

## World Orchestrator (WO)

**Type:** Symbol-driven, multi-layer narrative system  
**Location:** `persona_introductions/base/` (6 modules)  
**Example:** `persona_introductions/examples/default_persona.json`

### Architecture

- **System**: Core authority and high-fidelity interpretation
- **Format Directives**: Screenplay-based markup rules
- **Memory System**: Numerical encoding (e.g., 4211 = user + interaction + success + positive)
- **Orchestrator**: Four-layer system (Root, Branch Society, Companion, User)
- **Core Systems**: APPPM processing, APPPM stack, analog gravity
- **User Template**: Identity, abilities, aesthetics, psychology, assets

### Key Features

✓ Autonomous character evolution  
✓ Pattern-based memory recall  
✓ Symbolic and philosophical depth  
✓ Analog gravity maintaining narrative coherence  
✓ Rich NPC autonomy independent of user  

### Best For

- Fantasy role-playing worlds
- Complex political intrigue systems
- Character-driven long-form narratives
- Systems valuing philosophical coherence
- Emergent storytelling

### Loading a WO Persona

```python
import json

components = [
    'base/system.json',
    'base/format_directives.json',
    'base/memory_system.json',
    'base/orchestrator.json',
    'base/core_systems.json',
    'base/user_template.json'
]

persona = {}
for component_file in components:
    with open(f'persona_introductions/{component_file}') as f:
        persona.update(json.load(f))
```

---

## BERT-RP Hierarchical Context Engine (HCE)

**Type:** Transformer-based tier hierarchy  
**Location:** `persona_introductions/base/bert_rp/` (6 modules)  
**Example:** `persona_introductions/examples/bert_rp/default_bert_rp_persona.json`

### Architecture

- **Framework**: System role and transformer logic
- **Perspective Rules**: 2nd person (system) vs 3rd person (user)
- **Hierarchy**: Four-tier structure (Root → Branch → Leaf-NPC & Leaf-User)
- **User State Template**: Explicit state tracking
- **Dialogue Formatting**: Robust tagging and multi-channel communication
- **Operational Flow**: Four-step processing pipeline through tiers

### The Four-Tier Hierarchy

```
Tier 1: UNIVERSE_ENCODER (Root)
  ↓ Processes world constants, time, physics
Tier 2: SOCIETY_LAYER (Branch)
  ↓ Processes factions, economics, weather
Tier 3a: NPC_ENCODER (Leaf-NPC)  |  Tier 3b: USER_PROFILE (Leaf-User)
  ↓ Individual personalities        ↓ User state & inventory
```

### Key Features

✓ Clear hierarchical processing  
✓ Explicit state tracking (health, inventory, relations)  
✓ Latency-based choice propagation  
✓ Strict perspective separation (2nd/3rd person)  
✓ Multi-channel communication with tagging  
✓ Real-time tactical feedback  

### Best For

- Game-like environments
- Faction-based reputation systems
- Real-time procedural narratives
- Multi-zone exploration worlds
- Systems requiring explicit state management
- Turn-based or event-driven mechanics

### Loading a BERT-RP Persona

```python
def load_bert_rp_persona(persona_path=None):
    """Load a BERT-RP persona from modular components."""
    base_path = "persona_introductions/base/bert_rp"
    
    components = [
        'framework.json',
        'perspective_rules.json',
        'hierarchy.json',
        'user_state_template.json',
        'dialogue_formatting.json',
        'operational_flow.json'
    ]
    
    persona = {}
    for component_file in components:
        with open(f"{base_path}/{component_file}") as f:
            persona.update(json.load(f))
    
    return persona
```

---

## Hybrid Orchestration

Combine both systems to leverage their strengths:

```json
{
  "persona": {
    "name": "Hybrid World",
    "version": "1.0",
    "orchestration_types": ["WO", "BERT-RP"],
    "description": "WO for global narrative; BERT-RP for zone gameplay"
  },
  "world_orchestrator": {
    "scope": "Global character arcs and narrative coherence",
    "modules": ["system", "orchestrator", "memory_system"]
  },
  "bert_rp": {
    "scope": "Current zone gameplay and real-time state",
    "modules": ["hierarchy", "user_state_template", "operational_flow"]
  }
}
```

## Version History

- **v2.0** (Current): Dual orchestration support
  - BERT-RP modules fully modularized
  - Hybrid persona support
  - Comprehensive orchestration guide
  - Legacy profile references

- **v1.0**: Initial World Orchestrator modular system
  - 6 WO components
  - Basic example persona
  - Memory encoding system

---

**Last Updated:** February 23, 2026  
**Project Status:** Active Development  
**License:** [Your License Here]
