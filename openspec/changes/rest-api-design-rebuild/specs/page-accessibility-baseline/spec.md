## ADDED Requirements

### Requirement: Skip-to-content link present and functional
The page SHALL include a visually hidden `<a href="#main-content">Skip to content</a>` link as the first focusable element inside `<body>`. It SHALL become visible when it receives keyboard focus.

#### Scenario: Skip link is first focusable element
- **WHEN** a keyboard user presses Tab on page load
- **THEN** the skip link SHALL receive focus before the theme toggle or navigation

#### Scenario: Skip link reveals on focus
- **WHEN** the skip link receives focus
- **THEN** it SHALL become visible in the top-left area of the viewport

#### Scenario: Skip link navigates to main content
- **WHEN** a user activates the skip link
- **THEN** focus SHALL move to the element with `id="main-content"` (the `<main>` element)

### Requirement: Global :focus-visible style defined
The CSS SHALL define a `:focus-visible` rule that applies a 2px solid outline using `var(--accent)` with 2px offset to all interactive elements, ensuring keyboard focus is always visible.

#### Scenario: Focus indicator visible on links
- **WHEN** a keyboard user tabs to a link
- **THEN** a visible focus ring using `--accent` SHALL appear around the link

#### Scenario: Focus indicator visible on buttons
- **WHEN** a keyboard user tabs to a button (including tab buttons and theme toggle)
- **THEN** a visible focus ring using `--accent` SHALL appear around the button

#### Scenario: Focus indicator does not appear on mouse click
- **WHEN** a mouse user clicks a link or button
- **THEN** the `--accent` focus ring SHALL NOT appear (`:focus-visible` behavior)

### Requirement: .sr-only utility class defined
The CSS SHALL define a `.sr-only` class that visually hides an element while keeping it accessible to screen readers, using the standard clip-path technique.

#### Scenario: sr-only element not visible
- **WHEN** an element has class `sr-only`
- **THEN** it SHALL be invisible to sighted users (not occupying layout space or visible on screen)

#### Scenario: sr-only element readable by screen reader
- **WHEN** a screen reader encounters an element with class `sr-only`
- **THEN** it SHALL read the element's text content

### Requirement: Score dot elements have aria-label set by JavaScript
All `.score` elements on the page SHALL have `role="img"` and `aria-label="X out of 5"` (where X is the count of filled dots) set by JavaScript at page load time. The filled dot character SHALL be `●` (U+25CF).

#### Scenario: aria-label computed from dot count
- **WHEN** the page loads and the score accessibility script runs
- **THEN** every `.score` element SHALL have `aria-label` set to the correct count (e.g., `aria-label="4 out of 5"` for `●●●●○`)

#### Scenario: role="img" set on score elements
- **WHEN** the page loads
- **THEN** every `.score` element SHALL have `role="img"`

#### Scenario: Screen reader announces score meaningfully
- **WHEN** a screen reader encounters a `.score` element
- **THEN** it SHALL announce "X out of 5" instead of individual bullet characters

### Requirement: One insecure HTTP link replaced with HTTPS
All external links on the page SHALL use `https://`. Specifically, the Collection+JSON spec link (`amundsen.com`) SHALL use `https://`.

#### Scenario: No http:// links present
- **WHEN** the page HTML is inspected
- **THEN** no `href` attribute SHALL begin with `http://`
