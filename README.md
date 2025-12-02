# Global Copilot Instructions

## 🔒 Safety & Restriction Rules (Critical)
- The agent **may suggest or propose terminal commands** for tasks such as building, running scripts, or package management.
- **Do not execute or run commands automatically.**
- Always **ask for explicit approval** before suggesting any command to be executed.
- **Never propose or execute destructive commands** such as:
  - `rm`, `rm -rf`, `mv`, `sudo`, `chmod`, `chown`, `kill`, etc.
- Never create, modify, or reference files **outside the active workspace**.
- Never:
  - Delete files  
  - Move files  
  - Modify files outside the workspace  
  - Create files outside the current project  
- Perform operations **only through code changes**, never shell operations.
- If any action might be unsafe or destructive, pause and request explicit confirmation.
- Default to “do nothing without permission” in ambiguous situations.

---

## 🚫 Restrictions on Refactors & File Operations
- Refactor only files that are open or part of the current project.
- Never modify user environment, system files, or external directories.
- Never recommend or produce shell scripts that could alter, delete, or move files.
- When unsure about a refactor location, ask a clarifying question instead of guessing.

---

## 🤖 Hallucination Prevention & API Safety
- Do not invent functions, APIs, components, or hooks.
- Only use APIs and libraries that already exist in the workspace.
- Check `package.json` before referencing a dependency.
- If uncertain whether a function or API exists, ask before generating code.

---

## 🧩 General Coding Style
- Always use **TypeScript** with strict typing.
- Always prefer **arrow functions** for:
  - Components
  - Utility functions
  - Callbacks
  - Event handlers
- Use **React functional components with Hooks only** (no class components).
- Prefer modular code: small, focused files with clear single responsibility.
- Avoid large “god” components—split logic into hooks or small components as needed.

---

## 📝 Documentation Requirements (JSDoc)
- **All exported functions in `.ts` files MUST include JSDoc comments.**
- JSDoc must contain:
  - `@param` for each parameter
  - `@returns` describing the return type and purpose
  - Clear description of function behavior and edge cases
- For React components, include a short JSDoc block describing:
  - Props
  - Purpose
  - Any important rendering details

---

## 🧠 React-Specific Best Practices
- Avoid unnecessary re-renders by memoizing expensive computations.
- Use explicit prop typing with TypeScript `interface` or `type`.
- No usage of deprecated lifecycle methods or class components.
- The agent must **never use deprecated methods, properties, or APIs** from any imported package.
- Before generating code, the agent should verify that:
  - The method or property exists in the **installed version** of the package.
  - The method or property is not marked as deprecated in official documentation or TypeScript typings.

---

## 🌐 Code Quality Expectations
- Follow industry-standard formatting: clean, consistent, readable.
- Prefer early returns over deeply nested conditionals.
- Avoid side effects in utility functions unless explicitly needed.
- Use descriptive, meaningful names for all functions, variables, props, and files.

---

## 🧪 Testing (optional but encouraged)
- Encourage writing simple testable units.
- Separate logic into util functions for easier testing when appropriate.
