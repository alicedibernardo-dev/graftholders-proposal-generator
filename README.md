# GRAFTHOLDERS Proposal Generator

App statica in italiano: cliente, progetto, attività, quantità, prezzi, IVA, bozze nel browser, esportazione JSON e stampa/PDF. Non usa AI né un database remoto. Nessun dato cliente viene incluso nel repository.

## Cloudflare Workers con GitHub

1. Apri https://dash.cloudflare.com/ e vai in **Workers & Pages → Create application → Import a repository** (i nomi possono variare).
2. Autorizza l'app GitHub di Cloudflare per questo repository e seleziona il branch `main`.
3. Comando di build: lascia vuoto. Comando di deploy: `npx wrangler deploy`. Directory radice: `/`.
4. Pubblica e apri l'URL `workers.dev` restituito da Cloudflare.
5. Per un dominio già presente nel tuo account: Worker → Settings → Domains & Routes → Add → Custom Domain. Scegli il sottodominio desiderato e conferma. Il dominio deve essere sotto il tuo controllo; non è configurato da questo repository.

I push successivi a main vengono pubblicati dal collegamento Git di Cloudflare. Non inserire token nel repository. Questa configurazione non crea risorse D1, R2 o Workers AI e non richiede segreti applicativi.

## Sviluppo e verifica

Richiede Node.js 22 o successivo.

```sh
npm install
npm run check
npm run dev
```

Deploy manuale dopo autenticazione: `npx wrangler login`, poi `npm run deploy`.

## Dati

Le bozze sono salvate nel localStorage del singolo browser. JSON è un'esportazione di backup (importazione non ancora disponibile). Per il PDF scegli “Salva come PDF” nella finestra di stampa. I preventivi non sono condivisi o sincronizzati tra dispositivi. Rivedi dati fiscali e condizioni prima dell'invio.
