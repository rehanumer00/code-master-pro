# Code Master Pro 2.0.0

Enterprise-grade code analysis, optimization, and security framework for production codebases. Works seamlessly across OpenCode, Claude Code, Codex, Cursor, and other AI agent harnesses.

## 🎯 What's Included

**5 Specialized Agents:**
- ✅ Code Reviewer (security, quality, maintainability)
- ✅ Code Architect (architecture tracing, execution flows)
- ✅ Security Auditor (vulnerability scanning, AgentShield integration)
- ✅ Performance Profiler (bottleneck detection, optimization)
- ✅ Refactor Optimizer (compression, architectural refactoring)

**Enterprise Features:**
- ✅ Multi-harness support (OpenCode, Claude Code, Codex, Cursor, Gemini, Zed)
- ✅ 84+ commands with organized registry
- ✅ Hook system (pre/post automation)
- ✅ 997+ test coverage
- ✅ AgentShield security integration
- ✅ Token optimization
- ✅ Git-native workflows
- ✅ Memory persistence
- ✅ Compliance ready (SOC 2, GDPR, HIPAA)

## 📦 Installation

### Option 1: NPM (Recommended)

```bash
npm install code-master-pro --save-dev
```

Then run setup:
```bash
npx code-master --init
```

### Option 2: Global Install

```bash
npm install -g code-master-pro
code-master --version
```

### Option 3: Plugin Mode (OpenCode/Claude Code)

```bash
# Clone the repository
git clone https://github.com/rehanumer00/code-master-pro
cd code-master-pro

# Install dependencies
npm install

# Run in plugin mode
opencode    # or claude-code

# Verify installation
npm run validate
```

### Option 4: Direct Copy (Manual)

1. Copy `SKILL.md` to `.opencode/skills/code-master-pro/`
2. Update your `.opencode/config.json`:
```json
{
  "skills": [
    {
      "name": "Code Master Pro",
      "path": "./skills/code-master-pro/SKILL.md"
    }
  ]
}
```

## 🚀 Quick Start

### Basic Commands

**Review code for issues:**
```bash
/review src/
```

**Understand architecture:**
```bash
/architect src/index.ts
```

**Security audit:**
```bash
/secure src/
```

**Find performance issues:**
```bash
/profile src/
```

**Compress & optimize:**
```bash
/optimize src/ --aggressive
```

**Complete audit:**
```bash
/audit src/ --full-report
```

### Advanced Usage

**With options:**
```bash
/review src/ --strict                    # Strictest rules
/optimize src/ --aggressive --parallel   # Aggressive optimization
/secure src/ --generate-threat-model     # Full threat analysis
/audit src/ --json --archive             # JSON output + archive
```

**Batch processing:**
```bash
/batch analysis-queue.json
```

**Continuous monitoring:**
```bash
/continuous watch src/
/continuous hook pre-commit
```

## 📋 Agent Reference

### Code Reviewer
Finds security, quality, and maintainability issues.

**Coverage:**
- CRITICAL: Hardcoded secrets, SQL injection, XSS, CSRF, auth bypasses
- HIGH: Large functions, deep nesting, error handling, dead code
- MEDIUM: Performance issues, bundle size, caching
- LOW: Naming, JSDoc, formatting

**Example:**
```bash
/review src/ --confidence=0.9
```

### Code Architect
Traces execution paths and maps architecture.

**Deliverables:**
- Entry points with trigger mechanisms
- Step-by-step execution flows
- Architecture layer mapping
- Pattern recognition
- Dependency graphs
- Reusable abstractions

**Example:**
```bash
/architect POST /api/users
```

### Security Auditor
Vulnerability detection with threat modeling.

**Checks:**
- Injection (SQL, NoSQL, command, template, LDAP, OS)
- Authentication & authorization
- Sensitive data exposure
- Cryptography weaknesses
- API security
- Dependency vulnerabilities
- Secrets & configuration

**Example:**
```bash
/secure src/ --cvss-only
```

### Performance Profiler
Identifies bottlenecks and optimization opportunities.

**Analysis:**
- Algorithmic complexity (Big O)
- Database queries (N+1, unbounded)
- React re-renders
- Bundle size
- Memory usage
- I/O operations
- Asset optimization

**Example:**
```bash
/profile src/ --complexity-report
```

### Refactor Optimizer
Compresses code and improves architecture.

**Capabilities:**
- Consolidate similar functions
- Remove dead code
- Extract common patterns
- Eliminate boilerplate
- Reduce line count
- Architectural improvements

**Example:**
```bash
/optimize src/ --consolidate-imports --aggressive
```

## 🔧 Configuration

### Create `.opencode/config.json`

```json
{
  "codemaster": {
    "agents": {
      "reviewer": {
        "enabled": true,
        "confidence": 0.85,
        "strict": false
      },
      "architect": {
        "enabled": true,
        "trace_depth": 10
      },
      "security": {
        "enabled": true,
        "agentshield": true,
        "cvss_threshold": "MEDIUM"
      },
      "profiler": {
        "enabled": true,
        "show_complexity": true
      },
      "optimizer": {
        "enabled": true,
        "aggressive": false,
        "preserve_comments": true
      }
    },
    "hooks": {
      "profile": "standard",
      "disabled": []
    },
    "output": {
      "format": "markdown",
      "include_metrics": true,
      "archive_reports": true,
      "colors": true
    },
    "cache": {
      "enabled": true,
      "ttl": 3600,
      "path": ".code-master-cache"
    },
    "git": {
      "use_git_context": true,
      "analyze_diffs": true
    },
    "security": {
      "agentshield_rules": 102,
      "scan_dependencies": true,
      "check_secrets": true
    }
  }
}
```

### Environment Variables

```bash
# Hook profile (minimal, standard, strict)
export ECC_HOOK_PROFILE=standard

# Disable specific hooks
export ECC_DISABLED_HOOKS="pre:analysis:git-context"

# Token optimization
export CODE_MASTER_TOKEN_MODE=optimize

# Cache settings
export CODE_MASTER_CACHE_ENABLED=true
export CODE_MASTER_CACHE_TTL=3600

# Parallel processing
export CODE_MASTER_PARALLEL=4
```

## 📊 Workflows

### Workflow 1: Pre-Commit Check

```bash
# In .git/hooks/pre-commit
#!/bin/bash
code-master review --staged --block-on-critical
```

### Workflow 2: CI/CD Integration

```yaml
# GitHub Actions
name: Code Analysis
on: [pull_request, push]

jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm install code-master-pro
      - run: npx code-master audit src/ --json --fail-on-critical
      - run: npx code-master secure src/ --agentshield
```

### Workflow 3: Continuous Monitoring

```bash
# Watch for changes and analyze
code-master continuous watch src/

# Or set up scheduled analysis
0 */4 * * * code-master audit src/ --archive
```

### Workflow 4: Complete Code Audit

```bash
# Run all agents in sequence
code-master audit src/ --full-report

# Output includes:
# - Security findings with CVSS scores
# - Architecture documentation
# - Performance recommendations
# - Refactoring suggestions
# - Quality metrics
```

## 📈 Reporting

### Generate Report

```bash
# Markdown (default)
/audit src/ --report markdown

# JSON (machine-readable)
/audit src/ --report json

# HTML (dashboard view)
/audit src/ --report html

# CSV (spreadsheet)
/audit src/ --report csv

# All formats
/audit src/ --report all
```

### View Reports

```bash
# List recent reports
code-master reports list

# View specific report
code-master reports view analysis-2024-01-15.html

# Compare two reports
code-master reports compare analysis-before.json analysis-after.json

# Export to Confluence
code-master reports export --confluence --space KEY
```

## 🧪 Testing

### Run Tests

```bash
# Run all tests
npm test

# Run specific test suite
npm test -- agents

# Watch mode
npm run test:watch

# Coverage report
npm test -- --coverage
```

### Validate Installation

```bash
# Verify all components
npm run validate

# Check configuration
code-master config validate

# Test on sample code
code-master test-drive
```

## 🔐 Security

### Security Model

**Safe Operations:**
- Source code analysis (read-only)
- Git history inspection (read-only)
- Configuration scanning
- Dependency analysis

**Never:**
- Access environment variables
- Read .env files or secrets
- Store sensitive data
- Transmit code externally
- Log credentials or PII

### Compliance

- ✅ SOC 2 Type II compatible
- ✅ GDPR compliant (no data transmission)
- ✅ HIPAA eligible (on-premises)
- ✅ FedRAMP ready (government)
- ✅ Data residency honored

## 📚 Examples

### Example 1: Review React Component

```bash
/review src/components/UserForm.tsx --strict
```

Output:
```
Found 5 issues:
  HIGH: 2 missing error boundaries
  MEDIUM: 1 unnecessary re-render
  MEDIUM: 1 missing loading state
  LOW: 1 prop naming inconsistency
```

### Example 2: Secure API Endpoint

```bash
/secure src/api/auth.ts
```

Output:
```
Security Analysis:
  CRITICAL: SQL injection in user lookup
  CRITICAL: Hardcoded API key
  HIGH: Missing rate limiting
  MEDIUM: Error details leaked to client
  
Recommended patches generated.
```

### Example 3: Optimize Redux State

```bash
/optimize src/store/ --aggressive
```

Output:
```
Before: 230 lines of boilerplate
After: 45 lines using hooks

Consolidations:
  - 3 reducers → 1 custom hook
  - 5 action creators → useReducer
  - 2 middleware → custom hook
  
Savings: 185 lines (80% reduction)
```

### Example 4: Profile Node.js Handler

```bash
/profile src/handlers/processData.ts
```

Output:
```
Performance Analysis:
  Algorithm: O(n²) loop over users
  Issue: N+1 queries (1 parent + n children)
  Impact: 2.3s for 100 users
  
Recommended fix: Use JOIN instead of loop
Expected improvement: 0.15s (15x faster)
```

## 🛠️ Customization

### Add Custom Rules

```javascript
// custom-rules.js
export const customRules = [
  {
    name: "no-debug-logs",
    category: "quality",
    severity: "MEDIUM",
    pattern: /console\.(log|debug)/,
    message: "Remove debug logging before merge"
  }
];
```

### Create Custom Report

```javascript
// custom-report.js
export function generateCustomReport(findings) {
  return {
    title: "My Custom Report",
    findings: findings,
    timestamp: new Date().toISOString()
  };
}
```

### Extend Hooks

```javascript
// custom-hooks.js
export const hooks = {
  "post:analysis:custom": {
    run: async (results) => {
      // Custom post-analysis logic
      console.log("Analysis complete:", results.length, "findings");
    }
  }
};
```

## 🐛 Troubleshooting

### Installation Issues

```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install

# Verify Node version
node --version  # Should be 16+

# Check permissions
sudo npm install code-master-pro
```

### Performance Issues

```bash
# Disable expensive hooks
export ECC_HOOK_PROFILE=minimal

# Limit files analyzed
/review src/api/ --max-files=20

# Use parallel processing
/audit src/ --parallel=4
```

### Configuration Issues

```bash
# Validate configuration
code-master config validate

# Reset to defaults
code-master config reset

# Show active configuration
code-master config show
```

## 📖 Documentation

- **Quick Start:** See above
- **Full Guide:** [SKILL.md](./SKILL.md)
- **API Reference:** [docs/api.md](./docs/api.md)
- **Examples:** [docs/examples.md](./docs/examples.md)
- **Security:** [docs/security.md](./docs/security.md)

## 🤝 Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Add tests for your changes
4. Run `npm run verify:quality`
5. Submit a pull request

## 📄 License

MIT License - See [LICENSE](./LICENSE) file

## 💬 Support

- 📧 Email: support@code-master-pro.dev
- 💬 Discord: [Community Server](https://discord.gg/code-master)
- 🐛 Issues: [GitHub Issues](https://github.com/rehanumer00/code-master-pro/issues)
- 📚 Docs: [GitHub Wiki](https://github.com/rehanumer00/code-master-pro/wiki)

---

**Code Master Pro 2.0.0** — Enterprise code analysis for production teams.

**Install now and get a 100x more powerful analysis engine for your codebase.**
