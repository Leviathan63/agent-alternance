# Agent alternance

Workflow [n8n](https://n8n.io) qui cherche chaque jour à 8h des offres d'alternance (réseau, télécom, cybersécurité, admin systèmes) autour de ta ville, les note avec une IA locale (Ollama) et envoie les meilleures (score ≥ 3/5) sur Discord.

## Sources
- La Bonne Alternance (api.apprentissage.beta.gouv.fr)
- Google Jobs via SerpAPI

## Installation
1. Dans n8n : **Import from file** → `agent-alternance.json`
2. **Renseigner ta localisation** (voir ci-dessous)
3. Créer les 2 credentials (Header Auth pour La Bonne Alternance, Query Auth pour SerpAPI) et les sélectionner dans les nœuds HTTP
4. Configurer Ollama et le webhook Discord
5. Tester avec **Execute workflow**, puis activer le workflow

## À personnaliser

| Nœud | Paramètre | Valeur à mettre |
|---|---|---|
| La Bonne Alternance | `latitude` | Latitude de ta ville (ex. `48.8566`) |
| La Bonne Alternance | `longitude` | Longitude de ta ville (ex. `2.3522`) |
| La Bonne Alternance | `radius` | Rayon de recherche en km (défaut : `30`) |
| La Bonne Alternance | `romes` | Codes [ROME](https://www.francetravail.fr/candidat/en-savoir-plus/le-code-rome.html) des métiers visés (défaut : réseau/télécom/systèmes) |
| Google Jobs (SerpAPI) | `location` | Ta ville, ex. `Paris, Île-de-France, France` |
| Google Jobs (SerpAPI) | `q` | Mots-clés de recherche |
| Nœud IA (prompt) | `TA_FORMATION`, `TON_ANNEE`, `TA_VILLE`, `TES_COMPETENCES` | Ta formation (ex. `BUT Réseaux et Télécommunications`), ton année (ex. `2e année`), ta ville et tes compétences (ex. `Cisco, routage, VLAN, cybersécurité`) |

Pour trouver les coordonnées d'une ville : clic droit sur le lieu dans Google Maps, la latitude et la longitude s'affichent en premier.

## Licence
[MIT](LICENSE)
