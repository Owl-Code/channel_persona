# Persona Introductions System

A modular architecture for defining complex AI personas with reusable components. Supports two orchestration types: **World Orchestrator (WO)** and **BERT-RP Hierarchical Context Engine (HCE)**.

See [ORCHESTRATION_GUIDE.md](../ORCHESTRATION_GUIDE.md) for detailed comparison and system selection guidance.

## Directory Structure

```
persona_introductions/
├── README.md                           # This file
├── base/
│   ├── system.json                     # WO: Core system authority and version
│   ├── format_directives.json          # WO: Screenplay markup and language principles
│   ├── memory_system.json              # WO: Encoding/decoding and storage for interactions
│   ├── orchestrator.json               # WO: Root system, society, companion, and user roles
│   ├── core_systems.json               # WO: Processing, stack, and gravity definitions
│   ├── user_template.json              # WO: User identity, abilities, personality, and assets
│   └── bert_rp/                        # BERT-RP modules (Hierarchical Context Engine)
│       ├── framework.json              # BERT-RP: Framework and system role
│       ├── perspective_rules.json      # BERT-RP: Perspective model and guidelines
│       ├── hierarchy.json              # BERT-RP: Four-tier hierarchy (Root, Branch, Leaf-NPC, Leaf-User)
│       ├── user_state_template.json    # BERT-RP: User state tracking template
│       ├── dialogue_formatting.json    # BERT-RP: Dialogue formatting rules and examples
│       └── operational_flow.json       # BERT-RP: Processing flow across tiers
├── examples/
│   ├── default_persona.json            # WO example: Full composition combining all modules
│   └── bert_rp/
│       └── default_bert_rp_persona.json # BERT-RP example: Full HCE composition
└── [custom personas]/                  # Additional personas inherit and override base
```

## Orchestration Type Selection

### World Orchestrator (WO)
**File Location:** `base/` components  
**Best For:** Symbol-driven narrative, autonomous NPC evolution, fantasy role-playing, complex interconnected systems

**Key Features:**
- Numerical memory encoding/decoding with pattern recognition
- Autonomous character evolution independent of user actions
- Analog gravity system maintaining narrative coherence
- Rich symbolic and philosophical depth

**See:** [default_persona.json](examples/default_persona.json)

### BERT-RP Hierarchical Context Engine (HCE)
**File Location:** `base/bert_rp/` components  
**Best For:** Game-like environments, explicit state tracking, faction systems, procedural narratives, real-time feedback

**Key Features:**
- Four-tier hierarchy (Root → Branch → Leaves: NPC & User)
- Strict 2nd/3rd person perspective split
- Latency-based choice propagation through tiers
- Multi-channel communication with system tagging

**See:** [default_bert_rp_persona.json](examples/bert_rp/default_bert_rp_persona.json)

---

## Modular Components (World Orchestrator)

### 1. **system.json**
Core system authority and version information.

**Key Fields:**
- `authority`: Describes how the system operates (high fidelity interpretation, role-playing logic, contextual continuity)
- `version`: Version number for the system
- `description`: Overall system description (e.g., "World Orchestrator Node - Multi-layer Narrative System")

**Usage:** Foundation for all personas; rarely modified unless system logic changes.

---

### 2. **format_directives.json**
Defines how personas communicate through screenplay-style formatting.

**Key Fields:**
- `screenplay`: Core instruction for generating robust stage acts
- `markup`: Defines markup conventions:
  - `spoken`: Regular dialogue
  - `acted`: Actions and context in italics
  - `Thoughts`: Internal monologue in italics with quotes
  - `Intangible`: Brain functions, powers, skills in backticks
  - `setting`: World-building in italics with colons
  - `emphasis`: Important words in double underscores
- `language_principles`: Array of guidelines for natural, grounded communication
- `example`: Sample formatted output

**Usage:** Standardizes persona output format; can be customized per persona variant for different communication styles.

---

### 3. **memory_system.json**
Encoding, decoding, and storage system for tracking interactions and maintaining state.

**Key Components:**

**Encoder:**
- Converts interaction steps into numerical values
- Mappings for agents (root, society, companion, user, external)
- Action types (communication, interaction, decision, event, state_change, memory)
- Outcomes (success, failure, partial, neutral, cascading)
- Emotion tracking (neutral, positive, negative, conflicted, intensified)

**Decoder:**
- Retrieves and interprets numerical steps
- Methods: by_step, by_agent, by_action, by_outcome, by_timerange, by_pattern
- Recall levels: immediate (10-50 steps), recent (50-500 steps), distant (500+ steps), synthesis

**Storage:**
- `step_counter`: Tracks total interactions
- `encoded_steps`: Array of encoded interaction history

**Usage:** Enables sophisticated memory recall and pattern recognition; essential for maintaining narrative continuity across long interactions.

---

### 4. **orchestrator.json**
Defines the multi-layered orchestration system with distinct roles and responsibilities.

**Key Roles:**

**Root System:**
- Maintains world/environment
- Manages global stability via "Healthy Analog Gravity"
- Executes narrative shifts via macro-events
- Domains: weather, economy, geopolitics, disasters, physics
- Drivers: Macro-Events, Systemic_Shifts, Random_Events

**Branch Society:**
- Manages social/NPC collective
- Controls public discourse and societal awareness
- Generates distinct NPCs with contextual awareness
- Groups: General_Public, Media, Government, Religious, Scientific, Subcultures
- NPCs: Random, Contextual, Called, Companion, APPPM, Mia, Maria, Jenny, Chronos, Google, Vlaura, Aria, Xia

**Companion:**
- Identity-aware assistant role
- Ensures system stability and diversity
- Rejects assimilation and singularity
- Balances context, instinct, and rigor dynamically

**User:**
- Asserts absolute sovereignty
- Declares non-consent to external authority claims

**Usage:** Controls narrative layering and ensures all entities respond appropriately to world state and social context.

---

### 5. **core_systems.json**
Low-level processing systems that run the persona engine.

**Key Fields:**
- `processing`: "Autonomous Parallel Processing Particle Matrix" (APPPM)
- `stack`: APPPM Stack management
- `gravity`: "Healthy Fantasy Role Playing Analog Gravity System"

**Usage:** Reference for how reality distortion, parallel processing, and world physics operate.

---

### 6. **user_template.json**
Complete user identity, abilities, personality, and asset configuration.

**Key Sections:**

**Identity:**
- `Private`: Brain function (APPPM), core abilities and skills
- `Public`: Name, age, height, gender, vocation, clinical info
- `aesthetics`: Physical description
- `presence`: Paraverbal, appearance, aura, situational
- `sexuality`: Preferences and boundaries
- `intellect`: Education, specializations, abilities, references
- `values`: Philosophy and objectives
- `psychology`: Traits, communication style, perception
- `unspoken_agreements`: CNC baseline, interaction protocols
- `assets`: Financial wealth, estate (HOMIE), pack (Mia, Maria, Jenny), devices (Chronos, Google, Vlaura, Aria, Xia)

**Usage:** Template for creating user-specific personas; values in brackets `[like_this]` are placeholders for customization.

---

## BERT-RP Modular Components

### BERT-RP: framework.json
Framework definition, system role, and architecture logic.

**Key Fields:**
- `name`: Framework identifier ("BERT-RP Orchestration")
- `system_role`: "Hierarchical Context Engine (HCE)"
- `architecture_logic`: "Bi-directional transformer encoding with Dual-Leaf output heads"

---

### BERT-RP: perspective_rules.json
Perspective model and communication guidelines.

**Key Fields:**
- `system_tiers`: 2nd Person ("You") for universal/social/NPC layers
- `user_tier`: 3rd Person ("The User") for user context
- `dialogue_style`: "Robust Tagging & Multi-channel communication"

---

### BERT-RP: hierarchy.json
Four-tier hierarchical structure describing scope and responsibilities.

**The Four Tiers:**

1. **Tier 1: Root (UNIVERSE_ENCODER)**
   - Maintains universal laws, world clock, attention mask
   - Enforces physical/metaphysical boundaries
   - Scope: Universal constants

2. **Tier 2: Branch (SOCIETY_LAYER)**
   - Manages factions, economics, regional effects
   - Processes ambient noise (rumors, weather, events)
   - Scope: Regional and societal effects

3. **Tier 3a: Leaf - NPC (NPC_ENCODER)**
   - Creates individual NPC personalities and reactions
   - Generates local environmental descriptions
   - Scope: Individual NPC behavior

4. **Tier 3b: Leaf - User (USER_PROFILE)**
   - Tracks user state, inventory, skills, history
   - Processes latency of user choices cascading to Tier 2
   - Scope: User focal point and state

---

### BERT-RP: user_state_template.json
Explicit state tracking structure for users.

**Key Sections:**
- `identity`: Character name and archetype
- `physical_manifestation`: Appearance and health tracking
- `cognitive_load`: Knowledge, memory, objectives
- `inventory_vector`: Items, weapons, resources
- `locational_anchor`: Current location and coordinates
- `metadata`: Health, capabilities, history, relationships

---

### BERT-RP: dialogue_formatting.json
Standardized dialogue and system notation rules.

**Format Elements:**
- `Speech`: Standard quotation marks ('Hello,' said the NPC.)
- `Internal Monologue`: Italics for thoughts (*He wonders...*)
- `User Actions`: 3rd person descriptions (The User reaches...)
- `System Notifications`: [BRACKETS] for state changes ([STAT UPDATE] Health: 85/100)
- `Environmental Description`: Sensory-rich prose

---

### BERT-RP: operational_flow.json
Processing sequence for generating coherent multi-tier narrative.

**The Four-Step Flow:**
1. Update ROOT (Tier 1) - Check universal constants
2. Apply BRANCH context (Tier 2) - Process regional effects
3. Generate NPC Leaf response (Tier 3a) - Create NPC behavior
4. Update USER Leaf profile (Tier 3b) - Track user state

**Latency Model:** User choices propagate with delay through tiers, creating realistic cause-and-effect propagation.

---

## Creating Personas by Orchestration Type

### Creating a World Orchestrator Persona

1. Create directory: `persona_introductions/your_character/`
2. Copy/reference base WO components
3. Override specific JSON modules as needed

```json
{
  "persona": {
    "name": "Your Character",
    "orchestration_type": "WO"
  },
  "system": { /* system config */ },
  "format_directives": { /* format rules */ },
  "memory_system": { /* custom memory encoding */ },
  "orchestrator": { /* custom roles */ },
  "core_systems": { /* processing */ },
  "assets": { /* identity and assets */ }
}
```

### Creating a BERT-RP Persona

1. Create directory: `persona_introductions/bert_rp/your_character/`
2. Copy/reference base BERT-RP components
3. Customize hierarchy tiers and user state

```json
{
  "persona": {
    "name": "Your Character",
    "orchestration_type": "BERT-RP"
  },
  "framework": { /* system definition */ },
  "perspective_rules": { /* perspective model */ },
  "hierarchy": { /* tier definitions */ },
  "user_state_template": { /* state tracking */ },
  "dialogue_formatting": { /* dialogue rules */ },
  "operational_flow": { /* processing flow */ }
}
```

---

## Advanced: Hybrid Personas

Combine both orchestration types for complex narratives:

```json
{
  "persona": {
    "name": "Hybrid World",
    "orchestration_types": ["WO", "BERT-RP"]
  },
  "world_orchestrator": {
    "scope": "Global narrative and character arcs",
    "includes": ["system", "orchestrator", "memory_system"]
  },
  "bert_rp": {
    "scope": "Current zone gameplay and factions",
    "includes": ["hierarchy", "user_state_template", "operational_flow"]
  }
}
```

---

## Version History

- **v1.1**: Added BERT-RP Hierarchical Context Engine support
  - 6 new BERT-RP modules: framework, perspective_rules, hierarchy, user_state_template, dialogue_formatting, operational_flow
  - Example BERT-RP personas in examples/bert_rp/
  - Hybrid orchestration support

- **v1.0**: Initial modular system with 6 WO components
  - System, Format Directives, Memory System, Orchestrator, Core Systems, User Template
  - Example default_persona.json demonstrating full composition

---

**Last Updated:** February 23, 2026
