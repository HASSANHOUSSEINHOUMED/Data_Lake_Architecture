# 🏗️ Data Lake Architecture - TP Final

**Matière** : Architecture Data Lake, Data Warehouse & Data Lakehouse  
**Établissement** : IPSSI Paris  
**Programme** : Mastère 2 Big Data & Intelligence Artificielle  
**Période** : Janvier 2026

Pipeline complet d'ingestion, transformation et analyse de données selon l'architecture **Medallion** (Bronze → Silver → Gold).

---

## 🎓 Objectif Pédagogique

Implémentation d'un **Data Lake production-ready** couvrant :
- **Ingestion** : Données brutes depuis PostgreSQL
- **Transformation** : Nettoyage, enrichissement, modélisation
- **Analyse** : KPIs, segmentation clients (RFM), visualisations
```
PostgreSQL (source)
    ↓
BRONZE (ingestion + métadonnées)
    ↓
SILVER (transformations : Dim/Fact tables)
    ↓
GOLD (KPIs, Revenue, RFM Analytics)
```

---

## 📁 Structure Livrable

| Phase | Responsable | Objectif | Livrables |
|-------|------------|----------|-----------|
| **Phase 1** | Meissa | Bronze Ingestion | 7 tables ingérées, métadonnées |
| **Phase 2** | Marcus | Silver Transformations | Dim_Customers, Dim_Products, Fact_Orders |
| **Phase 3-4** | Hedi | Streaming Integration | Simulation Kafka, Batch/Streaming merge |
| **Phase 5** | Hassan | Gold Analytics | KPIs Revenue, Analyse RFM, Dashboard |

---

## 🚀 Démarrage Rapide

### Prérequis
```bash
- Apache Spark 4.0.1
- Python 3.9+
- PostgreSQL 18
- JupyterLab
```

### Exécution
```bash
# 1. Démarrer l'environnement Docker
docker-compose up -d

# 2. Ouvrir JupyterLab
# http://localhost:8888

# 3. Ouvrir le notebook
notebooks/TP_FINAL_COMPLET.ipynb
```

---

## 📊 Architecture Implémentée

### **BRONZE** (Ingestion)
```
customers      → 91 lignes
orders         → 830 lignes
order_details  → 2,155 lignes
products       → 77 lignes
employees      → 9 lignes (bonus)
suppliers      → 29 lignes (bonus)
categories     → 8 lignes (bonus)

Métadonnées ajoutées :
+ _horodatage_ingestion
+ _systeme_source (postgresql/kafka)
+ _nom_table
+ _date_ingestion
```

### **SILVER** (Transformations)
```
Dim_Customers
- company_name: InitCap
- country: MAJUSCULES
- Jointures avec métadonnées

Dim_Products
- Calcul stock_status (CRITIQUE si <10)
- Jointure avec catégories
- Métadonnées techniques

Fact_Orders
- Jointure orders + order_details
- Calcul montant_net (unit_price * qty * (1-discount))
- Dedupliquées par (order_id, product_id)
```

### **GOLD** (Analytics)
```
KPI Revenue
- Chiffre d'affaires total
- Revenue par pays (Top 10)
- Revenue cumulatif

Analyse RFM
- Recency: Jours depuis dernière commande
- Frequency: Nombre de commandes
- Monetary: Valeur totale dépensée

Segmentation Clients:
- VIP (Q3)
- LOYAL (Q2-Q3)
- REGULAR (Q1-Q2)
- AT_RISK (<Q1)
```

---

## 📈 Résultats Clés

| Métrique | Valeur |
|----------|--------|
| **Tables ingérées** | 7 (4 obligatoires + 3 bonus) |
| **Lignes Bronze** | 3,199 |
| **Lignes Silver** | 2,155 (Fact_Orders) |
| **Clients actifs** | 91 |
| **Commandes** | 830 |
| **Revenue total** | ~$3M+ |
| **Segments RFM** | 4 catégories |
| **Dashboard** | ✅ 6 visualisations |

---

## 💻 Stack Technique

### Data Processing
- **Apache Spark 4.0.1** - Traitement distribué
- **PySpark** - API Python Spark
- **Parquet** - Format de stockage columnar

### Source & Storage
- **PostgreSQL 18** - Source de données
- **JDBC Connector** - Connexion Spark-PostgreSQL
- **File System Local** - Stockage Bronze/Silver/Gold

### Visualisation & Analytics
- **Matplotlib & Seaborn** - Graphiques statiques
- **Plotly** - Visualisations interactives (bonus)
- **Pandas** - Manipulation DataFrames

### Engineering
- **Docker** - Containerization
- **JupyterLab** - Notebook interactif
- **Git** - Versioning

---

## 📚 Technologies Maîtrisées

### Data Lake & Medallion Architecture
- ✅ Zone Bronze (ingestion raw)
- ✅ Zone Silver (transformations)
- ✅ Zone Gold (analytics)
- ✅ Partitionnement par date
- ✅ Métadonnées techniques

### ETL / ELT
- ✅ JDBC PostgreSQL
- ✅ Transformations PySpark (withColumn, select, join)
- ✅ Agrégations (groupBy, agg)
- ✅ Deduplications

### Data Warehouse Concepts
- ✅ Dimension Tables (Dim_Customers, Dim_Products)
- ✅ Fact Tables (Fact_Orders)
- ✅ Slow Changing Dimensions
- ✅ Star Schema

### Business Analytics
- ✅ KPIs Revenue
- ✅ RFM Segmentation
- ✅ Customer Analytics
- ✅ Dashboard Exécutif

---

## 👥 Équipe - Groupe 8

| Membre | Rôle | Phase(s) | Contribution |
|--------|------|----------|--------------|
| **Meissa** | Data Engineer | Phase 1 | Ingestion Bronze complète |
| **Marcus** | Data Transformer | Phase 2 | Transformations Silver (Dim/Fact) |
| **Hedi** | Streaming Specialist | Phase 3-4 | Simulation Kafka + Intégration |
| **Hassan** | Analytics & BI | Phase 5 | Gold KPIs + Dashboard + RFM |

---

## 📊 Progression Compétences

| Compétence | Phase 1 | Phase 2 | Phase 3-4 | Phase 5 |
|-----------|---------|---------|-----------|---------|
| **Data Ingestion** | ✅ | - | - | - |
| **ETL/Transformations** | - | ✅ | ✅ | - |
| **Streaming** | - | - | ✅ | - |
| **Data Modeling** | - | ✅ | - | - |
| **Analytics/KPIs** | - | - | - | ✅ |
| **Visualization** | - | - | - | ✅ |
| **Production-Ready** | ✅ | ✅ | ✅ | ✅ |

---

## 📁 Fichiers Livrés
```
TP_FINAL_COMPLET.ipynb   - Notebook complet (toutes phases)
TP_FINAL_COMPLET.pdf     - Version PDF
README.md                 - Ce fichier
```

---

## 🔍 Validation & Qualité

- ✅ **5/5 Phases complètes** et fonctionnelles
- ✅ **Métadonnées techniques** sur toutes les tables
- ✅ **Data lineage** traçable (source_system + table_name)
- ✅ **Partitionnement** par date d'ingestion
- ✅ **Dashboard exécutif** avec 6 visualisations
- ✅ **Code** professionnel et réutilisable

---

## 📞 Contact & Documentation

**Groupe 8 - Data Lake Architecture**
- 📧 Contact : hassan.houssein.houmed@gmail.com
- 🐙 GitHub : https://github.com/HASSANHOUSSEINHOUMED

---

**Dernière mise à jour** : Janvier 2026  
**Matière** : Architecture Data Lake, Data Warehouse & Data Lakehouse - Mastère 2