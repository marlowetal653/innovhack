---
description: Check if additional context is needed before proceeding with any task. Uses the brief-mcp to search the knowledge base for relevant project context (business, code, architecture, etc.).
tools: ['brief-mcp/search-context', 'brief-mcp/list-knowledge', 'brief-mcp/add-knowledge']
priority: high
---

## User Input

```text
$ARGUMENTS
```

## Purpose

This command **MUST** be invoked before any significant action to ensure you have all necessary context about the project. The brief-mcp knowledge base contains:

- Business context and requirements
- Code architecture and patterns
- Technical decisions and rationale
- Domain knowledge
- Team conventions

## Outline

1. **Analyze the current task**: What are you about to do?
   - Extract key concepts, entities, and domains from the task
   - Identify what knowledge might be needed

2. **Query the knowledge base for context**:
   - Use `brief-mcp/search-context` with a relevant question
   - Example: "What are the business rules for [feature]?"
   - Example: "What patterns do we use for [domain]?"

3. **Review the response**:
   - The MCP returns an AI-powered answer with sources
   - Check the similarity scores and metadata
   - Identify if the context is sufficient

4. **If context is missing or incomplete**:
   - List existing knowledge with `brief-mcp/list-knowledge`
   - Ask the user if they want to add missing context
   - Use `brief-mcp/add-knowledge` to store new context for future use

5. **Report context status**:
   ```markdown
   ## Context Check Results

   **Task**: [What you're about to do]

   ### Retrieved Context
   - [Summary of what the MCP returned]
   - Sources: [List sources with similarity scores]

   ### Context Gaps
   - [List any missing information]

   ### Ready to Proceed
   - [ ] Business context understood
   - [ ] Code patterns identified
   - [ ] Constraints known
   - [ ] Dependencies mapped
   ```

6. **Proceed only when context is sufficient**

## Integration with Other Commands

This command should be automatically invoked before:
- `/speckit.specify` - Need business context
- `/speckit.plan` - Need architectural context
- `/speckit.implement` - Need code patterns and conventions
- Any code modification - Need existing patterns

## Example Usage

```
/brief.context I need to add a payment feature

# Calls brief-mcp/search-context with:
# "What are the requirements and patterns for payment features?"

# Returns context about:
# - Existing payment integrations
# - Business rules for payments
# - Security requirements
# - Related features
```

## MCP Tools Reference

| Tool | Purpose |
|------|---------|
| `search-context` | Search knowledge base with AI-powered answers |
| `add-knowledge` | Add new documents to the knowledge base |
| `list-knowledge` | List all documents in knowledge base |
| `delete-knowledge` | Remove documents from knowledge base |
