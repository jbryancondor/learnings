## ADDED Requirements

### Requirement: Tab container has role="tablist"
The element wrapping all tab buttons in the benchmark section SHALL have `role="tablist"` and an `aria-label` describing the tab group (e.g., `aria-label="Benchmark categories"`).

#### Scenario: tablist role present
- **WHEN** a screen reader encounters the tab container
- **THEN** it SHALL announce the element as a tablist with its label

### Requirement: Each tab button has correct ARIA attributes
Every tab button SHALL have: `role="tab"`, a unique `id` (e.g., `id="tab-bm-styles"`), `aria-selected="true"` for the active tab and `aria-selected="false"` for inactive tabs, `aria-controls` pointing to its panel's `id`, and `tabindex="-1"` on all inactive tabs.

#### Scenario: Active tab attributes correct
- **WHEN** a tab is active
- **THEN** it SHALL have `aria-selected="true"` and SHALL NOT have `tabindex="-1"`

#### Scenario: Inactive tab attributes correct
- **WHEN** a tab is inactive
- **THEN** it SHALL have `aria-selected="false"` and `tabindex="-1"`

### Requirement: Each tab panel has correct ARIA attributes
Every tab panel element SHALL have: `role="tabpanel"`, a unique `id` matching its tab button's `aria-controls`, and `aria-labelledby` pointing to its tab button's `id`.

#### Scenario: Panel labelled by its tab
- **WHEN** a screen reader enters a tab panel
- **THEN** it SHALL announce the panel's label using the associated tab button text

### Requirement: Keyboard navigation follows WAI-ARIA tabs pattern
When focus is on a tab button, the keyboard SHALL navigate between tabs as follows: ArrowRight moves to the next tab (wrapping), ArrowLeft moves to the previous tab (wrapping), Home moves to the first tab, End moves to the last tab. Each navigation SHALL both focus and activate the target tab.

#### Scenario: ArrowRight wraps from last to first
- **WHEN** focus is on the last tab button and ArrowRight is pressed
- **THEN** focus SHALL move to the first tab button and activate it

#### Scenario: ArrowLeft wraps from first to last
- **WHEN** focus is on the first tab button and ArrowLeft is pressed
- **THEN** focus SHALL move to the last tab button and activate it

#### Scenario: Home activates first tab
- **WHEN** any tab button has focus and Home is pressed
- **THEN** the first tab SHALL be activated and focused

#### Scenario: End activates last tab
- **WHEN** any tab button has focus and End is pressed
- **THEN** the last tab SHALL be activated and focused

#### Scenario: Arrow keys do not scroll the page
- **WHEN** ArrowRight or ArrowLeft is pressed while a tab is focused
- **THEN** the default browser scroll behavior SHALL be prevented (`e.preventDefault()`)

### Requirement: Click behavior is preserved
Existing mouse click behavior SHALL continue to work — clicking a tab button SHALL activate that tab and update all ARIA states consistently with the keyboard behavior.

#### Scenario: Click activates tab and updates aria-selected
- **WHEN** a user clicks an inactive tab button
- **THEN** it SHALL become active, `aria-selected="true"`, its panel SHALL become visible, and all other tabs SHALL have `aria-selected="false"` and `tabindex="-1"`
