# Orchestration Systems Guide

This project supports two distinct orchestration architectures. Choose based on your narrative needs and system design preferences.

## Quick Comparison

| Aspect | World Orchestrator (WO) | BERT-RP (Hierarchical Context Engine) |
|--------|------------------------|---------------------------------------|
| **Paradigm** | Symbol-driven multi-layer narrative | Transformer-based tier hierarchy |
| **Authority** | Single immutable authority center | Distributed tier-based context |
| **Narrative Depth** | Fantasy role-playing with analog gravity | Linear tier processing with latency |
| **Memory System** | Numerical encoding/decoding with patterns | State tracking across tiers |
| **Perspective** | Mixed (internal storytelling) | Strict 2nd/3rd person split |
| **NPC Generation** | Autonomous character evolution | Reactive hierarchy processing |
| **Best For** | Rich, interconnected fantasy worlds | Structured, game-like environments |
| **Complexity** | High symbolic depth | High procedural clarity |

---

## World Orchestrator (WO) System

### Location
```
persona_introductions/
├── base/
│   ├── system.json
│   ├── format_directives.json
│   ├── memory_system.json
│   ├── orchestrator.json
│   ├── core_systems.json
│   └── user_template.json
└── examples/
    └── default_persona.json
```

### Architecture
- **Root System**: Maintains world/environment integrity
- **Branch Society**: Manages social collective and NPC evolution
- **Companion**: Identity-aware assistant
- **User**: Soverign focal point

### Key Features
- **Memory Encoding**: Convert interactions to numerical values (e.g., 4211 = user + interaction + success + positive)
- **Pattern Recognition**: Recall history via methods like `by_agent`, `by_outcome`, `by_pattern`
- **Autonomous NPCs**: Characters evolve independently based on values and interactions
- **Analog Gravity**: Metaphysical stability system maintaining narrative continuity
- **Symbolic Depth**: Rich psychological and philosophical framework

### Use Cases
- Complex fantasy worlds with political intrigue
- Character-driven narratives with deep NPC autonomy
- Systems requiring philosophical coherence
- Long-form storytelling with emergent complexity

### Example Persona
[default_persona.json](examples/default_persona.json) - Full composition with all modules

---

## BERT-RP Hierarchical Context Engine (HCE)

### Location
```
persona_introductions/
├── base/bert_rp/
│   ├── framework.json
│   ├── perspective_rules.json
│   ├── hierarchy.json
│   ├── user_state_template.json
│   ├── dialogue_formatting.json
│   └── operational_flow.json
└── examples/bert_rp/
    └── default_bert_rp_persona.json
```

### Architecture

**Four-Tier Hierarchy:**

1. **Tier 1: Root (UNIVERSE_ENCODER)**
   - Perspective: 2nd Person ("You")
   - Maintains universal laws, world clock, attention mask
   - Enforces physical/metaphysical boundaries

2. **Tier 2: Branch (SOCIETY_LAYER)**
   - Perspective: 2nd Person ("You")
   - Processes regional effects, factions, economics
   - Generates ambient noise (rumors, weather, events)

3. **Tier 3a: Leaf - NPC (NPC_ENCODER)**
   - Perspective: 2nd Person ("You")
   - Creates individual NPC personalities and reactions
   - Generates local environmental descriptions

4. **Tier 3b: Leaf - User (USER_PROFILE)**
   - Perspective: 3rd Person ("The User")
   - Tracks user state, inventory, skills, history
   - Processes latency of user choices on Branch layer

### Key Features
- **Bi-directional Processing**: Information flows up from user actions, down from universal rules
- **Latency Model**: User choices propagate with delay: User → Tier 3b → Tier 2 → Tier 1
- **Perspective Split**: System tiers use 2nd person; user context uses 3rd person
- **Structured State**: Explicit tracking of health, inventory, relationships, objectives
- **Multi-channel Communication**: Simultaneous narrative streams with clear tagging

### Dialogue Format
```
Vex narrows his eyes. 'I don't recognize your face,' he says, while *wondering if he should pull his blaster.* 
The User remains silent, hand hovering near their belt. 
[ALERT] Vex is evaluating your threat level. 
[NPC STATE] Vex: Suspicious (rep: -15).
```

### Use Cases
- Game-like environments with clear game states
- Multiple concurrent quest lines
- Faction-based reputation systems
- Real-time tactical scenarios
- Systems requiring explicit state tracking
- Procedurally-generated worlds

### Example Persona
[default_bert_rp_persona.json](examples/bert_rp/default_bert_rp_persona.json) - Full BERT-RP composition

---

## Choosing an Orchestration System

### Choose **World Orchestrator** if you want:
✓ Deep philosophical coherence  
✓ Autonomous character evolution  
✓ Symbolic/metaphorical representations  
✓ Complex interconnected systems  
✓ Narrative-first approach  
✓ Character agency independent of user  

### Choose **BERT-RP** if you want:
✓ Clear gamified structure  
✓ Explicit state tracking  
✓ Hierarchical tier-based processing  
✓ Procedural predictability  
✓ Multi-faction reputation systems  
✓ Real-time tactical feedback  

### Choose **Both** if you want:
✓ Flexible architecture supporting multiple narrative styles  
✓ World-building at WO level with BERT-RP mechanics for specific zones  
✓ Story-driven (WO) with gameplay elements (BERT-RP)  

---

## Project Structure

```
channel_persona/
├── README.md                           # This file
├── persona_introductions/
│   ├── README.md                       # Modular components guide
│   ├── base/
│   │   ├── system.json                 # WO: Core system
│   │   ├── format_directives.json      # WO: Screenplay rules
│   │   ├── memory_system.json          # WO: Encoding/decoding
│   │   ├── orchestrator.json           # WO: Multi-layer roles
│   │   ├── core_systems.json           # WO: Processing systems
│   │   ├── user_template.json          # WO: User identity
│   │   └── bert_rp/                    # BERT-RP modules
│   │       ├── framework.json          # BERT-RP system definition
│   │       ├── perspective_rules.json  # BERT-RP perspective model
│   │       ├── hierarchy.json          # BERT-RP four-tier structure
│   │       ├── user_state_template.json # BERT-RP user state
│   │       ├── dialogue_formatting.json # BERT-RP dialogue rules
│   │       └── operational_flow.json   # BERT-RP processing flow
│   └── examples/
│       ├── default_persona.json        # WO example
│       └── bert_rp/
│           └── default_bert_rp_persona.json  # BERT-RP example
└── [other project files]
```

---

## Integration with Your System

### Loading a World Orchestrator Persona
```python
import json

# Load base components
with open('base/system.json') as f:
    system = json.load(f)
with open('base/format_directives.json') as f:
    format_directives = json.load(f)
with open('base/memory_system.json') as f:
    memory_system = json.load(f)
with open('base/orchestrator.json') as f:
    orchestrator = json.load(f)
with open('base/core_systems.json') as f:
    core_systems = json.load(f)
with open('base/user_template.json') as f:
    user = json.load(f)

# Compose full persona
persona = {
    **system,
    **format_directives,
    **memory_system,
    **orchestrator,
    **core_systems,
    "assets": user
}
```

### Loading a BERT-RP Persona
```python
import json

# Load base components
with open('base/bert_rp/framework.json') as f:
    framework = json.load(f)
with open('base/bert_rp/perspective_rules.json') as f:
    perspective_rules = json.load(f)
with open('base/bert_rp/hierarchy.json') as f:
    hierarchy = json.load(f)
with open('base/bert_rp/user_state_template.json') as f:
    user_state = json.load(f)
with open('base/bert_rp/dialogue_formatting.json') as f:
    dialogue = json.load(f)
with open('base/bert_rp/operational_flow.json') as f:
    operational_flow = json.load(f)

# Compose full persona
persona = {
    **framework,
    **perspective_rules,
    **hierarchy,
    "user_state_template": user_state,
    **dialogue,
    **operational_flow
}
```

---

## Creating a Hybrid Persona

You can combine both systems for complex narratives:

```json
{
  "persona": {
    "name": "Hybrid Narrative",
    "version": "1.0",
    "orchestration_types": ["WO", "BERT-RP"]
  },
  "world_orchestrator": {
    "scope": "Global narrative, character arcs, philosophical coherence",
    "modules": ["system", "orchestrator", "memory_system"]
  },
  "bert_rp": {
    "scope": "Current zone gameplay, faction mechanics, real-time state",
    "modules": ["hierarchy", "user_state_template", "operational_flow"]
  }
}
```

---

## Performance Considerations

### World Orchestrator
- **Memory Usage**: Moderate to high (depends on encoded_steps history)
- **Processing**: Recursive pattern matching can be CPU-intensive
- **Scalability**: Best for single-POV, multi-layer narratives

### BERT-RP
- **Memory Usage**: Moderate (explicit state tracking)
- **Processing**: Linear tier processing, very predictable
- **Scalability**: Excellent for multi-zone, multi-faction worlds

---

## Advanced Customization

### Adding New Coordination Layers to WO
Extend `orchestrator.json` with new roles beyond Root/Branch/Companion/User.

### Extended Tiers for BERT-RP
Add sub-tiers under existing hierarchy for more granular control (e.g., Tier 2.5 for local politics).

### Custom Memory Systems
Adapt WO's memory_system.encoder for domain-specific mappings (e.g., magic-based encoding).

### Perspective Variations
Modify BERT-RP's perspective_rules for alternate narratives (e.g., 1st person companion, 2nd person for user).

---

**Last Updated:** February 23, 2026
