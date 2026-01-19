# Stack Tecnologico

- **Frontend**: Docsify (generatore documentazione), Vanilla JavaScript
- **Build tools**: Rollup, Stylus, npm-run-all
- **Librerie**: marked (Markdown parser), prismjs (syntax highlighting), medium-zoom, handlebars
- **Testing**: ESLint
- **Altri strumenti**: npm, lerna (monorepo), live-server


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



