

**Génération des Embeddings de Mots en Darija à l’aide de GloVe**

---

### 🔍 **Description du Projet**

Ce projet a pour objectif de créer un modèle d'embeddings de mots pour le dialecte marocain, Darija, en utilisant l'algorithme GloVe. Les embeddings capturent les relations syntaxiques et sémantiques des mots, avec une application dans l'analyse des sentiments.

### 🎯 **Fonctionnalités Principales**
- **Scraping de données** : Extraction des commentaires YouTube et des articles du site goud.ma.
- **Prétraitement des données** : Nettoyage, tokenisation et lemmatisation.
- **Modèle GloVe** : Génération des embeddings à partir des co-occurrences de mots.
- **Évaluation des embeddings** : Qualitative et quantitative.
- **Analyse de sentiments** : Utilisation des embeddings pour un modèle d'analyse de sentiments en Darija.
- **Application Flask** : Interface pour prédire les sentiments.

---

### 🗂️ **Structure du Projet**

```
📂 data/               - Données brutes et prétraitées
📂 embeddings/         - Embeddings générés
📂 src/                - Scripts de scraping, prétraitement, génération d'embeddings et analyse
    ├── scrape_data.py     - Script de scraping
    ├── preprocess.py      - Script de prétraitement
    ├── glove_model.py     - Script pour le modèle GloVe
    ├── sentiment_analysis.py - Analyse de sentiments
📂 app/                - Application Flask
    ├── app.py             - Script pour lancer l'application
    ├── templates/         - Interface utilisateur (HTML)
📄 README.md           - Documentation
```

---

### ⚙️ **Installation**

1. **Cloner le dépôt** :
   ```bash
   git clone https://github.com/votreutilisateur/darija-embeddings.git
   cd darija-embeddings
   ```

2. **Installer les dépendances** :
   ```bash
   pip install -r requirements.txt
   ```

3. **Télécharger les données** : Récupérez les commentaires YouTube et les articles du site goud.ma.

4. **Exécuter le scraping et le prétraitement** :
   ```bash
   python src/scrape_data.py
   python src/preprocess.py
   ```

5. **Générer les embeddings GloVe** :
   ```bash
   python src/glove_model.py
   ```

---

### 🛠️ **Utilisation**

#### **1. Analyse des Sentiments**

Exécutez le modèle d'analyse de sentiments :
```bash
python src/sentiment_analysis.py --text "Votre texte ici"
```

#### **2. Déploiement de l'Application**

1. Lancez l'application Flask :
   ```bash
   python app/app.py
   ```

2. Ouvrez votre navigateur à : `http://127.0.0.1:5000/`

---

### 📊 **Résultats**

- **Évaluation qualitative** : Analyse des relations sémantiques entre les mots proches.
- **Évaluation quantitative** : Performances du modèle sur l'analyse de sentiments.

---

### 👥 **Auteurs**

- Malak Berri
- Wiam Terrab
- Kaoutar Zouguagh




