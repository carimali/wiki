# Technology Stack

- **Frontend**: Docsify 4.8.6 (documentation generator), Vanilla JavaScript
- **Build tools**: Rollup 0.53.3, Stylus 0.54.7, npm-run-all 4.1.5
- **Libraries**: marked 4.0.10 (Markdown parser), prismjs 1.18.0 (syntax highlighting), medium-zoom 0.4.0, handlebars 4.5.3
- **Testing**: ESLint 6.8.0
- **Other tools**: npm, lerna 3.20.2 (monorepo), live-server 1.2.1


## Workflow

```
Checklist → Piano → Modalità → Implementazione
```

1. **Checklist**: Verifica implementazioni simili, stack, blocchi
2. **Piano**: Sequenza sintetica (obbligatorio pre-code)
3. **Modalità**: Junior (step-by-step) | Senior (rapido) | RALPH (autonomo)
4. **Implementazione**: Pattern reuse, testing quando rilevante

---

## Linee guida di STILE

### Comunicazione
- Risposte concise e dirette con esempi pratici
- Formattazione minima (elenchi puntati solo se necessari)
- Per task complessi: chiedere conferma prima di creare un piano dettagliato

### Codice
- **Nessun commento** – codice autoesplicativo con nomi chiari
- Commenti ammessi solo per: logica complessa, algoritmi non ovvi, decisioni architetturali
- Naming: `camelCase` (metodi/variabili), `PascalCase` (classi/componenti)
- Principi: SOLID, DRY, Single Responsibility


### Modalità Piano

- Piano estremamente conciso. Sacrificare la grammatica a favore della sintesi.
- Alla fine di ogni piano, fornire una lista di domande irrisolte, se presenti.



## Storage

- Piani: `~/.claude/plans/[nome].md`
- Progress: `progress/[nome]_progress.md` (agent crea dir al primo task)

---

See @assets/CLAUDE.BASE.md
