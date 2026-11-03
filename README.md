# 📊 BI Portfolio

Portfolio de mes projets de **Business Intelligence**, réalisés dans le cadre de ma formation à l'ENSIM (5ᵉ année).

Chaque projet a son propre dépôt GitHub, avec son code, son pipeline automatisé (GitHub Actions) et son tableau de bord en ligne (GitHub Pages).

## Projets

| # | Projet | Question métier | Technologies | Code | Démo |
|---|--------|-----------------|--------------|------|------|
| 1 | **EU Capitals Dashboard** | Quelle capitale de l'UE offre la meilleure météo la semaine prochaine, tout en limitant le CO₂ du trajet depuis Paris ? | Python, API météo, GitHub Actions, GitHub Pages | [Dépôt](https://github.com/omar-el-moujahid/eu-capitals-dashboard) | [Dashboard](https://omar-el-moujahid.github.io/eu-capitals-dashboard/) |
| 2 | **Smart Mobility Le Mans** | Avec des ressources limitées, où et quand Le Mans Métropole doit-elle améliorer en priorité son réseau de transport public ? | Python, pandas, GTFS, GTFS-RT, GitHub Actions, GitHub Pages, Chart.js | [Dépôt](https://github.com/omar-el-moujahid/Smart-Mobility-Le-Mans) | [Dashboard](https://omar-el-moujahid.github.io/Smart-Mobility-Le-Mans/) |

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

## Structure

```
bi-portfolio/          ← ce dépôt : la vitrine
eu-capitals-dashboard/ ← projet 1
...                    ← projets suivants
```

## Contact

- GitHub : [omar-el-moujahid](https://github.com/omar-el-moujahid)
