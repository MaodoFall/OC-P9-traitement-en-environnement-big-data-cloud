# 📊 Projet Big Data - Classification d'images de Fruits sur AWS

**Projet 9 – Mastère Spécialisé Data Science – OpenClassrooms**  
**Client : Fruits (start-up de l'Agritech)**  
**Rôle : Data Scientist**

---

## 🎯 Objectifs

L'objectif est de développer une architecture Big Data complète pour la start-up **"Fruits!"** de l'AgriTech, spécialisée dans les solutions innovantes pour la récolte des fruits. Le projet vise à créer une application mobile de reconnaissance de fruits par photographie pour sensibiliser le grand public à la biodiversité des fruits, tout en posant les bases d'un futur moteur de classification pour des robots cueilleurs intelligents.

### 1. Court terme
- Créer une application mobile grand public de reconnaissance de fruits par photographie
- Sensibiliser à la biodiversité des fruits

### 2. Long terme  
- Développer un moteur de classification d'images de fruits robuste
- Créer des robots cueilleurs intelligents

---

## 🗂️ Jeu de Données

- **Source** : [Kaggle - Dataset de fruits et légumes](https://www.kaggle.com/datasets/moltean/fruits) 
- **Volume** : 90483 images
- **Test set** : 22 688 images réparties dans 131 classes/variétés
- **Format** : Images 100x100 pixels
- **Classes** : Apple Braeburn, Banana, Kiwi, Watermelon, etc..

---

## 🏗️ Architecture Big Data

### Services AWS Utilisés

#### 🗄️ Amazon S3 (Simple Storage Service)
- **Rôle** : Stockage des données
- **Avantages** : 
  - Stockage illimité et élastique
  - Séparation du stockage et du calcul
  - Accès rapide et coût optimisé
  - Bucket utilisé : `p9-data-maodo`

#### ⚡ Amazon EMR (Elastic MapReduce)
- **Rôle** : Plateforme de calcul distribué
- **Type** : Platform as a Service (PaaS)
- **Avantages** :
  - Instances EC2 avec applications pré-installées
  - Intégration native avec S3
  - Facilité de gestion et scalabilité

#### 🔐 AWS IAM (Identity and Access Management)
- **Rôle** : Gestion sécurisée des identités et permissions
- **Fonction** : Contrôle d'accès aux ressources AWS

#### 📊 JupyterHub
- **Rôle** : Environnement de développement
- **Usage** : Développement et pilotage des notebooks

---

## 🔧 Chaîne de Traitement

### Technologies Utilisées
- **Apache Spark** : Moteur de traitement distribué
- **PySpark** : Interface Python pour Spark
- **MobileNetV2** : CNN pré-entraîné pour l'extraction de features
- **PCA** : Réduction de dimensionnalité
- **Format Parquet** : Stockage optimisé des résultats

### Étapes du Pipeline

1. **Chargement des Images**
   - Import des images depuis S3
   - Extraction des labels à partir des noms de dossiers

2. **Prétraitement**
   - Redimensionnement des images
   - Normalisation des données

3. **Extraction de Features**
   - Utilisation de MobileNetV2 pré-entraîné sur ImageNet
   - Transfer Learning pour une extraction rapide
   - Diffusion du modèle sur les workers via broadcast

4. **Réduction de Dimension**
   - Application de la PCA (Principal Component Analysis)
   - Optimisation de la dimensionnalité des features

5. **Stockage**
   - Sauvegarde des résultats au format Parquet dans S3
   - Architecture optimisée pour les requêtes futures

---

## 🚀 Installation et Configuration

### Prérequis
- Compte AWS avec permissions appropriées
- Python 3.8+
- Apache Spark 3.x

### Déploiement Cloud
1. **Création du cluster EMR**
   - Configuration via AWS Console ou CLI
   - Bootstrap actions pour les dépendances
   - Connexion SSH et configuration FoxyProxy

2. **Lancement du traitement**
   - Accès à JupyterHub via EMR
   - Exécution du notebook PySpark
   - Monitoring via Spark UI

---

## 📊 Résultats

- **Architecture scalable** : Prête pour l'augmentation du volume de données
- **Pipeline optimisé** : Traitement distribué efficient
- **Features extraites** : Base solide pour la classification
- **Stockage optimisé** : Format Parquet pour les performances

---

## 🔍 Monitoring et Performance

- **Spark UI** : Monitoring des jobs et performances
- **Historique des tâches** : Traçabilité complète
- **Métriques de performance** : Temps d'exécution et utilisation des ressources

---

## 📈 Perspectives d'Amélioration

- **Augmentation du dataset** : Intégration de nouvelles variétés de fruits
- **Optimisation des hyperparamètres** : Fine-tuning du modèle
- **Pipeline ML complet** : Intégration de l'entraînement de modèles

---

## 🏆 Compétences Développées

- Modélisation de données dans un environnement Big Data
- Réalisation de calculs distribués sur des données massives
- Sélection et utilisation d'outils Cloud adaptés
- Mise en œuvre d'architectures scalables

---

## 📞 Contact

**Maodo FALL**  
*Data Scientist* 

---

*Ce projet démontre la mise en place d'une architecture Big Data complète sur AWS, posant les bases techniques solides pour un futur moteur de reconnaissance de fruits dans un contexte d'AgriTech innovant.*
