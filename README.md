# 🏗️ Data Lake Architecture - TP Final

---

## 📌 Contexte

**Projet** : Pipeline Data Lake complet selon l'architecture **Medallion**  
**Matière** : Architecture Data Lake, Data Warehouse & Data Lakehouse - Mastère 2  
**Type** : Projet en équipe (4 personnes)  
**Stack** : PySpark 4.0.1 + PostgreSQL + Parquet + Streaming Kafka  

Pipeline production-ready couvrant **ingestion** (Bronze) → **transformations** (Silver) → **analytics** (Gold) pour une base e-commerce complète (Northwind).

---

## 👥 Équipe & Contributions

| Rôle | Personne | Spécialité |
|------|----------|-----------|
| **Phase 1** | Meissa | Bronze Ingestion (PostgreSQL) |
| **Phase 2** | Marcus | Silver Transformations (Dim/Fact) |
| **Phase 3-4** | Hedi | Streaming & Intégration Batch/Streaming |
| **Phase 5** 🔥 | **Hassan HOUSSEIN HOUMED** | Gold Analytics + KPIs + RFM + Dashboard |

---

## 🎯 Mon Rôle : Data Analytics - Phase 5 (Gold Layer)

J'ai conçu et implémenté **la couche Gold complète** : KPIs métier, segmentation clients RFM et dashboard analytique.

### 💰 KPIs Revenue Implémentés

**Indicateurs clés de performance calculés** :

| KPI | Description | Résultat |
|-----|-------------|----------|
| **Chiffre d'affaires Total** | Montant total des commandes | ~$1.3M |
| **Top 10 Pays par Revenue** | Répartition géographique | USA, France, Germany en tête |
| **Revenue Cumulatif** | Tendance croissante | Visualisation par pays |
| **Panier Moyen** | Ticket moyen | $1,565 |

### 👥 Analyse RFM - Segmentation Clients

**Modèle de segmentation 4 segments** basé sur :

- **Recency** (R) : Jours depuis dernière commande
- **Frequency** (F) : Nombre de commandes
- **Monetary** (M) : Valeur totale dépensée

**Résultats segmentation** :

| Segment | Description | Clients | Stratégie |
|---------|-------------|---------|-----------|
| **VIP** | Q3+ monetary (très haute valeur) | ~23 | Fidélisation premium |
| **LOYAL** | Q2-Q3 (fidèles réguliers) | ~23 | Rewards & upsell |
| **REGULAR** | Q1-Q2 (clients normaux) | ~23 | Engagement standard |
| **AT_RISK** | <Q1 (à risque) | ~22 | Winback campaigns |

---

## 📊 Dashboard Exécutif - 6 Visualisations

J'ai créé un **dashboard complet** avec Matplotlib/Seaborn :

1. **Top 10 Pays par Revenue** (Bar chart horizontal)
2. **Distribution Segmentation RFM** (Pie chart)
3. **Distribution Recency** (Histogramme)
4. **Frequency vs Monetary Value** (Scatter plot)
5. **Revenue Cumulatif** (Line chart + fill)
6. **Résumé Exécutif** (Table KPIs clés)

---

## 🔄 Flux de Données Complet (Medallion)
```
PostgreSQL (Northwind)
    ↓ [PHASE 1 - Meissa]
BRONZE (ingestion brute)
    ├─ customers (91 lignes)
    ├─ orders (830 lignes)
    ├─ order_details (2,155 lignes)
    ├─ products (77 lignes)
    └─ + métadonnées (_horodatage_ingestion, _systeme_source, etc.)
    
    ↓ [PHASE 2 - Marcus]
SILVER (transformations dimensionnelles)
    ├─ Dim_Customers (InitCap, MAJUSCULES)
    ├─ Dim_Products (stock_status, categories)
    └─ Fact_Orders (montant_net calculé)
    
    ↓ [PHASE 3-4 - Hedi]
STREAMING + INTEGRATION
    ├─ Kafka simulation (50 messages)
    └─ Batch + Streaming merge
    
    ↓ [PHASE 5 - Hassan] 🔥
GOLD (analytics & KPIs)
    ├─ Revenue Analysis (KPIs, pays, cumulatif)
    ├─ RFM Segmentation (4 segments clients)
    └─ Dashboard (6 visualisations + résumé)
```

---

## 🛠️ Stack Technique

### **Big Data & Processing**
- ![Apache Spark](https://img.shields.io/badge/Apache%20Spark-E25A1C?style=flat-square&logo=apache-spark&logoColor=white) - Traitement distribué PySpark 4.0.1
- ![Parquet](https://img.shields.io/badge/Parquet-FF6B6B?style=flat-square) - Format columaire optimisé
- ![Hadoop](https://img.shields.io/badge/Hadoop-66CCFF?style=flat-square&logo=apache-hadoop&logoColor=white) - Stockage distribué

### **Source & Intégration**
- ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=flat-square&logo=postgresql&logoColor=white) - Base source Northwind
- ![JDBC](https://img.shields.io/badge/JDBC-FF9800?style=flat-square) - Connecteur Spark-PostgreSQL
- ![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat-square&logo=apache-kafka&logoColor=white) - Streaming simulé

### **Analytics & Visualization**
- ![Matplotlib](https://img.shields.io/badge/Matplotlib-1f77b4?style=flat-square) - Graphiques statiques
- ![Seaborn](https://img.shields.io/badge/Seaborn-9467bd?style=flat-square) - Visualisations statistiques
- ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) - Manipulation DataFrames

### **Infrastructure**
- ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) - Containerization
- ![JupyterLab](https://img.shields.io/badge/JupyterLab-F37726?style=flat-square&logo=jupyter&logoColor=white) - Notebook interactif
- ![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white) - Version control

---

## 🚀 Lancement du Projet

### **Démarrer l'infrastructure**
```bash
docker-compose up -d
```
→ Lance PostgreSQL, Spark, JupyterLab, Kafka, MinIO

### **Ouvrir le notebook**
```
http://localhost:8888
notebooks/TP_FINAL_COMPLET.ipynb
```

### **Exécuter les phases dans l'ordre**
```
Phase 1: Ingestion Bronze (7 tables)
    ↓
Phase 2: Transformations Silver (Dim/Fact)
    ↓
Phase 3-4: Streaming Kafka + Intégration
    ↓
Phase 5: Gold Analytics + RFM + Dashboard
```

---

## 💡 Décisions Architecturales Justifiées

### **1. Architecture Medallion (Bronze → Silver → Gold)**

| Couche | Objectif | Avantage |
|--------|----------|----------|
| **Bronze** | Ingestion brute | Source unique de vérité (SoT) |
| **Silver** | Transformations | Données propres, standardisées |
| **Gold** | Analytics | Prête pour consommation métier |

✅ **Justification** : Séparation des responsabilités, traçabilité complète, scalabilité.

### **2. Métadonnées Techniques Obligatoires**
```python
_horodatage_ingestion  # Quand
_systeme_source        # D'où (postgresql/kafka)
_nom_table            # Quoi
_date_ingestion       # Partitionnement
```

✅ **Justification** : Data governance, audit trail, reproductibilité.

### **3. Parquet pour le Stockage**

| Format | Compression | Requêtes | Choix |
|--------|------------|----------|-------|
| CSV | Non | Lente | ❌ |
| JSON | Moyenne | Moyenne | ⚠️ |
| **Parquet** | ✅ 5-10× | ✅ Rapide | ✅ |

✅ **Justification** : Compression, performance analytique, standard Big Data.

### **4. RFM Segmentation basée sur Quartiles**
```python
VIP     = Q3+ monetary
LOYAL   = Q2-Q3
REGULAR = Q1-Q2
AT_RISK = <Q1
```

✅ **Justification** : Segment équilibrés, adapter stratégies marketing par groupe.

---

## 📈 Résultats & Impact

**Données traitées** :
- 7 tables ingérées (4 obligatoires + 3 bonus)
- 3,199 lignes brutes
- 2,155 lignes fact_orders après transformations

**KPIs produits** :
- Chiffre d'affaires : ~$1.3M
- Clients actifs : 91
- Commandes : 830
- Taux conversion : Excellent

**Segmentation clients** :
- 4 segments RFM générés
- Clients VIP identifiés
- Stratégies marketing différenciées

**Qualité pipeline** :
- ✅ 100% fiabilité (0 perte données)
- ✅ Métadonnées complètes (traçabilité)
- ✅ Format optimisé (Parquet)
- ✅ Code production-ready

---

## 🎓 Compétences Démontrées

- ✅ **Architecture Data Lake** (Medallion pattern)
- ✅ **Spark SQL & PySpark** (ingestion, transformations, agrégations)
- ✅ **Data Modeling** (Dim/Fact tables, star schema)
- ✅ **Analytics & KPIs** (Revenue, RFM, segmentation)
- ✅ **Data Visualization** (Matplotlib, Seaborn, 6 graphiques)
- ✅ **Data Governance** (métadonnées, audit trail)
- ✅ **ETL/ELT patterns** (batch & streaming)
- ✅ **Collaboration équipe** (4 personnes, phases dépendantes)

---

## 📂 Fichiers Livrés
```
TP_FINAL_COMPLET.ipynb   - Notebook complet (5 phases)
TP_FINAL_COMPLET.pdf     - Version PDF
README.md                - Documentation projet
```

---

## 👤 Auteur - Phase 5

**Hassan HOUSSEIN HOUMED**  
📚 Mastère 2 Big Data & Intelligence Artificielle - IPSSI Paris  
📧 hassan.houssein.houmed@gmail.com  
🐙 GitHub : https://github.com/HASSANHOUSSEINHOUMED

---

<div align="center">

**Dernière mise à jour** : Janvier 2026  
**Matière** : Architecture Data Lake, Data Warehouse & Data Lakehouse

</div>
