## ADDED Requirements

### Requirement: Worked example uses orders API domain
The `#together` section SHALL use an orders API as the domain for all code examples, because orders map cleanly to pagination (list orders), expand (get order with line items), idempotency (create order), and error handling (validation failure).

#### Scenario: All four endpoint examples present
- **WHEN** a reader views `#together`
- **THEN** the section SHALL contain annotated code examples for: list orders with cursor pagination, get single order with `?expand=line_items`, create order with `Idempotency-Key` header, and RFC 9457 error response

### Requirement: Each endpoint example is annotated
Every code block in `#together` SHALL be preceded by a heading and a prose annotation explaining which pattern it demonstrates and why the design decision was made.

#### Scenario: List orders annotation references pagination section
- **WHEN** a reader views the list-orders example
- **THEN** the annotation SHALL reference `#pagination` and explain why cursor pagination is used for large datasets

#### Scenario: Create order annotation references idempotency
- **WHEN** a reader views the create-order example
- **THEN** the annotation SHALL explain the `Idempotency-Key` header and reference the versioning or auth pattern for context

#### Scenario: Error example uses RFC 9457 format
- **WHEN** a reader views the error response example
- **THEN** the JSON SHALL include `type`, `title`, `status`, `detail`, and `instance` fields matching RFC 9457

### Requirement: Section cross-links to individual pattern sections
The `#together` section SHALL include inline links back to the relevant pattern sections (`#errors`, `#pagination`, `#auth`, `#versioning`, `#n1`) so readers can drill into any pattern for detail.

#### Scenario: Cross-links are present
- **WHEN** a reader views each annotated example
- **THEN** at least one inline link to the relevant pattern section SHALL appear in the annotation prose

### Requirement: Section is anchored and TOC-linked
The `#together` section SHALL have `id="together"` and SHALL be listed in the grouped Table of Contents under the Synthesis group.

#### Scenario: Anchor link works
- **WHEN** a user navigates to `#together`
- **THEN** the browser SHALL scroll to the together section

#### Scenario: TOC entry present
- **WHEN** a user views the Table of Contents
- **THEN** an entry linking to `#together` SHALL appear in the Synthesis group
