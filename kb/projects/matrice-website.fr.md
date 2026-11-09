---
name: Matrice Website
year: 2026
tags: &a1
  - nextjs
  - react
  - typescript
  - supabase
repos:
  - name: matrice-website-v2
    role: author
    visibility: private
    description: Le site actuel de Matrice Technologies, refait en octobre 2026,
      avec pages de services, blog, espace d'équipe sur invitation et espaces
      clients (Next.js 16 + Supabase, auto-hébergé sur Coolify).
    year: 2026
    last_active: 2026-11
    language: TypeScript
    archived: false
    tags: *a1
  - name: matrice-website
    role: author
    visibility: private
    description: Première version du site de Matrice, avec une page d'accueil
      commerciale, un espace d'équipe sur invitation et des espaces clients qui
      affichent en direct les dépôts de mission (Next.js 16 + Supabase, couvert
      par Playwright et Vitest).
    year: 2026
    last_active: 2026-08
    language: TypeScript
    archived: false
    tags: *a1
---

Matrice Website regroupe le site public de Matrice Technologies et les espaces privés qui se trouvent derrière, répartis sur deux dépôts privés. `matrice-website` (de mai à août 2026) est la première version : une page d'accueil commerciale, un espace d'équipe sur invitation sous `/app` et, à partir de juillet 2026, des espaces clients. `matrice-website-v2` (commencé le 22 octobre 2026) est une refonte, et c'est aujourd'hui le site en ligne sur matricetechnologies.com : nouvelles pages de services et blog, avec l'espace privé et les espaces clients repris de la première version. Les deux sont des applications Next.js 16 / React 19 sur Supabase, testées avec Vitest et Playwright.

## What

La partie publique de la v2 comprend une page d'accueil, des pages de services (Ask Your Company, Build Your Academy, Build Your Digital Twin, Engineering), des pages à propos, partenaires et recrutement, ainsi qu'un blog d'articles sur le travail avec des agents, dont plusieurs avec des figures interactives ou des démonstrations jouables (par exemple « Planning with Agents », « Work 2.0 », « Introducing Wimym »). Les articles interactifs écrits pour la rubrique insights de la première version y ont été repris.

Un espace client, à l'adresse `matricetechnologies.com/clients/<slug>`, est un espace à accès restreint consacré à une mission de conseil. Son contenu se trouve dans le dépôt de mission du client (`content/` et `README.md`) et il est lu en direct depuis la branche `main` de ce dépôt : une fusion sur `main` publie une modification en quelques secondes, sans redéploiement du site. Un espace affiche la vue d'ensemble de la mission, le plan, les initiatives et les indicateurs clés, le volet commercial sous forme de phases chiffrées, les réunions, les documents (téléchargeables en PDF à la charte de Matrice), le modèle d'organisation du client, et une page Map qui représente les liens entre documents, réunions, phases et initiatives sous forme de graphe de forces. Les interlocuteurs du client y accèdent par le système d'invitation. Le contrat de rédaction destiné aux agents qui écrivent dans les dépôts de mission est publié sous `/clients/contribute/agents`, à côté d'un guide et d'un kit de démarrage pour les présentations commerciales.

L'espace `/app` sur invitation sert à l'équipe Matrice (base de connaissances, graphe, administration) : les administrateurs émettent et révoquent les invitations depuis `/app/admin` et, dans la v2, gèrent le registre des espaces clients depuis `/app/admin/repos`.

## Tech

Le contrôle d'accès vient de la première version : authentification Supabase avec des tables `profiles` et `invites` sous RLS strict, une fonction SECURITY DEFINER `consume_invite` qui marque une invitation comme utilisée de manière atomique, seulement si elle n'est ni révoquée, ni déjà utilisée, ni expirée et (lorsqu'elle est liée à un e-mail) si l'e-mail de l'utilisateur correspond, et un point d'accès interne qui supprime les comptes n'ayant jamais utilisé d'invitation. Pour les espaces clients, le site cherche dans un registre le dépôt et la branche de l'espace, télécharge l'archive du dépôt via l'API GitHub avec un jeton de GitHub App, construit l'espace à partir de cet instantané et le met en cache sous une étiquette propre à l'espace ; un webhook de push émis par la GitHub App invalide cette étiquette. Un mode local (`CLIENTS_LOCAL_<SLUG>`) sert un espace depuis une copie du dépôt sur disque pour les prévisualisations. Chaque dépôt de mission exécute en CI une vérification `validate-room` contre le contrat de rédaction ; le validateur de référence se trouve dans le dépôt du site et un test unitaire le maintient aligné sur les vrais constructeurs d'espaces. La première version gardait le registre dans un fichier JSON et était déployée sur Vercel. La v2 déplace le registre dans une table Supabase `client_repos` modifiable depuis l'administration, propose la connexion par Google et par e-mail, tourne sur un VPS déployé par Coolify avec une instance Supabase auto-hébergée, et imprime les PDF des documents via Gotenberg. L'interface utilise Tailwind 4, Base UI et shadcn/ui, avec d3 pour les graphes.

## Status

La v2 est le site en ligne, avec un travail actif jusqu'en novembre 2026, surtout sur les articles du blog. La première version n'a plus reçu de commit depuis août 2026. Les deux dépôts sont privés et internes à Matrice.

## Articles

Le blog est à l'adresse [matricetechnologies.com/blog](https://matricetechnologies.com/blog). Ses huit articles, de juillet à novembre 2026, ont chacun leur fiche dans la collection Articles de cette base de connaissances.
