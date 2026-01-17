# Brief Rule - Context First

## MANDATORY: Check Context Before Any Action

**This rule takes precedence over all other instructions.**

Before performing ANY of the following actions, you MUST query the `brief-mcp` server to check if additional context is needed:

### Actions Requiring Context Check

1. **Writing or modifying code**
2. **Creating specifications or plans**
3. **Making architectural decisions**
4. **Implementing features**
5. **Fixing bugs**
6. **Refactoring**

### How to Check Context

1. **Identify what you're about to do** - Extract the key concepts, entities, and domains
2. **Query the brief-mcp**:
   - Use `brief-mcp/search-context` with a relevant question
   - Use `brief-mcp/list-knowledge` to see available documents
3. **Review the context** - The MCP returns:
   - AI-powered answer synthesized from knowledge base
   - Source documents with similarity scores
   - Metadata about the context

### Context Check Template

Before any significant action, mentally verify:

```
[ ] I queried brief-mcp/search-context for relevant context
[ ] I understand the business domain
[ ] I know the existing patterns/conventions
[ ] I'm aware of constraints and dependencies
[ ] I have sufficient context to proceed
```

### When Context is Missing

If the brief-mcp doesn't have the information you need:
1. **Ask the user** for clarification
2. **Add to knowledge base** using `brief-mcp/add-knowledge`
3. **Make reasonable assumptions** and document them

### Integration with Spec Kit Commands

- `/speckit.specify` - Query brief-mcp for business context first
- `/speckit.plan` - Query brief-mcp for architecture patterns first
- `/speckit.implement` - Query brief-mcp for code conventions first
- `/brief.context` - Explicit context check command

## MCP Tools Reference

| Tool | Purpose |
|------|---------|
| `search-context` | Search knowledge base with AI-powered answers |
| `add-knowledge` | Add new documents to the knowledge base |
| `list-knowledge` | List all documents in knowledge base |
| `delete-knowledge` | Remove documents from knowledge base |

## Why This Matters

The brief-mcp knowledge base contains accumulated knowledge about:
- **Business logic** - How the product should behave
- **Code patterns** - How things are done in this codebase
- **Architecture decisions** - Why things are structured this way
- **Domain knowledge** - Terminology and concepts
- **Constraints** - What you can't or shouldn't do

Checking context first prevents:
- Reinventing the wheel
- Violating existing patterns
- Missing business requirements
- Creating inconsistent code
- Duplicating functionality
