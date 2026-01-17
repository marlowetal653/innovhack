# Brief - Context-First Development

> Fork de [GitHub Spec Kit](https://github.com/github/spec-kit) pour Innov Hack

**Brief** ajoute une couche de contexte intelligent a votre workflow de developpement. Avant toute action, l'agent AI verifie via le MCP Brief s'il a besoin de plus de contexte (business, code, architecture, etc.).

## Quick Start

### 1. Installer Brief dans votre projet

```bash
# Installation persistante (recommandee)
uv tool install brief-cli --from git+https://github.com/marlowetal653/innovhack.git

# Ou utilisation one-shot
uvx --from git+https://github.com/marlowetal653/innovhack.git brief init .
```

### 2. Initialiser votre projet

```bash
# Nouveau projet
brief init mon-projet --ai claude

# Projet existant
cd mon-projet
brief init . --ai claude
```

### 3. Configurer le MCP Brief

Ajoutez la configuration MCP dans votre fichier de config Claude Code:

**Linux/Mac**: `~/.config/claude-code/mcp.json`
**Windows**: `%APPDATA%\claude-code\mcp.json`

```json
{
  "mcpServers": {
    "brief-mcp": {
      "command": "npx",
      "args": ["-y", "brief-mcp", "--access-token", "VOTRE_TOKEN_MCP"]
    }
  }
}
```

## Comment ca marche

### La Regle Brief

Une fois installe, votre agent AI a une regle fondamentale:

> **Avant TOUTE action significative, verifier le contexte via brief-mcp**

Cela inclut:
- Ecrire ou modifier du code
- Creer des specs ou des plans
- Prendre des decisions d'architecture
- Implementer des features
- Fixer des bugs

### Le MCP Brief

Le MCP Brief contient le contexte accumule de votre projet:
- **Business** - Regles metier, requirements
- **Code** - Patterns, conventions, architecture
- **Decisions** - Pourquoi les choses sont faites ainsi
- **Domaine** - Terminologie, concepts
- **Contraintes** - Ce qu'on ne peut/doit pas faire

### Commandes Disponibles

```bash
# Verifier le contexte explicitement
/brief.context Je vais ajouter une feature de paiement

# Workflow spec-driven classique (avec check de contexte auto)
/speckit.constitution   # Principes du projet
/speckit.specify        # Creer une spec
/speckit.plan           # Planifier l'implementation
/speckit.tasks          # Decomposer en taches
/speckit.implement      # Implementer
```

## Pourquoi Brief?

### Le Probleme

Les agents AI codent souvent "a l'aveugle":
- Ils reinventent la roue
- Ils violent les patterns existants
- Ils oublient les regles metier
- Ils creent du code inconsistent

### La Solution

Brief force l'agent a **d'abord comprendre** avant d'agir:

```
1. User: "Ajoute un systeme de notifications"
2. Agent: *query brief-mcp*
   - "On a deja un systeme de messaging?"
   - "Quelles sont les conventions de notification?"
   - "Y a-t-il des contraintes de performance?"
3. Agent: *recoit le contexte*
4. Agent: *implemente en respectant le contexte*
```

## Structure du Projet

Apres `brief init`, votre projet contient:

```
.specify/
├── memory/
│   └── constitution.md     # Principes du projet
├── specs/
│   └── [features]/         # Specs par feature
├── templates/
│   ├── commands/           # Commandes slash
│   │   ├── brief.context.md    # Check de contexte
│   │   ├── specify.md          # Creer spec
│   │   └── ...
│   └── brief-rule.md       # Regle de contexte obligatoire
├── scripts/
│   ├── bash/
│   └── powershell/
└── mcp-config.json         # Template config MCP

.[agent]/                   # Fichiers specifiques a l'agent
└── commands/ or rules/
```

## Contribuer

1. Fork le repo
2. Creez une branche feature
3. Committez vos changements
4. Ouvrez une PR

## Credits

- [GitHub Spec Kit](https://github.com/github/spec-kit) - Le projet original
- Innov Hack Team

## License

MIT - Voir [LICENSE](LICENSE)
