Projet accessible sous GitHub:
https://github.com/christophesallessacareau-boop/traitement_images_semi_supervis-es  

le projet contient 2 notebooks:  
-code d'extraction des images zippées: 1_extract_zip.ipynb  
-code principal: main.ipynb   

Classification d'IRM cérébrales:  
  
-modèles de clustering  

-modele CNN:  
Détection de cancers du cerveau par apprentissage semi-supervisé sur images IRM,  
avec un dataset mixte : images labelisées (cancer / normal) et images NON labelisées:  
50 images labelisées cancer  
50 images labelisées normal  
1400 images NON labelisées

mapping des labels:  
0=normal  
1=cancer

Versions testées :  
Python 3.12.8,  
TensorFlow 2.17.0,  
scikit-learn 1.5.1  
voir fichier requirements.txt pour les autres bibliothèques

Métriques évaluées:  
Recall: Taux de détection des cancers (à maximiser)  
False Negatives: Cancers manqués (cas le plus critique)  
False Positives: Fausses alarmes  
F1 macro: arbitrage faux négatifs vs faux positifs (à maximiser)

Pipeline:
1. Chargement (CV2) & préprocessing des images
2. Analyse non supervisée-Extraction de features via ResNet50 (PCA, t-SNE, clustering)
3. CNN baseline (keras.Sequential)
4. Transfer learning ResNet50 + data augmentation
5. Pseudo-labeling des images non labelisées
6. Entraînement semi-supervisé itératif
7. Évaluation finale et courbes