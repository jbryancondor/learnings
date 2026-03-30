# 17 — Cucumber / Gherkin (BDD)

## 1. Overview
The original spec-driven development tool — Behavior-Driven Development (BDD) framework using Gherkin syntax (Given/When/Then). Specifications are executable: they run as automated tests. The OG of "write the spec, run the spec."

## 2. Key Data

| Attribute | Value |
|---|---|
| **Maker** | Cucumber Ltd / SmartBear (acquired) |
| **Type** | Open-source BDD testing framework |
| **GitHub Stars** | ~5,000+ (cucumber-js) |
| **License** | MIT |
| **Spec Format** | Gherkin (.feature files) |
| **SDD Level** | Executable specs (BDD) |
| **Agent Lock-in** | N/A (not AI-based) |
| **Install** | `npm install @cucumber/cucumber` (JS) or language-specific |
| **Languages** | Java, JavaScript, Ruby, Python, Go, .NET, and more |
| **Pricing** | Free |

## 3. How It Works

### Workflow
1. Write feature files in Gherkin syntax (Given/When/Then)
2. Implement step definitions (code that maps to Gherkin steps)
3. Run specs as tests: `npx cucumber-js`
4. Specs ARE the tests — living documentation

### Philosophy
Specifications are executable. They serve as both documentation and automated tests. When specs fail, the implementation doesn't match the contract.

## 4. Example Spec

### user-registration.feature
```gherkin
Feature: User Registration
  As a new user
  I want to register with my email and password
  So that I can access the platform

  Background:
    Given the registration system is running
    And the database is empty

  Scenario: Successful registration
    Given I have a valid email "user@example.com"
    And I have a valid password "SecurePass1"
    When I submit the registration form
    Then I should receive a 201 response
    And the response should contain my user ID
    And the response should contain my email
    And the response should NOT contain a password hash
    And I should receive a verification email

  Scenario: Duplicate email
    Given a user with email "user@example.com" already exists
    When I submit a registration with email "user@example.com"
    Then I should receive a 409 response
    And the response should say "Email already exists"

  Scenario: Weak password
    Given I have a valid email "user@example.com"
    And I have a weak password "abc"
    When I submit the registration form
    Then I should receive a 400 response
    And the response should list password requirements

  Scenario Outline: Invalid email formats
    When I submit a registration with email "<email>"
    Then I should receive a 400 response

    Examples:
      | email           |
      | not-an-email    |
      | @missing-local  |
      | missing@.domain |
```

### Step Definition (TypeScript)
```typescript
import { Given, When, Then } from '@cucumber/cucumber';

Given('I have a valid email {string}', function (email: string) {
  this.email = email;
});

When('I submit the registration form', async function () {
  this.response = await request(app)
    .post('/auth/register')
    .send({ email: this.email, password: this.password });
});

Then('I should receive a {int} response', function (status: number) {
  expect(this.response.status).toBe(status);
});
```

## 5. Strengths
- Specs ARE tests — executable documentation
- 20+ years of maturity and battle-testing
- Non-technical stakeholders can read Gherkin
- Multi-language support
- Living documentation that stays in sync with code
- Strong QA/testing integration
- Well-understood by enterprise teams

## 6. Weaknesses / Criticisms
- Not AI-powered (requires manual step definition coding)
- Step definitions can become maintenance burden
- Gherkin can become verbose for complex scenarios
- "We were sold BDD via Cucumber as the platonic ideal of SDD 20 years ago" — HN commenter
- Step reuse across features can be fragile
- Not suitable as a general SDD framework (testing-focused)

## 7. Adoption & Community
- Widely used in enterprise QA for 15+ years
- Acquired by SmartBear (same as Swagger/Stoplight)
- Multi-language implementations (Java, JS, Ruby, Python, Go, .NET)
- Standard tool in many CI/CD pipelines

## 8. When to Choose This Tool
- You want **executable specifications** (specs = tests)
- You have **non-technical stakeholders** who need to read specs
- You want **BDD** methodology
- You need **QA-driven** development
- You're in an **enterprise** with existing Cucumber infrastructure
- You want specs that **enforce compliance** automatically

## 9. Sources
- [Official Website](https://cucumber.io/)
- [GitHub: cucumber-js](https://github.com/cucumber/cucumber-js)
- [Gherkin Reference](https://cucumber.io/docs/gherkin/reference/)
- [Cucumber Docs](https://cucumber.io/docs/)
- [Martin Fowler: Understanding SDD](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html) (BDD comparison)
- [Hacker News Discussion on SDD](https://news.ycombinator.com/item?id=45610996)
