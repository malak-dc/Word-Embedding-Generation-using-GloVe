
# Génération des Embeddings de Mots en Darija à l’aide de GloVe

## 📄 Description du projet

Ce projet a pour objectif de créer un modèle d'embeddings de mots pour le dialecte marocain, Darija, en utilisant l'algorithme **GloVe**. Les embeddings de mots permettent de représenter les mots sous forme de vecteurs dans un espace continu, capturant ainsi des relations syntaxiques et sémantiques. Le projet inclut également une application d'analyse de sentiments basée sur ces embeddings.

L’analyse des sentiments, l’une des applications principales de ce projet, consiste à extraire les opinions exprimées dans les textes en Darija. Ce dialecte est sous-représenté dans le traitement automatique des langues (TALN), ce qui motive le développement de ce modèle.

## 🛠️ Fonctionnalités

- **Scraping de données** : Extraction des commentaires YouTube et des articles du site goud.ma pour construire un corpus en Darija.
- **Prétraitement linguistique** : Tokenisation (BERT, NLTK), lemmatisation, et nettoyage des données textuelles pour faciliter la modélisation.
- **Modèle GloVe** : Génération des embeddings de mots à partir d’une matrice de co-occurrence basée sur le corpus prétraité.
- **Évaluation des embeddings** : Validation qualitative (proximité sémantique) et quantitative (tâches d'analyse de sentiments).
- **Application Flask** : Application web pour la prédiction des sentiments dans des textes en Darija.

## ⚙️ Installation

1. **Cloner le dépôt** :
   ```bash
   git clone https://github.com/votreutilisateur/darija-embeddings.git
   cd darija-embeddings
   ```

2. **Installer les dépendances** :
   ```bash
   pip install -r requirements.txt
   ```

3. **Exécuter le scraping et le prétraitement des données** :
   - Scraping des données :
     ```bash
     python src/scrape_data.py
     ```
   - Prétraitement des données :
     ```bash
     python src/preprocess.py
     ```

4. **Générer les embeddings avec GloVe** :
   ```bash
   python src/glove_model.py
   ```

## 📂 Structure du projet

```
.
├── data/               # Dossier contenant les données brutes et prétraitées
├── embeddings/         # Dossier contenant les embeddings générés
├── src/                # Scripts pour le scraping, prétraitement, génération d'embeddings et analyse
│   ├── scrape_data.py  # Script de scraping des données
│   ├── preprocess.py   # Script de prétraitement des données
│   ├── glove_model.py  # Script pour la génération du modèle GloVe
│   ├── sentiment_analysis.py  # Analyse des sentiments
├── app/                # Application Flask
│   ├── app.py          # Script pour lancer l'application Flask
│   ├── templates/      # Fichiers HTML pour l'interface utilisateur
└── README.md           # Documentation
```

## 📝 Prétraitement des données

### Scraping

Les données ont été extraites de deux principales sources :
- **Commentaires YouTube** : Représentant des dialogues spontanés en Darija.
- **Articles du site goud.ma** : Reflétant l'écriture formelle du dialecte marocain.

### Tokenisation

Deux techniques principales de **tokenisation** ont été utilisées pour préparer les données textuelles en vue de leur utilisation dans le modèle d’embeddings :

1. **Tokenization BERT** : 
   - Le modèle **BERT** utilise une technique de tokenisation appelée **WordPiece**, qui segmente les mots en sous-mots. Cela permet de gérer efficacement les variations linguistiques, notamment en Darija, qui inclut des emprunts et des néologismes.
   - Cette méthode segmente les mots rares en morceaux plus petits, capturant ainsi une meilleure représentation des mots dans le contexte du TALN.

2. **Tokenization NLTK** :
   - La bibliothèque **NLTK** effectue une tokenisation plus traditionnelle, divisant les phrases en mots basés sur les espaces et la ponctuation.
   - Cette approche, bien qu’efficace pour des structures simples, a montré ses limites pour des dialectes complexes comme le Darija.

### Lemmatisation

La **lemmatisation** permet de regrouper les différentes formes d'un mot sous une même entité appelée **lemme**. En Darija, cela a impliqué la normalisation des mots en fonction de leurs racines (généralement trilitères). Nous avons appliqué une méthode de "Light-stemming", adaptée aux spécificités du dialecte, pour éviter les ambiguïtés dues aux emprunts linguistiques.

### Nettoyage

Le nettoyage des données a consisté en :
- La suppression des caractères non pertinents (chiffres, symboles).
- La normalisation des formes lexicales.
- Le filtrage des commentaires et titres contenant des éléments non textuels.

## 🔄 Construction du modèle GloVe

Le modèle GloVe a été utilisé pour générer des embeddings de mots en se basant sur la **matrice de co-occurrence**. Cette matrice capture la fréquence à laquelle les mots apparaissent ensemble dans une fenêtre de contexte définie. Les embeddings résultants sont des vecteurs qui encodent les relations sémantiques entre les mots du corpus.

### Caractéristiques du modèle GloVe

- **Fenêtre de contexte** : La taille de la fenêtre a été optimisée pour capturer les relations de co-occurrence locales et globales.
- **Matricialisation** : La construction de la matrice de co-occurrence a permis de factoriser les relations sémantiques entre les mots proches, capturant ainsi leur signification.
- **Optimisation** : Les vecteurs de mots sont formés par la minimisation de la fonction de coût, ce qui permet de générer des embeddings robustes.

## 🧪 Évaluation des embeddings

L'évaluation des embeddings s'est faite de deux manières :

1. **Qualitative** : Analyse des relations sémantiques entre les mots proches dans l'espace vectoriel.
   - Exemple : Les mots proches de "amour" incluent "aimer" et "chérir" dans les embeddings obtenus.

2. **Quantitative** : Comparaison avec d'autres modèles d'embeddings et évaluation sur une tâche d'analyse de sentiments en Darija.

## 🚀 Utilisation

### Analyse de Sentiments

Pour effectuer une analyse de sentiments sur un texte en Darija, utilisez le script suivant :

```bash
python src/sentiment_analysis.py --text "Votre texte ici"
```

### Déploiement de l'application Flask

1. Lancer l'application Flask :
   ```bash
   python app/app.py
   ```

2. Ouvrir l'application dans votre navigateur à l'adresse suivante : `http://127.0.0.1:5000/`

## 👥 Auteurs

- Wiam Terrab
- Kaoutar Zouguagh
- Malak Berri

