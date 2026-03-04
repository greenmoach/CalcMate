# AGENTS.md - Web Calculators Project

## Project Overview
Vanilla HTML/CSS/JS calculator applications. Each calculator is a self-contained single HTML file with no build tools, frameworks, or package managers.

### Directory Structure
```
/home/ubuntu/source/opencode-1/
├── index.html              # Home page
├── calculator.html         # Main calculator
├── entertainment/          # Entertainment calculators
├── transportation/         # Transportation calculators
├── utility/               # Utility calculators
├── education/             # Education calculators
├── fitness/               # Fitness calculators
├── lifestyle/             # Lifestyle calculators
├── finance/               # Finance calculators
└── health/                # Health calculators
```

---

## Build / Lint / Test Commands

**No build system exists.** Each calculator is a self-contained HTML file.

### Running the Project
- Open any `.html` file directly in a browser

### Testing
No test framework is configured by default. To add and run tests:

```bash
# Initialize npm and install vitest
npm init -y
npm install --save-dev vitest

# Run all tests
npx vitest run

# Run a single test file
npx vitest run test/calculator.test.js

# Run tests in watch mode
npx vitest
```

### Adding Tests
1. Create `test/` directory
2. Add test files (e.g., `test/calculator.test.js`)
3. Example test structure:
```javascript
import { describe, it, expect } from 'vitest';

describe('Loan Calculator', () => {
    it('calculates monthly payment correctly', () => {
        // Test logic here
    });
});
```

---

## Code Style Guidelines

### General
- **Vanilla HTML/CSS/JS** - no frameworks
- Each calculator in its own `.html` file
- **4-space indentation** for HTML/CSS/JS
- Keep files self-contained (inline CSS and JS)

### HTML
- Use semantic HTML5 elements (`<header>`, `<main>`, `<section>`, `<label>`, `<input>`, `<button>`)
- Use double quotes for all attributes
- Add `lang` attribute for accessibility (e.g., `lang="en"`, `lang="zh-TW"`)
- Include `meta viewport` for responsive design
- Include appropriate `<title>` for each page
- Link to Google Fonts via CDN

### CSS
- Put styles in `<style>` tag in `<head>`
- Use BEM-inspired class naming (`.calculator`, `.input-group`, `.btn-calculate`)
- Use CSS custom properties for shared colors
- Mobile-responsive breakpoints with `@media`
- CSS animations (`@keyframes`) for visual effects
- Hover/active states for interactive elements
- `box-sizing: border-box` reset
- Focus states for accessibility (`input:focus`, `button:focus`)

### JavaScript
- ES6+ syntax (arrow functions, `const`/`let`, template literals)
- Meaningful variable names (camelCase)
- PascalCase for function names acting as constructors/classes
- Prefer `const` over `let`, avoid `var`
- Template literals: `` `Value: ${value}` ``
- Strict equality (`===`) over loose equality (`==`)
- Event listeners for DOM interactions
- Keyboard events (Enter to submit, Escape to clear)
- Place `<script>` at end of `<body>` or use `defer`

### Error Handling
- Validate user input before processing
- User-friendly error messages (alert or inline)
- Handle edge cases (division by zero, NaN, empty inputs)
- Use try-catch for potentially failing operations
- Display "Please fill all fields" or similar prompts

### Accessibility
- Semantic elements with proper label associations
- `for` attribute on labels matching input `id`
- Keyboard input support (Enter to submit)
- Minimum 16px font size for inputs
- Adequate color contrast
- `aria-label` where context is unclear

---

## Naming Conventions

| Type          | Convention   | Example                        |
|---------------|--------------|--------------------------------|
| Functions     | camelCase    | `calculateLoan()`, `getBMI()`  |
| Variables     | camelCase    | `monthlyPayment`, `interestRate` |
| CSS classes   | kebab-case   | `.input-group`, `.result-display` |
| HTML ids      | camelCase    | `id="amount"`, `id="monthly-payment"` |
| HTML files    | kebab-case   | `loan-calculator.html`         |

---

## Common Patterns

### Input Form
```html
<div class="input-group">
    <label for="amount">Label Text</label>
    <input type="number" id="amount" placeholder="Enter value">
</div>
<button onclick="calculate()">Calculate</button>
```

### Result Display
```html
<div class="result" id="result">
    <div class="output-value" id="output">$0.00</div>
    <div class="details" id="details">Additional info</div>
</div>
```

### Calculation Function
```javascript
function calculate() {
    const input = parseFloat(document.getElementById('input').value);
    if (isNaN(input) || input === 0) {
        alert('Please enter a valid value');
        return;
    }
    const result = doCalculation(input);
    document.getElementById('output').textContent = formatResult(result);
    document.getElementById('result').classList.add('show');
}
```

### Navigation (sub-pages)
```html
<a href="../../index.html" class="back-link">← Back to Home</a>
```

---

## Adding New Calculators

1. **Choose category**: Place in appropriate directory (finance/, health/, etc.)
2. **Create HTML file**: Use kebab-case naming (`calculator-name.html`)
3. **Use template**: Copy structure from existing calculator in same category
4. **Add styling**: Match category's visual theme
5. **Implement calculation**: Add JS function with proper validation
6. **Test**: Open in browser, verify inputs work correctly
7. **Update index**: Add to index.html if it contains categorized list

---

## Notes for Agents

- Simple project - no complex tooling required
- Each file is independent - no shared state between calculators
- Test calculations with edge cases (0, negative, very large numbers)
- Maintain consistent visual style within category directories
- Use 2 decimal places for financial calculations
- No Cursor or Copilot rules configured in this project
