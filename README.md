---

# README - Diagrammes UML - Application Tournoi de Basket

## 📌 Présentation

Ce dossier contient l'ensemble des diagrammes UML réalisés pour l'application de gestion d’un tournoi de basket. Ces diagrammes modélisent la structure, les interactions et les cas d'utilisation principaux selon le cahier des charges fourni.

---

## 📂 Contenu UML

### 1. Diagramme de classes

* Modélise les entités principales (Equipe, Joueur, Arbitre, Terrain, Match, Poule, Classement)
* Définit les attributs, méthodes et relations dirigées entre classes
* Représente les contraintes métier clés (nombre joueurs par équipe, rôles, participation, règles d’arbitrage)

**Format** : code PlantUML
**Extrait :**

```plantuml
Equipe "1" --> "5..8" Joueur : contient >
Joueur "1" --> "1" Equipe : appartient >
Match "1" --> "1" Terrain : se joue sur >
```

---

### 2. Diagrammes de séquence (Architecture 3-tiers)

Représentation des flux d’interactions entre :

* **Frontend (Angular)**
* **Backend API (Spring Boot)**
* **Base de données (MySQL/PostgreSQL)**

Pour plusieurs scénarios métier importants :

* Ajouter un joueur
* Créer une équipe
* Générer les poules et le calendrier
* Saisir un score de match
* Exporter le rapport PDF du tournoi

**Exemple de diagramme séquence (Ajouter un joueur) :**

```plantuml
Admin -> Front : Remplit formulaire joueur
Front -> Backend : POST /api/joueurs
Backend -> DB : INSERT INTO joueur(...)
Backend --> Front : 201 Created
```

---

### 3. Diagramme de cas d’utilisation (Use Case)

Décrit les interactions entre les acteurs et le système :

* **Admin** : gestion complète du tournoi
* **Arbitre** : saisie des résultats
* **Utilisateur** : consultation du calendrier et classement

**Extrait PlantUML Use Case :**

```plantuml
actor Admin
actor Arbitre
actor Utilisateur

rectangle "Application de gestion de tournoi" {
  Admin --> (Gérer Joueurs)
  Arbitre --> (Saisir Résultats)
  Utilisateur --> (Voir Classement)
}
```

---

## ✅ Résumé des cas d’usage traités :

| # | Fonction                  | Méthode API                | Niveau couvert           |
| - | ------------------------- | -------------------------- | ------------------------ |
| 1 | Ajouter joueur            | POST /api/joueurs          | CRUD                     |
| 2 | Créer équipe              | POST /api/equipes          | Règles métier            |
| 3 | Générer poules/calendrier | POST /api/poules/generer   | Automatisation           |
| 4 | Saisir score              | PUT /api/matchs/{id}/score | Mise à jour + classement |
| 5 | Export PDF                | GET /api/export/pdf        | Reporting                |

---

