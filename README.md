# Caricare Wiki

Questo è il repository del wiki di *Caricare* ospitato su GitHub Pages.

## Requisiti

Assicurati che sul tuo PC siano installati:

- [VS Code](https://code.visualstudio.com/) o un altro editor che supporti Markdown
- Git
- Node.js

## Installazione e avvio del server locale

1. **Clona il repository**

```bash
git clone https://github.com/carimali/wiki.git
```

2. **Apri il terminale nella cartella del progetto**

```bash
cd wiki
```

3. **Installa le dipendenze e Docsify CLI**

```bash
npm install
npm i docsify-cli -g
```

4. **Avvia il server locale**

```bash
docsify serve docs
```

5. **Avvia il server locale per  Windows**

```bash
npx docsify serve docs
```

Il wiki sarà accessibile su `http://localhost:3000`.

## Note aggiuntive

 
- Per aggiornare il wiki, modifica i file Markdown nella cartella `docs` e il server locale rifletterà automaticamente le modifiche.

