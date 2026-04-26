# 📱 Lab Android — Gestion des Étudiants avec SQLite

> Application Android de gestion d'étudiants utilisant une base de données locale SQLite.  
> Aucune connexion réseau requise — tout fonctionne en local sur l'appareil.

---

## 📋 Table des matières

- [Aperçu](#aperçu)
- [Démonstration vidéo](#démonstration-vidéo)
- [Fonctionnalités](#fonctionnalités)
- [Architecture du projet](#architecture-du-projet)
- [Prérequis](#prérequis)
- [Installation](#installation)
- [Structure des fichiers](#structure-des-fichiers)
- [Base de données](#base-de-données)
- [Utilisation](#utilisation)

---

## Aperçu

Cette application Android permet de gérer une liste d'étudiants stockée localement grâce à **SQLite**, le système de base de données embarqué d'Android. Elle permet d'ajouter, rechercher et supprimer des étudiants sans aucune connexion Internet.

---

## 🎬 Démonstration vidéo

> La vidéo ci-dessous présente le fonctionnement complet du lab SQLite.



https://github.com/user-attachments/assets/0a5abfe6-dba3-4872-a7b9-15e7b17f79dc



---

## ✅ Fonctionnalités

- ➕ **Ajouter** un étudiant (nom + prénom) → stockage SQLite automatique
- 🔍 **Rechercher** un étudiant par son ID
- 🗑️ **Supprimer** un étudiant par son ID
- 💬 Messages **Toast** pour confirmer chaque action
- 🛡️ Validation des champs (champs vides, ID invalide)

---

## 🏗️ Architecture du projet

```
com.example.sqlite/
│
├── MainActivity.java                  ← Activité principale (UI + logique)
│
├── projet.fst.ma.app.classes/
│   └── Etudiant.java                  ← Modèle de données
│
├── projet.fst.ma.app.service/
│   └── EtudiantService.java           ← Opérations CRUD SQLite
│
└── projet.fst.ma.app.util/
    └── MySQLiteHelper.java            ← Création & gestion de la BDD
```

### Schéma des couches

```
┌─────────────────────────┐
│      MainActivity       │  ← Interface utilisateur
└──────────┬──────────────┘
           │
┌──────────▼──────────────┐
│    EtudiantService      │  ← Logique métier (CRUD)
└──────────┬──────────────┘
           │
┌──────────▼──────────────┐
│    MySQLiteHelper       │  ← Gestion de la base SQLite
└──────────┬──────────────┘
           │
┌──────────▼──────────────┐
│   Base SQLite locale    │  ← Fichier ecole.db sur l'appareil
└─────────────────────────┘
```

---

## 🔧 Prérequis

| Outil | Version recommandée |
|-------|-------------------|
| Android Studio | Hedgehog ou supérieur |
| JDK | 11 ou supérieur |
| Android SDK | API 26 minimum |
| Appareil / Émulateur | Android 8.0+ |

---

## 🚀 Installation

1. **Cloner ou télécharger** le projet

```bash
git clone https://github.com/votre-user/lab-sqlite-android.git
```

2. **Ouvrir** le projet dans Android Studio :
   `File → Open → sélectionner le dossier du projet`

3. **Synchroniser** Gradle :
   `File → Sync Project with Gradle Files`

4. **Lancer** l'application :
   - Sur émulateur : cliquer sur ▶ Run
   - Sur téléphone : activer le mode développeur + USB debugging

> Aucune dépendance externe requise — SQLite est intégré nativement dans Android.

---

## 📁 Structure des fichiers

```
app/
├── manifests/
│   └── AndroidManifest.xml
│
├── java/
│   ├── com/example/sqlite/
│   │   └── MainActivity.java
│   │
│   └── projet/fst/ma/app/
│       ├── classes/
│       │   └── Etudiant.java
│       ├── service/
│       │   └── EtudiantService.java
│       └── util/
│           └── MySQLiteHelper.java
│
└── res/
    ├── layout/
    │   └── activity_main.xml
    ├── drawable/
    │   └── card_background.xml
    └── values/
        ├── strings.xml
        └── styles.xml
```

---

## 🗄️ Base de données

**Nom :** `ecole.db`  
**Emplacement sur l'appareil :** `/data/data/com.example.sqlite/databases/ecole.db`

### Table `etudiant`

| Colonne | Type | Contrainte |
|---------|------|-----------|
| `id` | INTEGER | PRIMARY KEY AUTOINCREMENT |
| `nom` | TEXT | — |
| `prenom` | TEXT | — |

### Requête de création

```sql
CREATE TABLE etudiant (
    id      INTEGER PRIMARY KEY AUTOINCREMENT,
    nom     TEXT,
    prenom  TEXT
);
```

### Opérations CRUD disponibles

| Méthode | Description |
|---------|-------------|
| `create(Etudiant e)` | Insère un nouvel étudiant |
| `findById(int id)` | Recherche par ID |
| `findAll()` | Retourne tous les étudiants |
| `update(Etudiant e)` | Met à jour un étudiant |
| `delete(Etudiant e)` | Supprime un étudiant |

---

## 📖 Utilisation

### Ajouter un étudiant

1. Remplir les champs **Nom** et **Prénom**
2. Cliquer sur **Valider**
3. Un message de confirmation s'affiche
4. Les champs se vident automatiquement

### Rechercher un étudiant

1. Saisir l'**ID** dans le champ ID
2. Cliquer sur **Chercher**
3. Les informations s'affichent dans la zone résultat

### Supprimer un étudiant

1. Saisir l'**ID** dans le champ ID
2. Cliquer sur **Supprimer**
3. Confirmation de suppression affichée

---

## 👨‍💻 Auteur

> Réalisé par : Madili Kenza  
> Module : Développement Mobile  

---

## 📄 Licence

Ce lab est réalisé à des fins pédagogiques.
