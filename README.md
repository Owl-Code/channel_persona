# Channel Persona

A comprehensive, modular system for building complex AI personas and narrative orchestration with support for multiple orchestration architectures.

## Quick Start

Choose your orchestration type:

Mix and match different components to create a pseudo system prompt for you Channel persona or introduction.

example is hybrid_persona.json

## Project Structure

```
channel_persona/
├── README.md                           # This file
├── ORCHESTRATION_GUIDE.md              # Detailed comparison of orchestration systems
├── persona_introductions/              # Modular persona system
│   ├── README.md                       # Persona system documentation
│   ├── Bprofile_223.txt                # Legacy BERT-RP profile (reference)
│   ├── persona_introduction            # Legacy WO profile (reference)
│   ├── base/
│   │   ├── system.json                 # WO: System authority
│   │   ├── format_directives.json      # WO: Screenplay formatting
│   │   ├── memory_system.json          # WO: Memory encoding/decoding
│   │   ├── orchestrator.json           # WO: Multi-layer roles
│   │   ├── core_systems.json           # WO: Processing systems
│   │   ├── user_template.json          # WO: User identity template
│   │   └── bert_rp/                    # BERT-RP modular components
│   │       ├── framework.json
│   │       ├── perspective_rules.json
│   │       ├── hierarchy.json
│   │       ├── user_state_template.json
│   │       ├── dialogue_formatting.json
│   │       └── operational_flow.json
│   └── examples/
│       ├── default_persona.json
│       ├── hybrid_persona.json
│       └── bert_rp/          
│           └── default_bert_rp_persona.json
└── .git/                               # Version control
```
