# Projet SIG - Classification LULC Sentinel-2 (Richard Toll)

Ce projet regroupe un workflow de classification d'occupation du sol (LULC) a partir d'images Sentinel-2 sur la zone de Richard Toll, avec comparaison de modeles de machine learning (Random Forest / SVM) et production de cartes finales.

## Objectifs

- Extraire des variables spectrales utiles (bandes + indices).
- Entrainer et comparer des classifieurs supervises.
- Produire des sorties cartographiques et des metriques de performance.
- Permettre une analyse multi-annees (2015 et 2025).

## Structure actuelle

- `scripts_optimise.ipynb` : notebook principal (pipeline complet).
- `README.md` : documentation du projet.

## Donnees attendues (local)

Le workflow utilise notamment :

- des rasters Sentinel-2 (10 bandes),
- des echantillons de reference par annee (`DB_2015`, `DB_2025` en Shapefile),
- des dossiers de sortie pour les cartes et rapports.

## Environnement recommande

- Python 3.10+
- `numpy`, `pandas`
- `geopandas`, `rasterio`
- `matplotlib`, `seaborn`
- `scikit-learn`
- `jupyterlab` (pour le notebook)

Exemple d'installation :

```bash
python -m venv sig_env
source sig_env/bin/activate
pip install numpy pandas geopandas rasterio matplotlib seaborn scikit-learn jupyterlab
```

## Execution

### Option notebook (principal)

```bash
jupyter lab scripts_optimise.ipynb
```

Puis executer les cellules dans l'ordre :
chargement -> indices spectraux -> extraction echantillons -> entrainement/evaluation -> classification complete -> visualisations/export.

## Classes LULC utilisees

- Eau
- Bati
- Sols cultives
- Jachere
- Sols nus
- Zones humides

## Sorties generees (selon configuration)

- composites RGB / fausses couleurs,
- cartes d'indices (NDVI, SAVI, NDWI, MNDWI, BSI, NDRE),
- matrices de confusion,
- importance des variables,
- raster de classification final,
- tableaux de scores (CSV) et resume (JSON).

## Points d'attention

- Plusieurs chemins dans les scripts/notebooks sont absolus et doivent etre adaptes a votre machine.
- Les donnees raster volumineuses ne sont generalement pas versionnees dans Git.
