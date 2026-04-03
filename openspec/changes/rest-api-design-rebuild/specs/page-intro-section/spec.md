## ADDED Requirements

### Requirement: Prerequisites callout renders before page body
The page SHALL display a prerequisites callout as the first element inside `#intro`, listing the assumed knowledge (HTTP methods, JSON, client/server model) so readers can self-assess before continuing.

#### Scenario: Prerequisites callout present in DOM
- **WHEN** the page loads
- **THEN** a callout box with the heading "Prerequisites" SHALL appear inside `#intro` before any other content

#### Scenario: Prerequisites list is complete
- **WHEN** a reader inspects the prerequisites callout
- **THEN** it SHALL list at minimum: HTTP methods (GET/POST/PUT/PATCH/DELETE), JSON, and client/server model

### Requirement: REST definition paragraph is present
The page SHALL include a concise definition of REST (Representational State Transfer) inside `#intro` that explains the acronym and its architectural style origin.

#### Scenario: Definition text present
- **WHEN** a reader loads `#intro`
- **THEN** a paragraph defining REST SHALL be visible, referencing Roy Fielding's dissertation as the origin

### Requirement: HTTP methods table with Safe and Idempotent columns
The page SHALL render a table inside `#intro` listing the five primary HTTP methods (GET, POST, PUT, PATCH, DELETE) with columns: Method, Action, Safe (Yes/No), Idempotent (Yes/No), and common use.

#### Scenario: Table has correct structure
- **WHEN** the `#intro` section is rendered
- **THEN** a table SHALL appear with columns: Method, Action, Safe, Idempotent

#### Scenario: Safe and Idempotent values are correct
- **WHEN** a reader inspects the table
- **THEN** GET SHALL be marked Safe=Yes and Idempotent=Yes
- **THEN** POST SHALL be marked Safe=No and Idempotent=No
- **THEN** PUT SHALL be marked Safe=No and Idempotent=Yes
- **THEN** PATCH SHALL be marked Safe=No and Idempotent=No
- **THEN** DELETE SHALL be marked Safe=No and Idempotent=Yes

### Requirement: Idempotency definition callout
The page SHALL include a callout box inside `#intro` that defines idempotency in plain terms, explaining that calling the same operation multiple times produces the same result.

#### Scenario: Idempotency callout present
- **WHEN** a reader reaches the HTTP methods table
- **THEN** a callout SHALL appear nearby defining idempotency with a practical example (e.g., "DELETE /users/1 twice returns 404 the second time, not an error — the end state is the same")

### Requirement: Section is anchored and TOC-linked
The `#intro` section SHALL have `id="intro"` and SHALL be listed in the grouped Table of Contents under the Foundation group.

#### Scenario: Anchor link works
- **WHEN** a user navigates to `#intro`
- **THEN** the browser SHALL scroll to the intro section

#### Scenario: TOC entry present
- **WHEN** a user views the Table of Contents
- **THEN** an entry linking to `#intro` SHALL appear in the Foundation group
