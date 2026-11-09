# 📊 BI Portfolio

Portfolio de mes projets de **Business Intelligence**, réalisés dans le cadre de ma formation à l'ENSIM (5ᵉ année).

Chaque projet a son propre dépôt GitHub, avec son code et son tableau de bord en ligne (GitHub Pages). Les pipelines sont automatisés avec GitHub Actions lorsque le projet s'y prête.

## Projets

| # | Projet | Question métier | Technologies | Code | Démo |
|---|--------|-----------------|--------------|------|------|
| 1 | **EU Capitals Dashboard** | Quelle capitale de l'UE offre la meilleure météo la semaine prochaine, tout en limitant le CO₂ du trajet depuis Paris ? | Python, API météo, GitHub Actions, GitHub Pages | [Dépôt](https://github.com/omar-el-moujahid/eu-capitals-dashboard) | [Dashboard](https://omar-el-moujahid.github.io/eu-capitals-dashboard/) |
| 2 | **Smart Mobility Le Mans** | Avec des ressources limitées, où et quand Le Mans Métropole doit-elle améliorer en priorité son réseau de transport public ? | Python, pandas, GTFS, GTFS-RT, GitHub Actions, GitHub Pages, Chart.js | [Dépôt](https://github.com/omar-el-moujahid/Smart-Mobility-Le-Mans) | [Dashboard](https://omar-el-moujahid.github.io/Smart-Mobility-Le-Mans/) |
| 3 | **Scraping to KPI** | Quelles compétences techniques ressortent le plus dans un échantillon d'offres d'emploi ? | Python, Ollama (LLM local), GitHub Pages, Chart.js | [Dépôt](https://github.com/omar-el-moujahid/Web-scraping-and-converting-unstructured-text-into-a-measurable-KPI) | [Dashboard](https://omar-el-moujahid.github.io/Web-scraping-and-converting-unstructured-text-into-a-measurable-KPI/) |
| 4 | **CO2 Time Series** | Comment transformer une série de CO₂ bruitée en information exploitable, et jusqu'où peut-on la projeter honnêtement ? | Python, API Open-Meteo, GitHub Actions, GitHub Pages, Chart.js | [Dépôt](https://github.com/omar-el-moujahid/td-time-series) | [Dashboard](https://omar-el-moujahid.github.io/td-time-series/) |

## Détail des projets

### 1. EU Capitals Dashboard

**Objectif :** aider un voyageur parti de Paris à choisir une destination parmi 26 capitales européennes, en équilibrant deux critères : la qualité de la météo prévue et les émissions de CO₂ du trajet.

**Pipeline BI :**

1. **Acquisition** : table de référence des capitales (coordonnées GPS) et prévisions météo récupérées via une API, en une seule requête groupée pour plus de fiabilité.
2. **Nettoyage et calcul** : distance depuis Paris et estimation du CO₂ (facteur de 0,15 kg CO₂e/km, valeur arrondie issue de facteurs d'émission de type DEFRA).
3. **Scoring** : normalisation min-max de chaque critère, puis combinaison en un score unique qui classe les capitales.
4. **Automatisation** : un workflow GitHub Actions recalcule le classement et versionne le résultat (`rankings.json`, avec un horodatage `generated_at`).
5. **Restitution** : un dashboard publié sur GitHub Pages avec la recommandation, des graphiques et la date de dernière mise à jour.

**Points abordés :** fiabilité de l'acquisition, provenance des données, différence entre mesure et KPI, fraîcheur des données.

### 3. Scraping to KPI

**Objectif :** transformer le texte libre d'offres d'emploi en un indicateur mesurable, en explicitant les choix et les limites de sa construction.

**Pipeline BI :**

1. **Acquisition** : constitution locale d'un échantillon d'offres d'emploi, en tenant compte des règles d'accès et de réutilisation des données.
2. **Structuration** : extraction des compétences techniques de chaque offre avec un LLM local (Ollama).
3. **Qualité** : contrôle des résultats, notamment les variantes de casse, les oublis, les hallucinations et les écarts entre deux exécutions.
4. **KPI** : calcul de la part des offres mentionnant une compétence choisie et classement des compétences les plus fréquentes.
5. **Restitution** : publication sur GitHub Pages des seuls résultats agrégés, les offres brutes restant en local.

**Points abordés :** provenance et droits de réutilisation, place d'un LLM dans un pipeline, contrôle humain, KPI comme construction, limites d'un petit échantillon.

### 4. CO2 Time Series

**Objectif :** analyser 90 jours de CO₂ atmosphérique modélisé au Mans, lisser la série et produire une projection courte en affichant clairement ses limites.

**Pipeline BI :**

1. **Acquisition** : récupération de données horaires de CO₂ via l'API Air Quality d'Open-Meteo, puis calcul de moyennes journalières.
2. **Nettoyage** : réindexation sur chaque jour du calendrier et signalement des jours manquants, sans les remplir silencieusement.
3. **Modélisation** : moyenne mobile sur 7 jours, lissage exponentiel et projection linéaire à 7 jours.
4. **Automatisation** : un workflow GitHub Actions hebdomadaire actualise les données et versionne les résultats.
5. **Restitution** : un dashboard sur GitHub Pages présente la série, les courbes lissées, la projection et une note sur ses limites.

**Points abordés :** données modélisées et mesures réelles, détection des valeurs manquantes, comparaison des méthodes de lissage, limites d'une projection, comportement du pipeline en cas d'échec.
## Structure

```
bi-portfolio/                  ← ce dépôt : la vitrine
eu-capitals-dashboard/         ← projet 1
Smart-Mobility-Le-Mans/        ← projet 2
Web-scraping-and-converting-unstructured-text-into-a-measurable-KPI/  ← projet 3
td-time-series/                ← projet 4
```

## Contact

- GitHub : [omar-el-moujahid](https://github.com/omar-el-moujahid)
