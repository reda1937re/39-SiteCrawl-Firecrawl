# SiteCrawl-Firecrawl

Outil d'exploration multi-pages. Utilise `firecrawl.crawl()`, qui part d'une URL de départ, suit ses liens internes et **scrape** chaque page visitée (contrairement à `map()` qui ne fait que lister). C'est l'appel Firecrawl le plus coûteux en crédits, la limite de pages est donc volontairement basse par défaut. Le contenu de toutes les pages visitées est envoyé à un agent Groq qui produit une fiche de synthèse du site : vue d'ensemble, thèmes principaux, pages notables, chaque point étant cité `[1]`, `[2]`...

## Fonctionnement

1. `crawl_site()` — appelle `firecrawl.crawl()`, scrape plusieurs pages, renvoie la liste des pages
2. `digest()` — orchestre : crawl le site puis demande au LLM la fiche de synthèse

## Tech stack

- **Streamlit** — interface web
- **Agno** — framework d'agent IA
- **Firecrawl** — exploration et scraping multi-pages (`crawl`)
- **Groq** (`openai/gpt-oss-120b`) — LLM de synthèse
- **Pydantic** — structure de données

## Lancer le projet

```bash
pip install -r requirements.txt
```

Créer un fichier `.env` avec :
```
GROQ_API_KEY=...
FIRECRAWL_API_KEY=...
```

```bash
streamlit run app.py
```
