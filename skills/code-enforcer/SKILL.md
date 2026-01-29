# Coding Discipline Enforcer

## Description
Prevents ad-hoc, one-off solutions by enforcing programmatic implementation, proper integration, and documentation. This skill ensures all code changes are reusable, maintainable, and properly integrated into the primary codebase rather than creating isolated scripts or workflows.

## When to Use
- ANY code generation or modification task
- Before implementing new features
- When refactoring existing code
- When adding utilities or helpers

## Critical Rules - READ FIRST

### NEVER Do These Things
1. **No standalone scripts** - Don't create one-off scripts that aren't imported by the main codebase
2. **No duplicate logic** - If similar code exists, extend/refactor it instead of copying
3. **No orphaned files** - Every file must be imported/used somewhere
4. **No magic values** - Use constants, config files, or environment variables
5. **No undocumented exports** - Every public function needs JSDoc/docstring

### ALWAYS Do These Things
1. **Check existing patterns first** - Search codebase for similar implementations
2. **Integrate, don't isolate** - Add to existing modules rather than creating new ones
3. **Make it reusable** - Design for future use cases, not just current one
4. **Document intent** - Explain WHY, not just WHAT
5. **Update imports** - Ensure new code is actually used somewhere

## Step-by-Step Workflow

### Phase 1: Discovery (MANDATORY)
```bash
# 1. Find existing patterns
view /path/to/src/
grep -r "similar_function_name" src/

# 2. Check for related utilities
view src/utils/
view src/helpers/
view src/services/

# 3. Review project structure
view README.md
view docs/architecture.md  # if exists
```

**STOP** - Before writing ANY code, answer:
- Does similar functionality already exist?
- Which module should this belong to?
- What existing code will import/use this?

### Phase 2: Design
```markdown
# Document your plan BEFORE coding:

## Where This Goes
- File: src/[module]/[feature].ts
- Imports: Used by [specific files]
- Exports: [list what's exported]

## Why This Approach
- [Reasoning for design decisions]
- [How it fits existing patterns]
- [What it enables for future features]

## Integration Points
- [ ] Updated [file] to import this
- [ ] Added to [barrel export]
- [ ] Registered in [config/registry]
```

### Phase 3: Implementation
```typescript
// GOOD - Reusable, integrated function
// src/utils/validation.ts

/**
 * Validates email format and checks against blacklist
 * 
 * @param email - Email address to validate
 * @param blacklist - Optional array of blocked domains
 * @returns true if valid and not blacklisted
 * 
 * @example
 * ```ts
 * if (validateEmail(userInput, BLOCKED_DOMAINS)) {
 *   // proceed
 * }
 * ```
 */
export function validateEmail(
  email: string, 
  blacklist: string[] = []
): boolean {
  // Implementation
}

// src/config/constants.ts
export const BLOCKED_DOMAINS = ['spam.com', 'fake.net'];

// src/services/userService.ts
import { validateEmail } from '../utils/validation';
import { BLOCKED_DOMAINS } from '../config/constants';

export function registerUser(email: string) {
  if (!validateEmail(email, BLOCKED_DOMAINS)) {
    throw new Error('Invalid email');
  }
  // Rest of registration
}
```
```typescript
// BAD - Standalone, not integrated
// scripts/validate_email.js  ❌

function validate(email) {
  // Logic here but nothing imports this
}

// Used once in a random place, never reused
```

### Phase 4: Integration Checklist
```markdown
Before finishing, verify:

- [ ] Function/class is exported from its module
- [ ] Module is exported from barrel file (index.ts)
- [ ] At least one file imports and uses this code
- [ ] Constants are in config files, not hardcoded
- [ ] JSDoc/docstrings are complete
- [ ] Types/interfaces are defined and exported
- [ ] Tests exist (if test coverage required)
- [ ] No console.log() statements remain
- [ ] No commented-out code blocks
- [ ] README or docs updated if needed
```

### Phase 5: Documentation
```typescript
// Update the module's index or main file with comments:

/**
 * User Management Module
 * 
 * Exports:
 * - registerUser() - Creates new user accounts
 * - validateEmail() - Validates email format
 * - BLOCKED_DOMAINS - List of disallowed email domains
 * 
 * Usage:
 * ```ts
 * import { registerUser } from './users';
 * await registerUser(email, password);
 * ```
 */
```

## Code Organization Patterns

### Directory Structure Rules
```
src/
├── config/          # Constants, env vars, settings
├── types/           # TypeScript interfaces/types
├── utils/           # Pure functions, helpers
├── services/        # Business logic, API calls
├── models/          # Data models, schemas
├── controllers/     # Request handlers
└── index.ts         # Main entry point
```

**Rules:**
- Utils = stateless, reusable functions
- Services = stateful, business logic
- Models = data structures only
- Controllers = request/response handling

### Import Organization
```typescript
// GOOD - Clear dependency hierarchy
// src/services/userService.ts

// 1. External dependencies
import { hash } from 'bcrypt';
import { v4 as uuid } from 'uuid';

// 2. Internal types
import type { User, UserCreateInput } from '../types/user';

// 3. Internal utilities
import { validateEmail } from '../utils/validation';
import { db } from '../config/database';

// 4. Internal constants
import { BLOCKED_DOMAINS, MIN_PASSWORD_LENGTH } from '../config/constants';

// Implementation follows...
```

### Naming Conventions
```typescript
// Files: camelCase for single export, PascalCase for classes
userService.ts        // exports userService object
UserModel.ts          // exports UserModel class
validation.ts         // exports multiple functions

// Functions: verb + noun
getUserById()
validateEmail()
createUserAccount()

// Constants: SCREAMING_SNAKE_CASE
MAX_LOGIN_ATTEMPTS
API_BASE_URL
DEFAULT_TIMEOUT

// Types/Interfaces: PascalCase
interface UserProfile {}
type ValidationResult = {}
```

## Anti-Patterns to Reject

### ❌ The YOLO Script
```bash
# scripts/fix_thing.sh
#!/bin/bash
# Does something once, never integrated
```
**Instead:** Make it a proper CLI command or API endpoint

### ❌ The Magic Number
```typescript
if (attempts > 5) { // What is 5?
```
**Instead:**
```typescript
const MAX_LOGIN_ATTEMPTS = 5;
if (attempts > MAX_LOGIN_ATTEMPTS) {
```

### ❌ The Copy-Paste Special
```typescript
// File A
function validateUser(user) { /* logic */ }

// File B
function validateUser(user) { /* same logic */ }
```
**Instead:** One shared utility, imported by both

### ❌ The Orphan File
```typescript
// src/helpers/thing.ts
export function doThing() { /* nobody imports this */ }
```
**Instead:** Delete it or ensure it's actually used

### ❌ The God Function
```typescript
function handleEverything(data) {
  // 500 lines of mixed concerns
}
```
**Instead:** Break into focused, reusable functions

## Quality Gates

### Before Committing, Answer These:
1. **Is it findable?** - Can future developers find this code when they need it?
2. **Is it reusable?** - Could this solve similar problems later?
3. **Is it integrated?** - Is it actually being used by the codebase?
4. **Is it documented?** - Can someone understand WHY it exists?
5. **Is it tested?** - Can we verify it works?

If ANY answer is "no" - **STOP and fix it**.

## Examples of Good Integration

### Example 1: Adding Authentication
```typescript
// ❌ BAD - Standalone script
// auth_check.js
const token = process.argv[2];
// validate token logic...

// ✅ GOOD - Integrated middleware
// src/middleware/auth.ts
export function requireAuth(req, res, next) {
  const token = extractToken(req);
  if (!validateToken(token)) {
    return res.status(401).json({ error: 'Unauthorized' });
  }
  next();
}

// src/app.ts
import { requireAuth } from './middleware/auth';
app.use('/api/protected', requireAuth);
```

### Example 2: Adding Validation
```typescript
// ❌ BAD - Inline validation everywhere
function createUser(data) {
  if (!data.email.includes('@')) throw new Error('bad email');
  if (data.password.length < 8) throw new Error('bad password');
  // ...
}

function updateUser(data) {
  if (!data.email.includes('@')) throw new Error('bad email'); // Duplicated!
  // ...
}

// ✅ GOOD - Centralized, reusable validation
// src/validators/user.ts
import { z } from 'zod';

export const userSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8),
  // ...
});

export function validateUser(data: unknown) {
  return userSchema.parse(data);
}

// src/services/userService.ts
import { validateUser } from '../validators/user';

export function createUser(data: unknown) {
  const validData = validateUser(data);
  // Use validData...
}
```

### Example 3: Configuration Management
```typescript
// ❌ BAD - Magic values scattered everywhere
const apiUrl = 'https://api.example.com';  // In file A
const timeout = 5000;                       // In file B
const retries = 3;                          // In file C

// ✅ GOOD - Centralized configuration
// src/config/api.ts
export const API_CONFIG = {
  baseUrl: process.env.API_URL || 'https://api.example.com',
  timeout: parseInt(process.env.API_TIMEOUT || '5000'),
  maxRetries: parseInt(process.env.API_MAX_RETRIES || '3'),
} as const;

// src/services/apiClient.ts
import { API_CONFIG } from '../config/api';

export const apiClient = axios.create({
  baseURL: API_CONFIG.baseUrl,
  timeout: API_CONFIG.timeout,
});
```

## Decision Tree

When asked to implement a feature:
```
START
  ↓
Does similar code exist?
  ├─ YES → Extend/refactor existing code
  └─ NO → Continue
       ↓
Which module does this belong in?
  ├─ utils/ → Pure, stateless function
  ├─ services/ → Business logic
  ├─ models/ → Data structure
  └─ controllers/ → Request handling
       ↓
How will this be imported/used?
  ├─ Can't answer → STOP: Need integration plan
  └─ Clear usage → Continue
       ↓
Document intent and examples
  ↓
Implement with proper exports
  ↓
Verify integration checklist
  ↓
DONE
```

## Red Flags - Stop Immediately If:
- You're creating a file nothing imports
- You're copying logic that exists elsewhere
- You can't explain where this will be used
- You're hardcoding values that might change
- You're writing code "for later" that isn't needed now
- You're creating a new pattern instead of following existing ones

## Final Rule
**If it's not integrated into the codebase in a reusable way, it doesn't exist.**

No standalone scripts. No orphaned utilities. No magic values. Everything must be:
1. Properly placed in the module structure
2. Exported and imported where needed
3. Documented with clear intent
4. Following existing project patterns

When in doubt: **INTEGRATE, DON'T ISOLATE**
```

---

## How to Use This Skill

**Save it as:** `.claude/skills/coding-discipline/SKILL.md` in your project

**Reference it in prompts:**
```
"Read .claude/skills/coding-discipline/SKILL.md first, then help me implement user authentication"