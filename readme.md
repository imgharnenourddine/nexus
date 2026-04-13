<div align="center">

# ⚡ NEXUS
### *Intelligent Supply Chain Agent for Industrial Hardware*

<br/>

> **"From supplier to client — fully automated, fully intelligent."**

<br/>

[![FastAPI](https://img.shields.io/badge/FastAPI-0.115-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Next.js](https://img.shields.io/badge/Next.js-14-000000?style=for-the-badge&logo=next.js&logoColor=white)](https://nextjs.org)
[![Mistral](https://img.shields.io/badge/Mistral-AI_Agent-FF7000?style=for-the-badge&logo=mistral&logoColor=white)](https://mistral.ai)
[![XGBoost](https://img.shields.io/badge/XGBoost-Fine--tuned-ED7D31?style=for-the-badge&logo=python&logoColor=white)](https://xgboost.ai)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Aiven-336791?style=for-the-badge&logo=postgresql&logoColor=white)](https://aiven.io)

<br/>

**Industrial Challenge 2026 · Supply Chain & AI · Agentic AI**

</div>

---

## 📖 Table des matières

- [Pourquoi Nexus ?](#-pourquoi-nexus-)
- [Le contexte du hackathon](#-le-contexte-du-hackathon)
- [Le problème qu'on résout](#-le-problème-quon-résout)
- [L'entreprise simulée — TechBuild](#-lentreprise-simulée--techbuild)
- [Ce que Nexus fait](#-ce-que-nexus-fait)
- [Le flux complet de bout en bout](#-le-flux-complet-de-bout-en-bout)
- [Les 12 modules détaillés](#-les-12-modules-détaillés)
- [Les 2 interfaces](#-les-2-interfaces)
- [Les modèles ML — XGBoost Fine-tuné](#-les-modèles-ml--xgboost-fine-tuné)
- [Architecture technique](#-architecture-technique)
- [Stack technique](#-stack-technique)
- [Structure du projet](#-structure-du-projet)
- [Installation & Setup](#-installation--setup)
- [Variables d'environnement](#-variables-denvironnement)
- [Division des tâches — 5 développeurs](#-division-des-tâches--5-développeurs)
- [Roadmap MVP 3 jours](#-roadmap-mvp-3-jours)
- [Script de démo jury](#-script-de-démo-pour-le-jury)

---

## 💡 Pourquoi Nexus ?

**Nexus** vient du latin *"nectere"* qui signifie **lier, connecter, tisser ensemble**.

En anglais moderne, le mot *nexus* désigne **le point central qui relie plusieurs éléments entre eux** — le nœud qui connecte tout ce qui l'entoure.

Une supply chain industrielle c'est exactement ça — une chaîne de connexions entre des entités qui ne se parlent pas naturellement :

```
Fournisseurs (Taiwan, Corée, Chine)
        ↕
    Entrepôt
        ↕
   Production
        ↕
  Transporteurs
        ↕
    Clients
        ↕
  Retours & SAV
```

Aujourd'hui, chaque maillon fonctionne séparément. La communication est manuelle, lente, et sujette aux erreurs. Des informations se perdent entre chaque étape.

**Nexus est le point central intelligent qui connecte tous ces maillons automatiquement.** Il écoute, prédit, décide, agit — et relie chaque acteur de la chaîne en temps réel, sans friction.

Le nom n'est pas décoratif. Il décrit exactement ce que le système fait.

---

## 🌍 Le contexte du hackathon

**Industrial Challenge 2026** — thème Supply Chain & AI :

> *"Leverage AI and digital technologies to predict needs, optimize logistics flows, and streamline warehouse operations in increasingly complex industrial environments."*

| Ce que le hackathon demande | Ce que Nexus fait |
|---|---|
| **Predict needs** | XGBoost prédit rupture stock + commandes clients à 30 jours |
| **Optimize logistics flows** | Sélection auto fournisseur + transporteur + gestion retours |
| **Streamline warehouse operations** | Stock temps réel + emplacements + inspection retours |
| **AI and digital technologies** | Mistral LLM + XGBoost ML + FastAPI + Next.js |
| **Complex industrial environments** | Multi-fournisseurs, multi-transporteurs, multi-clients, SAV |

---

## 🎯 Le problème qu'on résout

Les PME industrielles dans le secteur hardware gèrent leur supply chain **manuellement** :

- Le responsable achats surveille les stocks sur Excel
- Il envoie des emails à la main à chaque fournisseur
- Il compare les devis dans un tableau Word
- Il génère les bons de commande un par un
- Il choisit un transporteur sans analyse objective
- Il gère les retours clients par email sans traçabilité
- Il ne sait pas ce que ses clients vont commander la semaine prochaine

**Les conséquences réelles :**

| Problème | Impact |
|---|---|
| Rupture de stock composants | Production arrêtée, clients perdus |
| Surstock | Capital immobilisé inutilement |
| Mauvais choix fournisseur | Coûts élevés, retards fréquents |
| Mauvais choix transporteur | Livraisons tardives, produits endommagés |
| Retours clients non tracés | Pertes financières, insatisfaction clients |
| Zéro visibilité prédictive | Réaction après coup, jamais en avance |

---

## 🏭 L'entreprise simulée — TechBuild

> **TechBuild** — PME de 200 employés spécialisée dans l'assemblage et la distribution de PC et serveurs industriels au Maroc.

Ce secteur est choisi délibérément : la pénurie mondiale de semiconducteurs de 2021-2023 a montré exactement ce qu'un système comme Nexus aurait pu éviter — des usines arrêtées pendant des mois faute de prédiction et d'anticipation.

### Les composants gérés (matières premières)

```
├── Processeurs Intel Core i7 / i9       (unités)
├── Processeurs AMD Ryzen 7 / 9          (unités)
├── RAM DDR5 16GB / 32GB                 (unités)
├── SSD NVMe 1TB / 2TB                   (unités)
├── Cartes mères ASUS / MSI              (unités)
├── GPU NVIDIA RTX 4070 / 4090           (unités)
├── Alimentations 750W / 1000W           (unités)
├── Boîtiers ATX Mid / Full Tower        (unités)
└── Câbles et visserie                   (lots)
```

### Les produits finis assemblés

```
├── PC Gaming Standard   → i7 + RTX 4070 + 16GB + 1TB SSD
├── PC Gaming Premium    → i9 + RTX 4090 + 32GB + 2TB SSD
├── PC Workstation       → Ryzen 9 + 64GB + 4TB SSD
├── Serveur Entry Level  → Xeon + 128GB + 10TB HDD
└── PC Bureau Entreprise → i5 + 16GB + 512GB SSD
```

### Les fournisseurs de composants

```
├── IntelDistrib    — processeurs Intel     (Taiwan,    délai moyen 21j)
├── AMDSupply       — processeurs AMD       (Chine,     délai moyen 18j)
├── KingstonPro     — RAM DDR5              (Hong Kong, délai moyen 14j)
├── SamsungSSD      — stockage NVMe         (Corée,     délai moyen 16j)
├── AsusWholesale   — cartes mères          (Taiwan,    délai moyen 20j)
├── NvidiaPartner   — GPU RTX               (Singapour, délai moyen 25j)
└── LocalElec       — câbles et accessoires (Maroc,     délai moyen 3j)
```

### Les transporteurs

```
├── DHL Express      — express nationale + internationale (délai 1j, fiabilité 98%)
├── Aramex           — standard nationale + internationale (délai 2j, fiabilité 95%)
├── FedEx            — premium internationale (délai 1j, fiabilité 97%)
├── CTM Messagerie   — économique nationale (délai 3j, fiabilité 88%)
└── Amana Express    — locale Maroc (délai 2j, fiabilité 91%)
```

### Les clients

```
├── EduTech Maroc    — universités et écoles        (pic septembre)
├── CyberArena       — cybercafés et gaming centers  (pic novembre)
├── CorpIT Solutions — entreprises                   (pic janvier)
├── DataCenter MA    — datacenters                   (trimestriel)
└── Particuliers     — via portail client             (pic Black Friday)
```

---

## ⚙️ Ce que Nexus fait

Nexus est un **agent IA autonome** qui gère 5 cycles simultanément :

```
CYCLE 1 — PRÉDICTION & APPROVISIONNEMENT FOURNISSEUR
XGBoost prédit les besoins → appel d'offre auto → négociation → commande

CYCLE 2 — COMMANDES CLIENTS
Client commande → vérification stock → production → transporteur → livraison

CYCLE 3 — SÉLECTION TRANSPORTEUR
Agent compare → sélection auto → email confirmation → tracking client

CYCLE 4 — GESTION DES RETOURS
Client initie retour → analyse motif → décision auto → ramassage → résolution

CYCLE 5 — SURVEILLANCE CONTINUE
Stock temps réel → alertes → recommandations → actions automatiques
```

---

## 🔄 Le flux complet de bout en bout

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DÉCLENCHEUR A — XGBoost PRÉDIT UNE RUPTURE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ML prédit : GPU RTX 4090 → rupture dans 8 jours
ML prédit : CyberArena va commander 20 PC dans 5 jours
Agent : stock insuffisant pour absorber la demande prédite
Agent déclenche automatiquement le flux d'approvisionnement
        ↓
DÉCLENCHEUR B — CLIENT PASSE UNE COMMANDE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CyberArena commande 20 PC Gaming Premium via portail client
        ↓
Agent vérifie stock produits finis
    ┌── Stock OK → sélection transporteur directement
    └── Stock insuffisant → ordre de production déclenché
        ↓
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ÉTAPE 1 — VÉRIFICATION MATIÈRES PREMIÈRES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

├── GPU RTX 4090   → 3/20  → INSUFFISANT ❌
├── i9 Processeur  → 5/20  → INSUFFISANT ❌
├── RAM 32GB       → 45/20 → OK ✅
├── SSD 2TB        → 30/20 → OK ✅
└── Cartes mères   → 25/20 → OK ✅

2 appels d'offre déclenchés simultanément
        ↓
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ÉTAPE 2 — APPEL D'OFFRE + NÉGOCIATION FOURNISSEURS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Mistral génère et envoie emails à 3 fournisseurs
Agent lit réponses IMAP → extrait prix/délai/conditions
XGBoost prédit retard par fournisseur
Tableau comparatif généré automatiquement
Budget dépassé → contre-offre automatique → acceptée ✅
Responsable valide en 1 clic → Bon de commande PDF envoyé
        ↓
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ÉTAPE 3 — SUIVI LIVRAISON FOURNISSEUR
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Relances automatiques J+1, J+5, date promise
Magasinier confirme réception → stock mis à jour
Score fournisseur recalculé → production débloquée
        ↓
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ÉTAPE 4 — PRODUCTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

20 PC Gaming Premium assemblés
Stock produits finis mis à jour
        ↓
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ÉTAPE 5 — SÉLECTION AUTOMATIQUE DU TRANSPORTEUR
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Agent analyse : destination Casablanca, 120kg, client urgent

┌──────────────────┬──────────┬───────┬───────────┬──────────────┐
│ Transporteur     │ Prix     │ Délai │ Fiabilité │ Score global │
├──────────────────┼──────────┼───────┼───────────┼──────────────┤
│ DHL Express      │ 850 MAD  │ 1j    │ 98%       │ ⭐⭐⭐⭐⭐    │
│ Aramex           │ 620 MAD  │ 2j    │ 95%       │ ⭐⭐⭐⭐      │
│ FedEx            │ 920 MAD  │ 1j    │ 97%       │ ⭐⭐⭐⭐      │
│ CTM Messagerie   │ 380 MAD  │ 3j    │ 88%       │ ⭐⭐⭐        │
│ Amana Express    │ 450 MAD  │ 2j    │ 91%       │ ⭐⭐⭐        │
└──────────────────┴──────────┴───────┴───────────┴──────────────┘

Client urgent → DHL Express sélectionné
Email confirmation enlèvement envoyé automatiquement
Numéro tracking transmis à CyberArena
        ↓
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ÉTAPE 6 — LIVRAISON & CONFIRMATION CLIENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Livraison effectuée → CyberArena confirme réception
Facture PDF générée automatiquement
Score DHL + score CyberArena mis à jour
        ↓
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ÉTAPE 7 — RETOUR CLIENT (si applicable)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CyberArena signale 1 PC Gaming Premium défectueux
        ↓
Mistral analyse le motif → responsabilité fournisseur GPU
        ↓
Client VIP + montant < seuil → retour approuvé AUTO
        ↓
Agent sélectionne Aramex pour ramassage
Email envoyé client + email envoyé transporteur
        ↓
Produit reçu → magasinier inspecte → défectueux confirmé
        ↓
    ┌── Remplacement → nouveau PC prélevé du stock
    ├── Remboursement → note de crédit PDF générée
    └── Réparation → ticket production créé
        ↓
Score NvidiaPartner pénalisé
Dashboard : "3 retours GPU ce mois → défaut série possible"
Rapport de cycle complet archivé
```

---

## 📦 Les 12 modules détaillés

### Module 1 — Gestion des stocks intelligente
- Stock composants avec **emplacement physique** (Zone, Rangée, Étagère)
- Stock produits finis assemblés
- Seuils critiques configurables par composant
- **XGBoost prédit rupture à 30 jours**
- Alertes temps réel dashboard + email
- Historique complet des mouvements de stock

### Module 2 — Prédiction des commandes clients (ML)
- Analyse historique commandes par client et par segment
- **XGBoost prédit volume et timing des prochaines commandes**
- Détection saisonnalité (rentrée, Black Friday, fin Q1)
- Alerte proactive avant même que le client commande
- Déclenchement automatique approvisionnement anticipé

### Module 3 — Portail client (interface séparée)
- Catalogue produits finis avec prix et disponibilité
- Passer une commande en ligne
- Suivi commande temps réel avec numéro de tracking
- **Initier et suivre un retour produit**
- Historique complet commandes + retours
- Emails automatiques à chaque étape

### Module 4 — Gestion de la production
- Ordre de production déclenché automatiquement
- Vérification automatique des composants disponibles
- Statut de production temps réel
- Notification automatique responsable production
- Réintégration des produits retournés réparables

### Module 5 — Gestion des fournisseurs
- Annuaire fournisseurs avec historique complet
- **Score dynamique = fiabilité délai (40%) + prix (35%) + qualité (25%)**
- **XGBoost prédit retard probable avant chaque commande**
- **Score pénalisé automatiquement si retour défectueux lié à ce fournisseur**
- Blacklist automatique si score sous le seuil configuré

### Module 6 — Appel d'offre automatique fournisseurs
- **Mistral génère l'email professionnel** selon composant et quantité
- Envoi simultané à N fournisseurs
- Relance automatique si pas de réponse en 24h
- Historique complet des appels d'offre

### Module 7 — Analyse des devis & négociation fournisseurs
- **Mistral extrait automatiquement** prix, délai, quantité depuis emails IMAP
- Tableau comparatif avec score global et retard prédit ML
- **Contre-offre automatique** si prix > budget configuré
- Recommandation justifiée en langage naturel

### Module 8 — Commande fournisseur & documents
- Validation humaine en 1 clic
- **Bon de commande PDF généré automatiquement**
- Budget mensuel configurable avec contrôle automatique
- Historique et archivage complet

### Module 9 — Sélection automatique du transporteur
- Annuaire transporteurs avec **tarifs fixes par zone et par poids**
- Score transporteur = fiabilité (40%) + prix (35%) + délai (25%)
- Sélection automatique selon priorité client + budget + destination
- **Email de confirmation enlèvement** automatique au transporteur
- Numéro de tracking transmis au client automatiquement
- **Score pénalisé si retour pour produit endommagé transport**

### Module 10 — Suivi livraison fournisseur intelligent
- Statuts automatiques planifiés (J+1, J+5, date promise)
- Alerte pré-commande si risque de retard prédit
- Relances urgentes automatiques si retard constaté
- Proposition fournisseur alternatif en cas de blocage
- Confirmation réception manuelle magasinier

### Module 11 — Gestion des retours clients ⭐ *nouveau*
- Client initie le retour depuis le portail avec motif déclaré
- **Mistral analyse le motif** et identifie la responsabilité automatiquement :
  - *Endommagé transport* → réclamation automatique au transporteur
  - *Produit défectueux* → score fournisseur pénalisé + alerte défaut série
  - *Mauvais produit* → erreur interne identifiée
  - *Annulation* → traitement immédiat si non expédié
- **Décision automatique** selon score client et montant :
  - Client VIP + montant faible → approuvé sans validation humaine
  - Client standard → validation responsable commercial
  - Motif suspect → escalade directeur
- **Sélection transporteur retour** automatique pour ramassage
- Email étiquette retour envoyé au client automatiquement
- Inspection à réception par le magasinier
- **Résolution automatique** : remplacement / remboursement / réparation
- Facture avoir PDF générée automatiquement si remboursement
- **Détection défaut série** : alerte si 3+ retours même composant même mois
- Score fournisseur + score transporteur mis à jour après chaque retour

### Module 12 — Dashboard & agent conversationnel
- Vue directeur : KPIs globaux temps réel via WebSocket
- Graphes : stock, prédictions, fournisseurs, transporteurs, taux de retour
- Alertes actives centralisées avec actions rapides
- Rapport mensuel automatique (économies, retours, incidents, KPIs)
- **Agent Mistral conversationnel :**
  - *"Quel est le taux de retour ce mois ?"*
  - *"Quel fournisseur a le plus de retours défectueux ?"*
  - *"Quel transporteur a le plus de produits endommagés ?"*
  - *"Prépare un appel d'offre pour 50 unités de RAM DDR5"*

---

## 🖥️ Les 2 interfaces

### Interface Client (portail séparé)
```
├── /login              → Connexion client
├── /dashboard          → Commandes en cours + statuts + tracking
├── /catalogue          → Catalogue produits finis + prix
├── /commande/nouveau   → Passer une nouvelle commande
├── /commande/{id}      → Suivi détaillé + tracking transporteur
├── /retours/nouveau    → Initier un retour produit  ⭐
├── /retours/{id}       → Suivre mon retour          ⭐
└── /historique         → Commandes + retours passés ⭐
```

### Interface Entreprise (portail interne)
```
├── /login
├── /dashboard                → KPIs globaux + alertes temps réel
├── /stock
│   ├── /composants           → Stock + emplacements physiques
│   └── /produits-finis       → Stock assemblés
├── /clients
│   ├── /commandes            → Commandes entrantes
│   ├── /predictions          → Prédictions ML
│   └── /annuaire             → Fiche client + score
├── /production
│   ├── /demandes             → Ordres en cours
│   └── /historique
├── /fournisseurs
│   ├── /annuaire             → Score + prédiction retard ML
│   ├── /appels-offre         → En cours + comparaison
│   └── /commandes            → Suivi livraisons
├── /transporteurs
│   ├── /annuaire             → Tarifs + score + historique
│   └── /livraisons           → En cours + tracking
├── /retours                              ⭐
│   ├── /en-attente           → À traiter
│   ├── /inspection           → Produits reçus à inspecter
│   ├── /historique           → Tous les retours
│   └── /qualite              → Taux retour par produit/fournisseur
├── /analytics
│   ├── /predictions          → Graphes rupture + commandes
│   ├── /performance          → KPIs supply chain
│   ├── /qualite              → Analyse retours + défauts série ⭐
│   └── /rapports             → Rapports mensuels
└── /agent                    → Chat Mistral
```

### Les rôles et accès

| Rôle | Accès |
|---|---|
| **Directeur** | Tout + validation retours escaladés |
| **Responsable Achats** | Fournisseurs + appels d'offre + commandes |
| **Responsable Commercial** | Clients + commandes + validation retours standards |
| **Responsable Production** | Production + réparations retours |
| **Magasinier** | Stock + réceptions + inspection retours |
| **Client** | Portail client séparé |

---

## 🤖 Les modèles ML — XGBoost Fine-tuné

### Pourquoi XGBoost

XGBoost est le modèle le plus utilisé en industrie pour les prédictions sur données tabulaires. Rapide, précis, interprétable — parfait pour expliquer au jury pourquoi telle prédiction a été faite. Fine-tuning avec **Optuna** sur datasets Kaggle réels.

---

### Modèle 1 — Prédiction rupture de stock

**Datasets Kaggle :**

| Dataset | Commande |
|---|---|
| DataCo Smart Supply Chain | `kaggle datasets download -d shashwatwork/dataco-smart-supply-chain` |
| Product Demand Forecast | `kaggle datasets download -d chakradharmattapalli/product-demand-forecast` |
| Online Retail Dataset | `kaggle datasets download -d abiodunonadeji/online-retail-dataset` |

```python
features = [
    'stock_actuel', 'consommation_moyenne_7j', 'consommation_moyenne_30j',
    'commandes_en_cours', 'saisonnalite_mois', 'jour_semaine',
    'tendance_consommation', 'historique_ruptures_passees'
]
target = 'jours_avant_rupture'
```

---

### Modèle 2 — Prédiction retard fournisseur

**Datasets Kaggle :**

| Dataset | Commande |
|---|---|
| Supply Chain Shipment Pricing | `kaggle datasets download -d divyeshardeshana/supply-chain-shipment-pricing-data` |
| E-Commerce Shipping Dataset | `kaggle datasets download -d prachi13/customer-churn-for-e-commerce` |

```python
features = [
    'fournisseur_id', 'pays_origine', 'delai_promis_jours',
    'historique_retard_moyen', 'taux_retard_fournisseur',
    'quantite_commandee', 'mois_annee', 'score_actuel_fournisseur'
]
target = 'retard_jours'
```

---

### Modèle 3 — Prédiction commandes clients

**Datasets Kaggle :**

| Dataset | Commande |
|---|---|
| E-commerce Sales Data | `kaggle datasets download -d carrie1/ecommerce-data` |
| Retail Sales Forecasting | `kaggle datasets download -d manjeetsingh/retaildataset` |
| Electronics Sales | `kaggle datasets download -d kuchhbhi2001/electronic-component-sales` |

```python
features = [
    'client_id', 'segment_client', 'volume_derniere_commande',
    'jours_depuis_derniere_commande', 'moyenne_commandes_30j',
    'mois_annee', 'evenement_saisonnier', 'tendance_croissance_client'
]
target = 'volume_predit_30j'
```

---

### Pipeline ML

```python
import optuna
from xgboost import XGBRegressor
from sklearn.metrics import mean_absolute_error
import joblib

def objective(trial):
    params = {
        'n_estimators': trial.suggest_int('n_estimators', 100, 1000),
        'max_depth': trial.suggest_int('max_depth', 3, 10),
        'learning_rate': trial.suggest_float('learning_rate', 0.01, 0.3),
        'subsample': trial.suggest_float('subsample', 0.6, 1.0),
        'colsample_bytree': trial.suggest_float('colsample_bytree', 0.6, 1.0)
    }
    model = XGBRegressor(**params)
    model.fit(X_train, y_train)
    return mean_absolute_error(y_val, model.predict(X_val))

study = optuna.create_study(direction='minimize')
study.optimize(objective, n_trials=100)

best_model = XGBRegressor(**study.best_params)
best_model.fit(X_train, y_train)
joblib.dump(best_model, 'ml/models/model.pkl')

# Endpoints FastAPI
# GET /api/v1/predictions/stock/{composant_id}
# GET /api/v1/predictions/retard/{fournisseur_id}
# GET /api/v1/predictions/clients
```

---

## 🏗️ Architecture technique

```
┌──────────────────────────────────────────────────────────────┐
│              PORTAIL CLIENT (Dev 4)                           │
│         Next.js 14 + Tailwind + shadcn/ui                    │
│     Commandes · Suivi tracking · Retours clients             │
└───────────────────────┬──────────────────────────────────────┘
                        │
┌──────────────────────────────────────────────────────────────┐
│              PORTAIL ENTREPRISE (Dev 3)                       │
│    Next.js 14 + Tailwind + shadcn/ui + Recharts              │
│  Stock · Fournisseurs · Transporteurs · Retours · Analytics  │
└───────────────────────┬──────────────────────────────────────┘
                        │ REST API + WebSocket
┌───────────────────────▼──────────────────────────────────────┐
│                    BACKEND FastAPI                            │
│                                                               │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌───────────────┐  │
│  │   Auth   │ │  Stock   │ │ Clients  │ │  Fournisseurs  │  │
│  │  (Dev 1) │ │  (Dev 1) │ │  (Dev 2) │ │    (Dev 2)     │  │
│  └──────────┘ └──────────┘ └──────────┘ └───────────────┘  │
│                                                               │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌───────────────┐  │
│  │Production│ │Transportr│ │  Retours │ │   Analytics   │  │
│  │  (Dev 1) │ │  (Dev 2) │ │  (Dev 2) │ │    (Dev 1)    │  │
│  └──────────┘ └──────────┘ └──────────┘ └───────────────┘  │
│                                                               │
│  ┌─────────────────────────────────────────────────────┐    │
│  │              AGENT MISTRAL LLM (Dev 2)               │    │
│  │  Génération emails · Analyse devis · Négociation     │    │
│  │  Analyse motifs retours · Chat conversationnel       │    │
│  └─────────────────────────────────────────────────────┘    │
│                                                               │
│  ┌─────────────────────────────────────────────────────┐    │
│  │          MODÈLES ML XGBoost (Dev 5)                  │    │
│  │  Modèle 1 : Prédiction rupture stock                 │    │
│  │  Modèle 2 : Prédiction retard fournisseur            │    │
│  │  Modèle 3 : Prédiction commandes clients             │    │
│  └─────────────────────────────────────────────────────┘    │
│                                                               │
│        SMTP · IMAP · ReportLab PDF · WebSocket               │
└───────────────────────┬──────────────────────────────────────┘
                        │
┌───────────────────────▼──────────────────────────────────────┐
│                PostgreSQL (Aiven Cloud)                       │
└──────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Stack technique

| Couche | Technologie | Usage |
|---|---|---|
| **Agent LLM** | Mistral API | Emails, devis, négociation, analyse retours, chat |
| **ML Prédiction** | XGBoost + scikit-learn + Optuna | 3 modèles fine-tunés Kaggle |
| **Backend** | FastAPI + Python 3.12 | API REST + WebSocket |
| **Base de données** | PostgreSQL + Aiven Cloud | Toutes les données |
| **ORM** | SQLAlchemy 2.0 async | Requêtes async |
| **Migrations** | Alembic | Schéma DB |
| **Auth** | JWT + passlib bcrypt | Authentification + RBAC |
| **Email sortant** | SMTP Gmail | Appels d'offre, commandes, retours |
| **Email entrant** | IMAP Gmail | Réponses fournisseurs |
| **PDF** | ReportLab | Bons de commande + factures + avoirs |
| **Frontend** | Next.js 14 + TypeScript | Portail client + portail entreprise |
| **UI** | Tailwind CSS + shadcn/ui | Design |
| **Graphes** | Recharts | Analytics |
| **Temps réel** | WebSockets | Alertes live |
| **Déploiement** | Railway + Vercel | Backend + Frontend |

---

## 📁 Structure du projet

```
nexus/
├── nexus-backend/
│   ├── app/
│   │   ├── api/v1/routes/
│   │   │   ├── auth.py
│   │   │   ├── stock.py
│   │   │   ├── clients.py
│   │   │   ├── production.py
│   │   │   ├── fournisseurs.py
│   │   │   ├── appels_offre.py
│   │   │   ├── devis.py
│   │   │   ├── commandes.py
│   │   │   ├── transporteurs.py
│   │   │   ├── livraisons.py
│   │   │   ├── retours.py               # ⭐ nouveau
│   │   │   ├── predictions.py
│   │   │   ├── analytics.py
│   │   │   └── agent.py
│   │   ├── services/
│   │   │   ├── auth_service.py
│   │   │   ├── stock_service.py
│   │   │   ├── client_service.py
│   │   │   ├── production_service.py
│   │   │   ├── fournisseur_service.py
│   │   │   ├── appel_offre_service.py
│   │   │   ├── devis_service.py
│   │   │   ├── negociation_service.py
│   │   │   ├── commande_service.py
│   │   │   ├── transporteur_service.py
│   │   │   ├── livraison_service.py
│   │   │   ├── retour_service.py        # ⭐ nouveau
│   │   │   ├── inspection_service.py    # ⭐ nouveau
│   │   │   ├── agent_service.py
│   │   │   ├── email_service.py
│   │   │   ├── pdf_service.py
│   │   │   └── analytics_service.py
│   │   ├── ml/
│   │   │   ├── models/
│   │   │   │   ├── stock_model.pkl
│   │   │   │   ├── retard_model.pkl
│   │   │   │   └── client_model.pkl
│   │   │   ├── training/
│   │   │   │   ├── train_stock.py
│   │   │   │   ├── train_retard.py
│   │   │   │   └── train_client.py
│   │   │   └── predict_service.py
│   │   ├── models/
│   │   │   ├── user.py
│   │   │   ├── composant.py
│   │   │   ├── produit_fini.py
│   │   │   ├── client.py
│   │   │   ├── commande_client.py
│   │   │   ├── production.py
│   │   │   ├── fournisseur.py
│   │   │   ├── appel_offre.py
│   │   │   ├── devis.py
│   │   │   ├── commande_fournisseur.py
│   │   │   ├── transporteur.py
│   │   │   ├── livraison_client.py
│   │   │   ├── retour_client.py         # ⭐ nouveau
│   │   │   ├── inspection_retour.py     # ⭐ nouveau
│   │   │   └── mouvement_stock.py
│   │   ├── schemas/
│   │   ├── core/
│   │   │   ├── config.py
│   │   │   ├── database.py
│   │   │   ├── security.py
│   │   │   └── dependencies.py
│   │   └── utils/
│   │       ├── email_parser.py
│   │       └── pdf_generator.py
│   ├── data/kaggle/
│   ├── tests/
│   ├── alembic/
│   ├── .env.example
│   ├── requirements.txt
│   └── main.py
│
├── nexus-client/
│   └── app/
│       ├── login/
│       ├── dashboard/
│       ├── catalogue/
│       ├── commande/
│       ├── retours/                     # ⭐ nouveau
│       └── historique/
│
└── nexus-enterprise/
    └── app/
        ├── dashboard/
        ├── stock/
        ├── clients/
        ├── production/
        ├── fournisseurs/
        ├── transporteurs/
        ├── retours/                     # ⭐ nouveau
        ├── analytics/
        └── agent/
```

---

## 🚀 Installation & Setup

### Prérequis
- Python 3.12+
- Node.js 18+
- Compte [Aiven](https://aiven.io) — PostgreSQL free tier
- Clé API [Mistral](https://console.mistral.ai)
- Compte Gmail avec SMTP + IMAP activés
- Compte [Kaggle](https://kaggle.com) pour les datasets ML

### Backend

```bash
git clone https://github.com/[votre-org]/nexus.git
cd nexus/nexus-backend

python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

pip install -r requirements.txt
cp .env.example .env

alembic upgrade head

kaggle datasets download -d shashwatwork/dataco-smart-supply-chain -p data/kaggle/
python ml/training/train_stock.py
python ml/training/train_retard.py
python ml/training/train_client.py

uvicorn main:app --reload
# API : http://localhost:8000 · Docs : http://localhost:8000/docs
```

### Frontend

```bash
cd nexus/nexus-client && npm install && npm run dev      # http://localhost:3000
cd nexus/nexus-enterprise && npm install && npm run dev  # http://localhost:3001
```

---

## 🔐 Variables d'environnement

```env
DATABASE_URL=postgresql+asyncpg://user:password@host:port/defaultdb?ssl=require
SECRET_KEY=your-secret-key-minimum-32-characters
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
REFRESH_TOKEN_EXPIRE_DAYS=7

MISTRAL_API_KEY=your-mistral-api-key
MISTRAL_MODEL=mistral-large-latest

SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=techbuild.nexus@gmail.com
SMTP_PASSWORD=your-gmail-app-password

IMAP_HOST=imap.gmail.com
IMAP_USER=techbuild.nexus@gmail.com
IMAP_PASSWORD=your-gmail-app-password

BUDGET_MENSUEL_ACHATS=100000
SEUIL_RELANCE_HEURES=24
SEUIL_SCORE_BLACKLIST=30
SEUIL_AUTO_RETOUR_MONTANT=5000
SEUIL_ALERTE_DEFAUT_SERIE=3

APP_ENV=development
```

---

## 👥 Division des tâches — 5 développeurs

### 👤 Dev 1 — Backend Fondations & Stock
*Synchronise avec : Dev 3 (Frontend Entreprise)*

| # | Tâche | Complexité |
|---|---|---|
| 1 | Auth Service — JWT, RBAC 6 rôles | 🔴 Complexe |
| 2 | Tous les modèles SQLAlchemy + migrations Alembic | 🟡 Moyenne |
| 3 | Stock Service — composants + produits finis + emplacements | 🟡 Moyenne |
| 4 | Production Service — ordres + réparations retours | 🟡 Moyenne |
| 5 | PDF Service — bons de commande + factures + avoirs | 🟢 Simple |
| 6 | Analytics Service — KPIs + taux retour + défauts série + WebSocket | 🟡 Moyenne |

---

### 👤 Dev 2 — Backend Agent & Fournisseurs & Retours
*Synchronise avec : Dev 4 (Frontend Client)*

| # | Tâche | Complexité |
|---|---|---|
| 1 | Client Service — commandes + scoring | 🟡 Moyenne |
| 2 | Fournisseur Service — annuaire + scoring + pénalités retours | 🟡 Moyenne |
| 3 | Email Service — SMTP + IMAP | 🟡 Moyenne |
| 4 | Appel Offre Service — Mistral + SMTP | 🟡 Moyenne |
| 5 | Devis Service — IMAP + Mistral extraction | 🔴 Complexe |
| 6 | Négociation Service — contre-offre automatique | 🟡 Moyenne |
| 7 | Commande Service — validation + PDF | 🟡 Moyenne |
| 8 | Transporteur Service — sélection + email + tracking + pénalités retours | 🟡 Moyenne |
| 9 | Livraison Service — suivi + relances | 🟡 Moyenne |
| 10 | Retour Service — analyse motif + décision + résolution | 🔴 Complexe |
| 11 | Inspection Service — réception + état + alerte défaut série | 🟡 Moyenne |
| 12 | Agent Service — Mistral conversationnel | 🟢 Simple |

---

### 👤 Dev 3 — Frontend Entreprise
*Synchronise avec : Dev 1 (Backend Fondations)*

| # | Tâche | Complexité |
|---|---|---|
| 1 | Layout + Auth + routing entreprise | 🟢 Simple |
| 2 | Dashboard global — KPIs + alertes + WebSocket | 🔴 Complexe |
| 3 | Pages Stock — composants + emplacements | 🟡 Moyenne |
| 4 | Pages Fournisseurs — annuaire + scores + appels d'offre | 🟡 Moyenne |
| 5 | Pages Production — ordres + réparations | 🟢 Simple |
| 6 | Pages Transporteurs — annuaire + scores + livraisons | 🟡 Moyenne |
| 7 | Pages Retours — en attente + inspection + historique + qualité | 🔴 Complexe |
| 8 | Pages Analytics — graphes + prédictions + taux retour | 🔴 Complexe |
| 9 | Page Agent — chat Mistral | 🟡 Moyenne |

---

### 👤 Dev 4 — Frontend Client
*Synchronise avec : Dev 2 (Backend Agent)*

| # | Tâche | Complexité |
|---|---|---|
| 1 | Layout + Auth + routing portail client | 🟢 Simple |
| 2 | Page Catalogue — produits + prix + disponibilité | 🟡 Moyenne |
| 3 | Page Nouvelle commande | 🔴 Complexe |
| 4 | Page Dashboard client — commandes + tracking | 🟡 Moyenne |
| 5 | Page Suivi commande — tracking temps réel | 🟡 Moyenne |
| 6 | Page Retour — initier + suivre un retour | 🔴 Complexe |
| 7 | Page Historique — commandes + retours | 🟢 Simple |
| 8 | Pages Clients entreprise — commandes + prédictions | 🔴 Complexe |

---

### 👤 Dev 5 — ML XGBoost & Data
*Synchronise avec : Dev 1 + Dev 2*

| # | Tâche | Complexité |
|---|---|---|
| 1 | Téléchargement + nettoyage 3 datasets Kaggle | 🟡 Moyenne |
| 2 | Feature engineering 3 modèles | 🔴 Complexe |
| 3 | Fine-tuning XGBoost — rupture stock | 🔴 Complexe |
| 4 | Fine-tuning XGBoost — retard fournisseur | 🔴 Complexe |
| 5 | Fine-tuning XGBoost — commandes clients | 🔴 Complexe |
| 6 | Predict Service — interface FastAPI unifiée | 🟡 Moyenne |
| 7 | Endpoints ML — `/predictions/stock` `/predictions/retard` `/predictions/clients` | 🟡 Moyenne |
| 8 | Données simulation TechBuild — dataset réaliste démo | 🟢 Simple |

---

### Résumé synchronisations & branches Git

```
Dev 1 ←→ Dev 3    Dev 2 ←→ Dev 4    Dev 5 ←→ Dev 1 + Dev 2

main
├── dev1/backend-fondations
├── dev2/backend-agent
├── dev3/frontend-entreprise
├── dev4/frontend-client
└── dev5/ml-xgboost
```

### Point de synchronisation global

```
JOUR 1 SOIR — Dev 1 merge Auth + modèles SQLAlchemy
        ↓ Dev 2, Dev 3, Dev 4 démarrent en parallèle
JOUR 2 SOIR — Dev 5 livre 3 modèles .pkl + endpoints predictions
        ↓ Dev 1 + Dev 2 intègrent les prédictions
JOUR 3 MATIN — Tests flux complet + fix bugs + pitch
```

---

## 📋 Roadmap MVP 3 jours

### 🔴 Jour 1 — Fondations & ML

```
Dev 1 : Auth + modèles SQLAlchemy (retour inclus) + migrations
Dev 2 : Client + Fournisseur + Email + Transporteur + Retour Service (structure)
Dev 3 : Layout entreprise + Dashboard + Pages Stock
Dev 4 : Layout client + Catalogue + Commande + Page Retour (structure)
Dev 5 : Téléchargement datasets + feature engineering + début training
```

### 🔴 Jour 2 — Cœur métier

```
Dev 1 : Stock + Production + PDF + Analytics (taux retour + défaut série)
Dev 2 : Appel Offre + Devis + Négociation + Commande + Transporteur + Retour complet
Dev 3 : Fournisseurs + Transporteurs + Retours + Production
Dev 4 : Dashboard client + Tracking + Retour complet + Historique
Dev 5 : Fine-tuning 3 modèles + Predict Service + Endpoints
```

### 🔴 Jour 3 — Intégration & Démo

```
Dev 1 : Intégration ML + WebSocket + tests
Dev 2 : Intégration ML + tests flux complet + retours
Dev 3 : Analytics + graphes Recharts + Agent + polish UI
Dev 4 : Prédictions clients + retour UI polish + tracking
Dev 5 : Données simulation TechBuild + support intégration
```

---

## 🎯 Script de démo pour le jury

```
⏱️ 4 minutes — dans cet ordre exact

[0:00] Dashboard entreprise
→ Alerte : "GPU RTX 4090 → rupture dans 8 jours"
→ Prédiction ML : "CyberArena commande dans 5 jours"
→ "Nexus détecte AVANT que ça arrive"

[0:35] Appel d'offre automatique
→ Email généré + envoyé à 3 fournisseurs
→ Contre-offre car hors budget → acceptée
→ Bon de commande PDF en 1 clic

[1:10] Production terminée → sélection transporteur
→ Tableau 5 transporteurs avec score ML intégré
→ DHL sélectionné automatiquement
→ Email enlèvement + numéro tracking transmis au client

[1:45] Portail client CyberArena
→ Commande 20 PC Gaming Premium
→ Email confirmation + tracking automatique

[2:15] CyberArena signale 1 PC défectueux
→ Retour initié depuis le portail client
→ Mistral analyse : responsabilité fournisseur GPU
→ Client VIP → approuvé automatiquement
→ Aramex envoyé pour ramassage
→ Score NvidiaPartner pénalisé
→ Dashboard : "3 retours GPU → défaut série possible"

[3:15] Dashboard analytics
→ Prédictions stock 30 jours
→ Score fournisseurs + transporteurs
→ Taux de retour par produit/fournisseur
→ "Supply chain complète — zéro friction"
```

---

<div align="center">

**⚡ NEXUS**

*Du latin "nectere" — lier, connecter, tisser ensemble.*
*Le point central qui relie tous les maillons de la supply chain.*

```
Fournisseurs → Entrepôt → Production → Transporteurs → Clients
                                                          ↕
                                                       Retours
        ↑_________________ NEXUS gère tout ________________↑
```

**Industrial Challenge 2026 · Supply Chain & AI · Agentic AI**

`XGBOOST` · `MISTRAL AI` · `FASTAPI` · `SUPPLY CHAIN` · `INDUSTRY 4.0`

</div>