# GARMI - Documentation Technique
**Portfolio Project - Stage 3**  
**Version 1.0 - 28 mai 2025**

---

## Table des Matières
1. [User Stories et Mockups](#1-user-stories-et-mockups)
2. [Architecture Système](#2-architecture-système)
3. [Composants, Classes et Base de Données](#3-composants-classes-et-base-de-données)
4. [Diagrammes de Séquence](#4-diagrammes-de-séquence)
5. [Spécifications APIs](#5-spécifications-apis)
6. [Stratégies SCM et QA](#6-stratégies-scm-et-qa)
7. [Justifications Techniques](#7-justifications-techniques)

---

## 1. User Stories et Mockups

### User Stories Prioritisées (MoSCoW)

#### **MUST HAVE (MVP Essentiels)**

**US001 - Création de compte**
> En tant qu'utilisateur, je veux créer un compte rapidement avec Google/Apple/Email, afin de sauvegarder ma garde-robe et synchroniser mes données.

**US002 - Ajout de vêtement**
> En tant qu'utilisateur, je veux photographier un vêtement et voir l'arrière-plan supprimé automatiquement, afin d'avoir une garde-robe digitale propre et professionnelle.

**US003 - Catégorisation**
> En tant qu'utilisateur, je veux classer mes vêtements par catégories prédéfinies (hauts, bas, chaussures, accessoires), afin de retrouver facilement mes pièces.

**US004 - Création d'outfit**
> En tant qu'utilisateur, je veux glisser-déposer mes vêtements sur un canvas libre, afin de créer visuellement des tenues harmonieuses.

**US005 - Suggestions de couleurs**
> En tant qu'utilisateur, je veux recevoir des suggestions d'accords de couleurs, afin de créer des tenues esthétiquement cohérentes.

**US006 - Sauvegarde de tenues**
> En tant qu'utilisateur, je veux sauvegarder mes tenues créées, afin de les réutiliser ou m'en inspirer plus tard.

#### **SHOULD HAVE (Fonctionnalités importantes)**

**US007 - Recherche rapide**
> En tant qu'utilisateur, je veux rechercher un vêtement par couleur ou catégorie, afin de le retrouver rapidement dans ma garde-robe.

**US008 - Visualisation garde-robe**
> En tant qu'utilisateur, je veux voir tous mes vêtements organisés par catégorie, afin d'avoir une vue d'ensemble de ma garde-robe.

#### **COULD HAVE (Améliorations futures)**

**US009 - Notifications intelligentes**
> En tant qu'utilisateur, je veux être rappelé de terminer une tenue commencée, afin de ne pas perdre mon travail créatif.

**US010 - Mode sombre**
> En tant qu'utilisateur, je veux pouvoir utiliser l'app en mode sombre, afin de préserver mes yeux et économiser la batterie.

#### **WON'T HAVE (Post-MVP)**

**US011 - Partage social** (reporté)
**US012 - Planification calendaire** (reporté)
**US013 - Statistiques d'utilisation** (reporté)

### Mockups Principaux

#### **Écran d'Authentification**
- Interface minimaliste avec 3 boutons : "Se connecter avec Apple", "Se connecter avec Google", "Se connecter avec Email"
- Logo GARMI centré en haut
- Illustration subtile de vêtements en arrière-plan

#### **Dashboard Principal**
- Vue grille de la garde-robe avec filtres par catégorie
- Bouton flottant "+" pour ajouter un vêtement
- Section "Tenues récentes" en bas

#### **Interface de Création d'Outfit**
- Canvas blanc central pour glisser-déposer
- Palette de vêtements sur les côtés (scrollable)
- Suggestions de couleurs en bas
- Boutons "Sauvegarder" et "Annuler"

#### **Processus d'Ajout de Vêtement**
- Caméra native iOS avec guide de cadrage
- Aperçu avec arrière-plan supprimé
- Sélection de catégorie avec icônes
- Confirmation et sauvegarde

---

## 2. Architecture Système

### Diagramme d'Architecture Globale

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   iOS FRONTEND  │    │   FIREBASE      │    │  EXTERNAL APIs  │
│                 │    │   BACKEND       │    │                 │
│  ┌───────────┐  │    │  ┌───────────┐  │    │  ┌───────────┐  │
│  │ SwiftUI   │  │◄──►│  │ Firestore │  │    │  │Vision API │  │
│  │ Views     │  │    │  │ Database  │  │    │  │(Apple)    │  │
│  └───────────┘  │    │  └───────────┘  │    │  └───────────┘  │
│                 │    │                 │    │                 │
│  ┌───────────┐  │    │  ┌───────────┐  │    │  ┌───────────┐  │
│  │ Core ML   │  │◄──►│  │ Firebase  │  │◄──►│  │Remove.bg  │  │
│  │ Vision    │  │    │  │ Storage   │  │    │  │API        │  │
│  └───────────┘  │    │  └───────────┘  │    │  └───────────┘  │
│                 │    │                 │    │                 │
│  ┌───────────┐  │    │  ┌───────────┐  │    │                 │
│  │ Local     │  │    │  │ Firebase  │  │    │                 │
│  │ Storage   │  │    │  │ Auth      │  │    │                 │
│  └───────────┘  │    │  └───────────┘  │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### Flux de Données

**1. Authentification :**
iOS App → Firebase Auth → Utilisateur connecté

**2. Ajout de Vêtement :**
Caméra iOS → Vision API → Image traitée → Firebase Storage → Métadonnées → Firestore

**3. Création d'Outfit :**
Interface SwiftUI → Logique locale → Sauvegarde Firebase → Synchronisation

**4. Synchronisation :**
Modifications locales → Firebase Sync → Autres appareils utilisateur

---

## 3. Composants, Classes et Base de Données

### Structure des Classes SwiftUI

#### **AuthenticationManager**
```swift
class AuthenticationManager: ObservableObject {
    @Published var user: User?
    @Published var isAuthenticated: Bool = false
    
    func signInWithApple()
    func signInWithGoogle() 
    func signInWithEmail(email: String, password: String)
    func signOut()
}
```

#### **WardrobeManager**
```swift
class WardrobeManager: ObservableObject {
    @Published var garments: [Garment] = []
    @Published var outfits: [Outfit] = []
    
    func addGarment(_ garment: Garment)
    func removeGarment(id: String)
    func createOutfit(_ outfit: Outfit)
    func syncWithFirebase()
}
```

#### **ImageProcessor**
```swift
class ImageProcessor {
    func removeBackground(from image: UIImage) -> UIImage?
    func processWithVisionAPI(_ image: UIImage) -> UIImage?
    func fallbackToRemoveBG(_ image: UIImage) -> UIImage?
    func optimizeImage(_ image: UIImage) -> UIImage
}
```

#### **ColorSuggestionEngine**
```swift
class ColorSuggestionEngine {
    private let colorDatabase: [ColorRule]
    
    func suggestMatchingColors(for garment: Garment) -> [Color]
    func validateColorHarmony(outfit: Outfit) -> Bool
    func loadColorRules() -> [ColorRule]
}
```

### Modèles de Données

#### **Garment**
```swift
struct Garment: Identifiable, Codable {
    let id: String
    let name: String
    let category: GarmentCategory
    let primaryColor: Color
    let secondaryColors: [Color]
    let imageURL: String
    let createdDate: Date
    let lastWorn: Date?
}
```

#### **Outfit**
```swift
struct Outfit: Identifiable, Codable {
    let id: String
    let name: String
    let garmentIDs: [String]
    let canvasLayout: CanvasLayout
    let createdDate: Date
    let lastUsed: Date?
}
```

#### **CanvasLayout**
```swift
struct CanvasLayout: Codable {
    let garmentPositions: [GarmentPosition]
    let canvasSize: CGSize
}

struct GarmentPosition: Codable {
    let garmentID: String
    let position: CGPoint
    let scale: CGFloat
    let rotation: CGFloat
}
```

### Structure Firebase Firestore

#### **Collection : users**
```json
{
  "userID": {
    "email": "user@example.com",
    "displayName": "User Name",
    "createdAt": "timestamp",
    "lastLoginAt": "timestamp",
    "preferences": {
      "darkMode": false,
      "notifications": true
    }
  }
}
```

#### **Collection : garments**
```json
{
  "garmentID": {
    "userID": "string",
    "name": "T-shirt blanc",
    "category": "tops",
    "primaryColor": "#FFFFFF",
    "secondaryColors": ["#000000"],
    "imageURL": "gs://garmi-storage/images/garmentID.jpg",
    "createdAt": "timestamp",
    "lastWorn": "timestamp",
    "tags": ["casual", "été"]
  }
}
```

#### **Collection : outfits**
```json
{
  "outfitID": {
    "userID": "string",
    "name": "Tenue décontractée",
    "garmentIDs": ["garment1", "garment2", "garment3"],
    "canvasLayout": {
      "garmentPositions": [
        {
          "garmentID": "garment1",
          "x": 100,
          "y": 150,
          "scale": 1.0,
          "rotation": 0
        }
      ]
    },
    "createdAt": "timestamp",
    "lastUsed": "timestamp"
  }
}
```

#### **Collection : colorRules** (Base interne)
```json
{
  "ruleID": {
    "primaryColor": "#FF0000",
    "complementaryColors": ["#00FF00", "#0000FF"],
    "harmonyType": "complementary",
    "description": "Rouge avec verts et bleus"
  }
}
```

---

## 4. Diagrammes de Séquence

### Séquence 1 : Authentification Utilisateur

```
Utilisateur -> App iOS -> Firebase Auth -> App iOS -> Utilisateur
    |            |            |            |            |
    |   Tap "Se connecter avec Apple"       |            |
    |----------->|            |            |            |
    |            |  Sign In with Apple     |            |
    |            |----------->|            |            |
    |            |            | Validate   |            |
    |            |            |----------->|            |
    |            |            |   Token    |            |
    |            |            |<-----------|            |
    |            |  User Data |            |            |
    |            |<-----------|            |            |
    |            |            |   Update UI State       |
    |            |----------->|            |            |
    |            |            |            |  Dashboard |
    |<-----------|            |            |<-----------|
```

### Séquence 2 : Ajout d'un Vêtement

```
Utilisateur -> App iOS -> Vision API -> Firebase Storage -> Firestore -> App iOS
    |            |            |              |              |            |
    |   Prend photo          |              |              |            |
    |----------->|            |              |              |            |
    |            | Process Image             |              |            |
    |            |----------->|              |              |            |
    |            |  Clean Image              |              |            |
    |            |<-----------|              |              |            |
    |            |    Upload Image           |              |            |
    |            |------------------------->|              |            |
    |            |           Image URL       |              |            |
    |            |<-------------------------|              |            |
    |            |        Save Metadata     |              |            |
    |            |------------------------------------->|            |
    |            |         Success          |              |            |
    |            |<-------------------------------------|            |
    |            |    Update UI             |              |            |
    |            |----------->|              |              |            |
    |   Confirmation         |              |              |            |
    |<-----------|            |              |              |            |
```

### Séquence 3 : Création d'Outfit

```
Utilisateur -> App iOS -> Local Storage -> Firebase -> App iOS -> Utilisateur
    |            |            |              |            |            |
    |  Glisse vêtements      |              |            |            |
    |----------->|            |              |            |            |
    |            | Update Canvas             |            |            |
    |            |----------->|              |            |            |
    |            |  Tap "Sauvegarder"       |            |            |
    |----------->|            |              |            |            |
    |            |   Save Locally           |            |            |
    |            |----------->|              |            |            |
    |            |       Sync to Firebase   |            |            |
    |            |------------------------->|            |            |
    |            |        Success           |            |            |
    |            |<-------------------------|            |            |
    |            |    Update UI             |            |            |
    |            |----------->|              |            |            |
    |   Tenue sauvegardée    |              |            |            |
    |<-----------|            |              |            |            |
```

---

## 5. Spécifications APIs

### APIs Externes Utilisées

#### **1. Apple Vision Framework**
- **Objectif** : Suppression d'arrière-plan principale
- **Avantages** : Intégré iOS, offline, gratuit, optimisé
- **Utilisation** : Traitement d'images de vêtements

#### **2. Remove.bg API** (Fallback)
- **URL** : `https://api.remove.bg/v1.0/removebg`
- **Méthode** : POST
- **Objectif** : Suppression d'arrière-plan de secours
- **Coût** : 50 images gratuites/mois, puis payant

#### **3. Firebase Services**
- **Authentication** : Gestion des comptes utilisateur
- **Firestore** : Base de données NoSQL
- **Storage** : Stockage des images
- **Cloud Functions** : Traitements serveur si nécessaire

### APIs Internes (Future Extension)

#### **Endpoint : Garments**

**GET /api/garments**
- **Description** : Récupérer tous les vêtements de l'utilisateur
- **Headers** : `Authorization: Bearer <token>`
- **Response** :
```json
{
  "success": true,
  "data": [
    {
      "id": "garment123",
      "name": "T-shirt blanc",
      "category": "tops",
      "primaryColor": "#FFFFFF",
      "imageURL": "https://storage.url/image.jpg",
      "createdAt": "2025-05-28T10:00:00Z"
    }
  ]
}
```

**POST /api/garments**
- **Description** : Ajouter un nouveau vêtement
- **Headers** : `Content-Type: multipart/form-data`
- **Body** :
```json
{
  "name": "Jeans bleu",
  "category": "bottoms",
  "primaryColor": "#1E3A8A",
  "image": "<base64_image_data>"
}
```
- **Response** :
```json
{
  "success": true,
  "data": {
    "id": "garment456",
    "message": "Vêtement ajouté avec succès"
  }
}
```

#### **Endpoint : Outfits**

**GET /api/outfits**
- **Description** : Récupérer toutes les tenues
- **Response** :
```json
{
  "success": true,
  "data": [
    {
      "id": "outfit789",
      "name": "Look casual",
      "garmentIDs": ["garment123", "garment456"],
      "canvasLayout": {...},
      "createdAt": "2025-05-28T15:30:00Z"
    }
  ]
}
```

**POST /api/outfits**
- **Description** : Créer une nouvelle tenue
- **Body** :
```json
{
  "name": "Tenue bureau",
  "garmentIDs": ["garment123", "garment456", "garment789"],
  "canvasLayout": {
    "garmentPositions": [...]
  }
}
```

#### **Endpoint : Color Suggestions**

**GET /api/colors/suggestions?primaryColor=#FF0000**
- **Description** : Obtenir des suggestions de couleurs
- **Response** :
```json
{
  "success": true,
  "data": {
    "primaryColor": "#FF0000",
    "suggestions": [
      {
        "color": "#00FF00",
        "type": "complementary",
        "confidence": 0.95
      }
    ]
  }
}
```

---

## 6. Stratégies SCM et QA

### Stratégie de Gestion de Code Source (SCM)

#### **Structure Git**
```
main
├── develop
├── feature/authentication
├── feature/camera-integration
├── feature/outfit-creation
├── feature/color-suggestions
└── hotfix/critical-bug-fix
```

#### **Workflow de Développement**
1. **Feature Branch** : Création d'une branche pour chaque fonctionnalité
2. **Development** : Développement et tests locaux
3. **Pull Request** : Revue de code automatique avec GitHub Actions
4. **Code Review** : Auto-review avec checklist
5. **Merge** : Fusion vers develop après validation
6. **Release** : Fusion develop → main pour déploiement

#### **Convention de Commits**
```
feat: ajout de la suppression d'arrière-plan
fix: correction du crash lors de l'upload
docs: mise à jour de la documentation API
style: amélioration de l'interface utilisateur
refactor: restructuration du WardrobeManager
test: ajout des tests unitaires pour ColorEngine
```

#### **Hooks Git**
- **Pre-commit** : Vérification du format de code (SwiftLint)
- **Pre-push** : Exécution des tests unitaires
- **Post-merge** : Nettoyage automatique des branches

### Stratégie d'Assurance Qualité (QA)

#### **Types de Tests**

**1. Tests Unitaires (XCTest)**
```swift
// Exemple de test pour ColorSuggestionEngine
class ColorSuggestionEngineTests: XCTestCase {
    func testComplementaryColorSuggestion() {
        let engine = ColorSuggestionEngine()
        let suggestions = engine.suggestMatchingColors(for: redGarment)
        XCTAssertTrue(suggestions.contains(Color.green))
    }
}
```

**2. Tests d'Interface (UI Tests)**
```swift
// Test du flow d'ajout de vêtement
func testAddGarmentFlow() {
    let app = XCUIApplication()
    app.buttons["Ajouter"].tap()
    app.buttons["Caméra"].tap()
    app.buttons["Prendre photo"].tap()
    XCTAssertTrue(app.buttons["Confirmer"].exists)
}
```

**3. Tests d'Intégration**
- Vérification de la synchronisation Firebase
- Tests des APIs externes (Vision, Remove.bg)
- Validation du processus d'authentification

#### **Outils de Test**
- **XCTest** : Framework de test natif iOS
- **Firebase Test Lab** : Tests sur appareils réels
- **TestFlight** : Déploiement beta pour tests utilisateurs
- **Crashlytics** : Monitoring des crashes en production

#### **Pipeline CI/CD avec GitHub Actions**
```yaml
name: GARMI CI/CD
on: [push, pull_request]
jobs:
  test:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run Unit Tests
        run: xcodebuild test -scheme GARMI
      - name: Run SwiftLint
        run: swiftlint
      - name: Build Archive
        run: xcodebuild archive
```

#### **Critères de Qualité**
- **Couverture de code** : Minimum 80%
- **Performance** : Temps de lancement < 3 secondes
- **Crash rate** : < 0.1% des sessions
- **Tests utilisateurs** : Score satisfaction > 4/5

#### **Stratégie de Déploiement**
1. **Development** : Déploiement automatique sur simulateur
2. **Staging** : TestFlight pour équipe interne
3. **Beta** : TestFlight pour testeurs externes (20 personnes)
4. **Production** : App Store après validation complète

---

## 7. Justifications Techniques

### Choix de l'Architecture

#### **Firebase vs CoreData**
**Décision** : Firebase  
**Justification** :
- **Synchronisation multi-appareils** : Essential pour l'expérience utilisateur moderne
- **Backup automatique** : Sécurité des données utilisateur
- **Évolutivité** : Facilite l'ajout de fonctionnalités sociales futures
- **Authentification intégrée** : Simplifie la gestion des comptes
- **Coût** : Gratuit jusqu'à usage significatif

#### **SwiftUI vs UIKit**
**Décision** : SwiftUI  
**Justification** :
- **Développement moderne** : Approche déclarative plus efficace
- **Performance** : Optimisations automatiques d'Apple
- **Maintenance** : Code plus lisible et maintenable
- **Intégrations** : Meilleure intégration avec les APIs iOS récentes
- **Courbe d'apprentissage** : Investissement dans la technologie d'avenir d'Apple

#### **Vision API vs Solutions tierces**
**Décision** : Vision API principale + Remove.bg fallback  
**Justification** :
- **Offline-first** : Fonctionne sans connexion internet
- **Performance** : Optimisé pour le hardware Apple
- **Coût** : Gratuit et illimité
- **Qualité** : Suffisante pour la plupart des cas d'usage
- **Fallback** : Remove.bg pour les cas complexes

### Choix des Données

#### **Structure NoSQL (Firestore)**
**Justification** :
- **Flexibilité** : Structure adaptable aux évolutions
- **Performance** : Requêtes rapides pour l'affichage temps réel
- **Synchronisation** : Temps réel entre appareils
- **Scalabilité** : Croissance automatique avec l'usage

#### **Stockage d'Images**
**Décision** : Firebase Storage  
**Justification** :
- **CDN intégré** : Chargement rapide des images
- **Compression automatique** : Optimisation des performances
- **Sécurité** : Contrôle d'accès granulaire
- **Coût** : Tarification progressive selon l'usage

### Choix d'Expérience Utilisateur

#### **Authentification Obligatoire**
**Justification** :
- **Sauvegarde des données** : Protection contre la perte
- **Synchronisation** : Expérience multi-appareils
- **Personnalisation** : Préférences utilisateur
- **Évolutivité** : Base pour fonctionnalités futures

#### **Canvas Libre vs Zones Fixes**
**Décision** : Canvas libre  
**Justification** :
- **Créativité** : Liberté totale de composition
- **Naturalité** : Reproduction de l'habillage physique
- **Différenciation** : Unique parmi les concurrents
- **Engagement** : Interface plus ludique et engageante

#### **Notifications Contextuelles**
**Justification** :
- **Engagement** : Maintien de l'utilisation
- **Utilité** : Évite la perte de travail
- **Non-intrusif** : Déclenchement intelligent selon le contexte

### Choix de Développement

#### **Approche MVP-First**
**Justification** :
- **Validation rapide** : Test du concept avant investissement complet
- **Feedback utilisateur** : Amélioration basée sur l'usage réel
- **Gestion des risques** : Limitation de la complexité initiale
- **Time-to-market** : Lancement rapide pour validation

#### **Architecture Modulaire**
**Justification** :
- **Maintenabilité** : Code organisé et évolutif
- **Testabilité** : Tests unitaires facilités
- **Réutilisabilité** : Composants réutilisables
- **Collaboration** : Structure claire pour le développement

---

## Conclusion

Cette documentation technique fournit une base solide pour le développement du MVP GARMI. L'architecture choisie privilégie la simplicité d'implémentation tout en préservant la possibilité d'évolution future. 

**Points clés de la stratégie technique** :
- **Backend Firebase** pour la robustesse et la synchronisation
- **SwiftUI** pour une interface moderne et performante  
- **Vision API** pour le traitement d'images offline
- **Architecture modulaire** pour la maintenabilité
- **Tests automatisés** pour la qualité

Le développement peut maintenant débuter avec une vision claire des composants, des interactions et des standards de qualité à respecter.

---

*Document créé le 28 mai 2025 dans le cadre du Portfolio Project - Stage 3*