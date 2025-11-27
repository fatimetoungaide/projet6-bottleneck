# Projet 6 — Analyse E-commerce (Bottleneck)

## Objectif du projet
Analyser les données commerciales d’une entreprise de vente de vin en fusionnant trois sources différentes :
- le fichier ERP (produits, coûts, marges),
- le fichier Web (prix affichés sur le site),
- le fichier Liaison (correspondance entre product_id et id_web).

Objectifs :
- nettoyer et préparer les données,
- résoudre les problèmes de doublons, valeurs manquantes et formats incorrects,
- fusionner correctement les trois sources,
- calculer des indicateurs clés (CA, marge, stock),
- produire une analyse descriptive sur les produits.

## Outils utilisés
- Python : pandas, numpy
- Visualisation : plotly, matplotlib
- Excel : vérifications, tri, formules
- SQL : compréhension des jointures et clés

## Nettoyage et préparation des données
- Conversion des colonnes au bon format (prix en string → float).
- Harmonisation des identifiants (sku → id_web).
- Détection et suppression des doublons.
- Gestion des valeurs manquantes dans id_web (91 lignes identifiées).
- Alignement des colonnes entre ERP, Web et Liaison.

## Fusion des données
### Étape 1 : ERP + Liaison
Jointure sur product_id  
→ LEFT JOIN  
→ Conserver tous les produits ERP, même sans id_web.

### Étape 2 : Fusion + Web
Jointure sur id_web  
→ INNER JOIN  
→ Garder seulement les produits ayant une correspondance complète ERP ↔ Web.

Résultat final :
- 714 produits complets
- 91 produits sans id_web (exclus de la fusion finale)

## Analyses réalisées
### 1. Analyse produits
- Calcul du CA par produit
- Calcul du taux de marge
- Comparaison prix ERP vs prix Web
- Classement :
  - produits à forte marge
  - produits à faible marge
  - produits non rentables
- Analyse du stock :
  - rotation
  - produits dormants
  - surstock

### 2. Analyses statistiques simples
- CA par type de produit
- Répartition des ventes
- Identification des outliers (boxplots)

### 3. Visualisations
- Barres horizontales (CA, marge)
- Boxplots (prix, marge)
- Graphiques de comparaison prix/marge

## Résultats principaux
- 91 produits sans correspondance détectés
- Catégories les plus rentables identifiées
- Détection de produits à très faible marge
- Identification de produits dormants et en surstock
- Amélioration de la cohérence des bases via nettoyage

## Contenu du repository
- notebooks/ : notebook d’analyse
- data/ : échantillons ERP, Web, Liaison
- README.md : documentation du projet


