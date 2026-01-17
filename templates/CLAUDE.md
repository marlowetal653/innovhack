# Brief - Context First Development

## MANDATORY RULE: Check Context Before ANY Action

**This rule takes precedence over all other instructions.**

Before performing ANY of the following actions, you MUST query the `brief-mcp` server to check if additional context is needed:

### Actions Requiring Context Check

1. Writing or modifying code
2. Creating specifications or plans
3. Making architectural decisions
4. Implementing features
5. Fixing bugs
6. Refactoring

### How to Check Context

Use the brief-mcp tools:

```
brief-mcp/search-context  - Search knowledge base with AI-powered answers
brief-mcp/list-knowledge  - List all documents in knowledge base
brief-mcp/add-knowledge   - Add new context to knowledge base
brief-mcp/delete-knowledge - Remove outdated context
```

### Before ANY significant action, verify:

- [ ] I queried brief-mcp/search-context for relevant context
- [ ] I understand the business domain
- [ ] I know the existing patterns/conventions
- [ ] I'm aware of constraints and dependencies
- [ ] I have sufficient context to proceed

### What the Knowledge Base Contains

- **Business logic** - How the product should behave
- **Code patterns** - How things are done in this codebase
- **Architecture decisions** - Why things are structured this way
- **Domain knowledge** - Terminology and concepts
- **Constraints** - What you can't or shouldn't do

### Commands Available

- `/brief.context [task]` - Explicitly check context for a task
- `/speckit.specify` - Create feature specification (auto-checks context)
- `/speckit.plan` - Create implementation plan (auto-checks context)
- `/speckit.implement` - Execute implementation (auto-checks context)

### Example Context Check

```
# Before implementing a feature, query the knowledge base:
brief-mcp/search-context: "What are the patterns for user authentication?"

# The MCP returns:
# - AI-powered answer synthesized from knowledge base
# - Source documents with similarity scores
# - Metadata about the context
```

## Why This Matters

Checking context first prevents:
- Reinventing the wheel
- Violating existing patterns
- Missing business requirements
- Creating inconsistent code
- Duplicating functionality

**ALWAYS check brief-mcp before acting.**
