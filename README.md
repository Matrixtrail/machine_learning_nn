# Projet de Transfer Learning avec PyTorch

Ce projet présente un exemple d’entraînement d’un modèle de transfer learning (ResNet-18 préentraîné) pour classer des images d’animaux. Il utilise PyTorch, TorchVision et quelques bibliothèques courantes pour le traitement d’images et l’entraînement de modèles.

---

## Structure du dépôt

```plaintext
├── animals/
│   ├── elephant/
│   ├── gorilla/
│   ├── leopard/
│   ├── lion/
│   ├── panda/
│   └── rhinoceros/
├── requirement.txt
├── dataset.csv
├── transfer_learning.py
└── README.md
```
- **animals/** : Dossier contenant les 6 classes d’images (elephant, gorilla, leopard, lion, panda, rhinoceros).  
- **dataset.csv** : Fichier CSV contenant éventuellement des informations sur chaque image (chemin d’accès, label, etc.).  
- **transfer_learning.py** : Script principal qui :
  - Sépare les données en ensembles d’entraînement (train) et de validation (val)
  - Met en place les transformations d’images
  - Définit et entraîne deux modèles ResNet-18
  - Affiche des exemples de prédictions
  - Sauvegarde le modèle final

---

## Prérequis

- Python 3.x  
- PyTorch  
- TorchVision  
- NumPy, Matplotlib, etc.

Pour installer les dépendances principales (exemple via pip) :
```bash
pip install -r requirement.txt
```

---

## Utilisation

1. Clonez ce dépôt ou téléchargez les sources :
```bash
   git clone https://github.com/Matrixtrail/machine_learning_nn.git
   cd machine_learning_nn
```

2. Préparez le dataset :
   - Assurez-vous d’avoir les dossiers d’images à l’intérieur de animals/.
   - Vérifiez que dataset.csv est bien présent si nécessaire.

3. Lancez le script d’entraînement :
```bash
   python transfer_learning.py
```
   Le script va :
   - Créer un répertoire data/ (s’il n’existe pas) pour répartir les images en data/train/ et data/val/.
   - Entraîner deux modèles :
     - model_ft (toutes les couches entraînables)
     - model_conv (couches gelées, sauf la dernière)
   - Afficher la perte (loss) et la précision (accuracy) à chaque époque d’entraînement.
   - Sauvegarder les modèles (full_model_ft.pth et full_model_conv.pth).

4. Visualisez les résultats :
   - Le script affichera quelques images de validation avec leurs prédictions pour vérifier les performances.
   - Les mesures de précision et de perte finale sont affichées dans le terminal.

---

## Personnalisation

- Classes : Pour utiliser d’autres classes, placez simplement les dossiers correspondants dans animals/.
- Split train/val : Ajustez la valeur train_ratio=0.8 si vous souhaitez modifier la proportion train/validation.
- Nombre d’époques : Modifiez la variable num_epochs lors de l’appel à train_model.
