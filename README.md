# Persona Introductions System

A modular architecture for defining complex AI personas with reusable components and multiple persona variants.

## Directory Structure

```
persona_introductions/
├── README.md                           # This file
├── base/                               # Base modular components
│   ├── system.json                     # Core system authority and version
│   ├── format_directives.json          # Screenplay markup and language principles
│   ├── memory_system.json              # Encoding/decoding and storage for interactions
│   ├── orchestrator.json               # Root system, society, companion, and user roles
│   ├── core_systems.json               # Processing, stack, and gravity definitions
│   └── user_template.json              # User identity, abilities, personality, and assets
├── examples/                           # Complete persona compositions
│   └── default_persona.json            # Full example combining all modules
└── [future persona variants]/          # Additional personas inherit and override base
```

## Modular Components

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

## Creating a New Persona

### Option 1: Use Base Components + Customization
1. Create a new directory: `persona_introductions/your_persona_name/`
2. Copy or reference the base components
3. Override specific sections as needed

Example structure:
```
persona_introductions/
├── base/                    # Shared base
├── examples/default_persona.json
├── your_persona/
│   ├── personality.json     # Override user_template.json with custom traits
│   ├── memory_system.json   # Custom memory encoding if needed
│   └── assets.json          # Custom estate and devices
```

### Option 2: Create Full Persona JSON
Create a complete persona file in `examples/` that includes all modules:

```json
{
  "persona": {
    "name": "Your Persona Name",
    "version": "1.0"
  },
  "system": { /* system config */ },
  "format_directives": { /* format rules */ },
  "memory_system": { /* memory config */ },
  "orchestrator": { /* role definitions */ },
  "core_systems": { /* processing systems */ },
  "assets": { /* user identity and assets */ }
}
```

## Persona Composition Best Practices

### 1. **Inheritance and Overrides**
- Base components should be minimal, authoritative, and rarely changed
- Each persona can override specific sections while inheriting others
- Document any deviations from base in persona-specific README

### 2. **NPC Management**
- Leverage the `orchestrator.branch_society` to define persona-specific NPCs
- Each NPC should have distinct dialogue patterns matching format_directives
- Use memory_system to track NPC evolution and state changes

### 3. **Asset Configuration**
- Customize estate (HOMIE) floors and rooms per persona
- Define unique devices or pack members if persona requires
- Keep device directives consistent across variants

### 4. **Memory Scaling**
- For long-running interactions, adjust step_counter and recall windows
- Consider persona-specific encoding mappings if they have unique agent types

### 5. **Orchestrator Customization**
- Dominate domains can be persona-specific (e.g., hacker persona might emphasize networks)
- Root system directives can be modified for different world types
- Society branch NPCs can be filtered per persona context

## Example Use Cases

### Use Case 1: Simple Character Variant
Create a persona that inherits all base systems but customizes user identity:
- Copy base/ components as-is
- Create custom user_template.json with different aesthetics and abilities
- Compose into examples/character_variant.json

### Use Case 2: Multiple Worlds
Create personas for different narrative worlds:
- Shared base system, format_directives, memory_system
- Orchestrator customized for each world's physics/politics
- Each persona gets world-specific root_system and branch_society

### Use Case 3: Team of Personas
Multiple personas that interact with each other:
- Shared orchestrator and core_systems
- Individual user_template.json and asset configurations
- Memory_system can reference each other via agent mappings

## Integration Points

### Loading a Persona
When instantiating a persona, merge components in this order:
1. Load base/ components (system, core_systems)
2. Load persona-specific overrides
3. Load format_directives and memory_system
4. Load orchestrator with persona-specific role definitions
5. Load user template with custom identity and assets

### Persistence
- Serialize memory_system.storage to save interaction history
- Load persisted memory on persona restart
- Use step_counter to resume from last known state

### Extension
- Add new modules by creating additional JSON files following the same pattern
- Register new modules in persona composition
- Document new modules in this README

## Customization Tips

### For Performance
- Reduce `memory_system.recall.distant` window for faster pattern matching
- Limit `orchestrator.branch_society.entities.npcs` to active characters
- Cache frequently accessed orchestrator configs

### For Narrative Quality
- Expand `format_directives.language_principles` with persona-specific nuances
- Create persona-specific emoji/tone mappings in format_directives
- Customize `orchestrator.root_system.drivers` for desired narrative pacing

### For Complexity
- Add new agent types to `memory_system.encoder.mappings.agents`
- Extend orchestrator roles (add mediator, judge, trickster, etc.)
- Create modular "ability_system.json" for complex power interactions

## Version History

- **v1.0**: Initial modular system with 6 base components
  - System, Format Directives, Memory System, Orchestrator, Core Systems, User Template
  - Example default_persona.json demonstrating full composition

---

**Last Updated:** February 23, 2026
