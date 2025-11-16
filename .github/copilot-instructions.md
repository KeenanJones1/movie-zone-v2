# Project Overview
This is a modern web application project skeleton. Goals: clean UI, fast performance, strong accessibility (a11y), and maintainable code.

## Tech & Style
**Stack**: Adaptable to multiple frameworks and languages:
- **Frontend**: React, Svelte, Angular, Vue, Ionic, or vanilla JS/TS
- **Backend**: Ruby on Rails, Node.js, Python (Django/Flask), or other frameworks
- **Styling**: Tailwind CSS, CSS Modules, SCSS, styled-components, or framework-specific solutions
- **Type Safety**: TypeScript, Flow, or language-native typing

**UI Philosophy**: semantic HTML, keyboard-first accessibility, minimal dependencies.

**Styling Consistency**: Choose ONE approach per project (Tailwind, CSS Modules, etc.). Use design tokens/variables; avoid magic numbers.

**Testing Defaults**:
- React: React Testing Library with `getByTestId`
- Svelte/Vue: @testing-library/svelte or @testing-library/vue
- Angular: TestBed with fixture.debugElement
- Rails: RSpec + Capybara for integration
- General: appropriate framework testing tools

## Coding Guidelines
- **Components/Modules**: Small, focused, single-responsibility. Prefer composition over inheritance.
- **State Management**: Use framework-appropriate patterns (React hooks, Svelte stores, Angular services, Rails ActiveRecord, etc.).
- **Performance**: Avoid unnecessary re-renders/queries; code-split pages/large components; memoize only when measured/obvious.
- **Async Operations**: Use async/await, explicit error paths, user-friendly error messages.
- **Accessibility**: Proper ARIA roles/labels, focus management in modals, sufficient color contrast, keyboard navigation.
- **Security**: Validate inputs, sanitize outputs, protect against XSS/CSRF/SQL injection based on stack.

## Clean Code Principles
- **Naming**: Use descriptive, intention-revealing names. Avoid abbreviations, single letters (except loop counters), and Hungarian notation.
- **Functions/Methods**: Do one thing well. Keep them small (<20 lines ideal). Minimize parameters (≤3 preferred).
- **DRY (Don't Repeat Yourself)**: Extract repeated logic into reusable functions/utilities. Avoid copy-paste coding.
- **YAGNI (You Aren't Gonna Need It)**: Don't add functionality until it's actually needed. Avoid premature optimization.
- **SOLID Principles**:
  - **S**ingle Responsibility: Each module/class does one thing
  - **O**pen/Closed: Open for extension, closed for modification
  - **L**iskov Substitution: Subtypes must be substitutable for base types
  - **I**nterface Segregation: Many specific interfaces > one general interface
  - **D**ependency Inversion: Depend on abstractions, not concretions
- **Error Handling**: Don't return null/undefined; use Option types or explicit error objects. Fail fast with clear messages.
- **Comments**: Code should be self-documenting. Use comments for "why", not "what". Remove commented-out code.
- **Boy Scout Rule**: Leave code cleaner than you found it. Refactor as you go.

## Working Agreement for Copilot
1. **Don't edit more than one file at a time** unless I say so.
2. For **large files/complex work**: propose an **Edit Plan** first (sections to change, order, dependencies, number of edits).
3. After each edit: report **"✅ Completed [n]/[N], ready for next?"**
4. **Ask before**: 
   - (a) cross-file changes
   - (b) API shape changes
   - (c) database migrations/schema changes
   - (d) snapshot/golden test updates

## Test Policy
- Add/update tests for meaningful behavior changes
- Use appropriate query methods for your framework (`getByTestId`, `getByRole`, etc.)
- Cover: render/response, main interaction, edge states (loading/error/empty)
- Keep tests **fast and deterministic**
- Backend: test business logic, edge cases, error handling, database interactions