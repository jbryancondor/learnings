## ADDED Requirements

### Requirement: Section contains exactly four decision scenarios
The `#scenarios` section SHALL contain exactly four closed-ended decision scenarios covering: pagination style choice, error format choice, versioning strategy choice, and N+1 solution choice.

#### Scenario: All four topics present
- **WHEN** a reader views `#scenarios`
- **THEN** four scenario items SHALL be visible covering pagination, errors, versioning, and N+1

### Requirement: Each scenario presents a concrete situation before the answer
Every scenario SHALL follow the pattern: situation description → answer → reasoning. The answer and reasoning SHALL be visible without requiring JavaScript — no show/hide toggle.

#### Scenario: Situation is concrete and specific
- **WHEN** a reader reads a scenario
- **THEN** the situation SHALL describe a specific engineering context (e.g., "You are building a feed API that serves 50M rows") not a generic description

#### Scenario: Answer is explicit and actionable
- **WHEN** a reader reads the answer portion of a scenario
- **THEN** the answer SHALL name a specific pattern or approach (e.g., "Use cursor pagination") without hedging

#### Scenario: Reasoning links back to a page section
- **WHEN** a reader reads the reasoning portion of a scenario
- **THEN** the reasoning SHALL include at least one link back to the relevant section on the page

### Requirement: Scenarios follow retrieval practice format
The layout SHALL visually distinguish the situation from the answer (e.g., using a callout or bordered box for the answer block) to encourage the reader to form their own answer before reading the provided one.

#### Scenario: Answer block is visually distinct
- **WHEN** a reader views a scenario
- **THEN** the answer block SHALL use a different visual treatment (callout, border, or background) from the situation text

### Requirement: Section is anchored and TOC-linked
The `#scenarios` section SHALL have `id="scenarios"` and SHALL be listed in the grouped Table of Contents under the Synthesis group.

#### Scenario: Anchor link works
- **WHEN** a user navigates to `#scenarios`
- **THEN** the browser SHALL scroll to the scenarios section

#### Scenario: TOC entry present
- **WHEN** a user views the Table of Contents
- **THEN** an entry linking to `#scenarios` SHALL appear in the Synthesis group
