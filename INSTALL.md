# Code Master Pro Installation Guide

## Quick Install (30 seconds)

### For OpenCode Users
```bash
# In your project directory
opencode --install code-master-pro
# or
npm install code-master-pro --save-dev
```

### For Claude Code Users
```bash
# In your project directory
npm install code-master-pro --save-dev
npx code-master --init
```

### For Codex Users
```bash
npm install code-master-pro --save-dev
npx code-master config --codex
```

### For Cursor Users
```bash
npm install code-master-pro --save-dev
# Cursor will auto-detect and load
```

## Verification (10 seconds)

After installation, verify it works:

```bash
# Check installation
npx code-master --version
# Expected: v2.0.0

# Run test
npx code-master test-drive
# Should analyze sample code successfully

# List commands
npx code-master --help
# Shows all 84+ commands
```

## Configuration (Optional)

Create `.opencode/config.json` in your project:

```json
{
  "codemaster": {
    "agents": {
      "reviewer": { "enabled": true },
      "architect": { "enabled": true },
      "security": { "enabled": true },
      "profiler": { "enabled": true },
      "optimizer": { "enabled": true }
    }
  }
}
```

Or use preset profiles:

```bash
# Minimal (fastest, least thorough)
npx code-master config --profile minimal

# Standard (balanced, recommended)
npx code-master config --profile standard

# Strict (slowest, most thorough)
npx code-master config --profile strict

# Full (enterprise, all features)
npx code-master config --profile full
```

## First Run

Start with a simple review:

```bash
# Review a single file
npx code-master review src/index.ts

# Review a directory
npx code-master review src/

# Full audit
npx code-master audit src/ --full-report
```

## Integration Options

### Option 1: Pre-Commit Hook (Recommended)
```bash
npx code-master install-hooks
# Now runs on every commit
# Blocks commit if CRITICAL issues found
```

### Option 2: CI/CD Pipeline (GitHub Actions)
```yaml
- name: Code Analysis
  run: npx code-master audit src/ --fail-on-critical
```

### Option 3: Manual Workflow
```bash
# Before pushing
npx code-master review src/
npx code-master secure src/
```

## Troubleshooting

### Issue: "Command not found"
```bash
# Make sure node_modules/.bin is in PATH
export PATH="./node_modules/.bin:$PATH"

# Or use npm run
npm install -D code-master-pro
npm exec code-master -- review src/
```

### Issue: "Port already in use"
```bash
# Check running processes
lsof -i :9000

# Or specify different port
npx code-master --port 9001
```

### Issue: "Memory error on large codebase"
```bash
# Increase Node memory
NODE_OPTIONS=--max-old-space-size=4096 npx code-master audit src/

# Or limit scope
npx code-master review src/api/ --max-files=20
```

### Issue: "Git context not available"
```bash
# If not in git repo
npx code-master analyze src/ --no-git

# Or initialize git
git init && git add . && git commit -m "initial"
```

## Uninstall

```bash
# Remove from project
npm uninstall code-master-pro

# Remove global
npm uninstall -g code-master-pro

# Remove hooks
npx code-master uninstall-hooks
```

## Next Steps

1. ✅ Run `npx code-master --version` (verify installation)
2. ✅ Run `npx code-master review src/` (try basic command)
3. ✅ Read [README.md](./README.md) (learn all features)
4. ✅ Check [SKILL.md](./SKILL.md) (deep dive documentation)
5. ✅ Run `npx code-master audit src/` (run full analysis)

## Support

- 📖 **Documentation:** [README.md](./README.md)
- 🎯 **Quick Reference:** [SKILL.md](./SKILL.md)
- 🐛 **Report Issues:** [GitHub Issues](https://github.com/rehanumer00/code-master-pro/issues)
- 💬 **Ask Questions:** [GitHub Discussions](https://github.com/rehanumer00/code-master-pro/discussions)

---

**Installation complete! Your codebase now has enterprise-grade analysis.**
