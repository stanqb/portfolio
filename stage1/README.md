# GARMI - Stage 1 Report: Team Formation and Idea Development

## 1. Team Formation Overview

### Project Structure (Individual Project)
Ce projet GARMI est développé en tant que projet individuel. En tant qu'unique contributeur, j'ai effectué une auto-évaluation de mes compétences et intérêts pour structurer efficacement le travail à réaliser.

### Compétences et Forces Personnelles
- **Développement**: Expérience solide en programmation C et Python
- **Conception UI/UX**: Intérêt pour le design d'interfaces utilisateur minimalistes et intuitives
- **Gestion de projet**: Capacité à planifier et exécuter les différentes étapes de développement
- **Vision produit**: Compréhension des besoins utilisateurs dans le domaine de la mode et du style

### Défis Techniques
- **Apprentissage de SwiftUI**: Bien que possédant une solide expérience en C et Python, je devrai consacrer du temps à l'apprentissage de SwiftUI, ce qui est pris en compte dans le planning
- **Familiarisation avec l'écosystème iOS**: Temps d'adaptation nécessaire aux spécificités du développement pour iOS (CoreML, Vision, etc.)
- **Courbe d'apprentissage**: Intégration dans le planning de périodes dédiées à la formation et aux tests préliminaires

### Organisation du Travail
Bien que travaillant seul, j'ai structuré le projet pour maximiser l'efficacité:

- **Segmentation des rôles**: J'ai divisé mon travail en "rôles fonctionnels" que j'assume à différents moments:
  - Lundi: Focus sur le design et l'UX
  - Mardi-Mercredi: Développement iOS et fonctionnalités techniques
  - Jeudi: Tests et améliorations
  - Vendredi: Documentation et planification

- **Gestion avec Notion**: 
  - **Dashboard principal**: Vue d'ensemble du projet avec KPIs et prochaines étapes
  - **Base de données de tâches**: Système permettant de visualiser l'avancement, la priorité et les échéances de chaque tâche
  - **Système de rappels**: Notifications programmées pour les deadlines importantes
  - **Galerie de références**: Collection organisée d'inspirations UI/UX
  - **Documentation technique**: Notes structurées sur les choix d'architecture et API
  - **Templates de tests**: Protocoles standardisés pour tester les fonctionnalités
  - **Kanban personnalisé**: Vue des tâches par statut (À faire, En cours, En test, Terminé)

- **Outils complémentaires**:
  - **GitHub**: Pour le versionnement du code
  - **Figma**: Pour les maquettes et prototypes
  - **TestFlight**: Pour le déploiement des versions de test

- **Contrôle qualité**: Auto-évaluation régulière avec des listes de contrôle et des tests utilisateurs avec des amis/famille pour obtenir des retours

## 2. Research and Brainstorming

### Inspiration et Recherche Initiale

Ma démarche de recherche s'est articulée autour de ma passion pour l'univers de la mode streetwear, en particulier les marques emblématiques comme Stüssy et Supreme qui ont révolutionné ce secteur. J'ai exploré comment ces marques ont su évoluer et se réinventer au fil du temps, tout en maintenant une identité forte.

#### Étude de marché préliminaire:
- **Analyse des applications existantes**: J'ai testé les principales applications de garde-robe virtuelle sur l'App Store (Whering, Stylebook, Cladwell) et identifié des lacunes dans leur expérience utilisateur et leur design visuel.
- **Recherches documentaires**: Lecture d'articles spécialisés sur les tendances de la mode digitale et l'évolution des habitudes vestimentaires.
- **Observation des réseaux sociaux**: Analyse de la manière dont les utilisateurs partagent leurs tenues sur Instagram et Pinterest, et identification des frustrations exprimées.

### Techniques de Brainstorming Appliquées

#### Mind Mapping
J'ai créé une carte mentale pour explorer les différentes problématiques liées à la gestion de garde-robe:
- **Branche principale 1**: Organisation physique (espace, visibilité, accessibilité)
- **Branche principale 2**: Choix quotidien (indécision, répétition, inspiration)
- **Branche principale 3**: Achats (doublons, impulsivité, coordination avec l'existant)
- **Branche principale 4**: Partage et communauté (validation sociale, découverte)

Cette carte m'a permis d'identifier le besoin central: un outil qui simplifie la visualisation et l'utilisation créative des vêtements déjà possédés.

#### Framework SCAMPER
J'ai appliqué le framework SCAMPER aux concepts existants de garde-robe digitale:

- **Substituer**: Remplacer les prises de photos complexes par un système automatisé de suppression d'arrière-plan
- **Combiner**: Fusionner la garde-robe digitale avec un guide d'accords de couleurs
- **Adapter**: Adapter l'expérience utilisateur pour la rendre aussi intuitive que l'habillage physique
- **Modifier**: Simplifier radicalement l'interface pour éviter la surcharge fonctionnelle
- **Proposer d'autres usages**: Transformer la garde-robe en source d'inspiration personnalisée
- **Éliminer**: Supprimer les fonctionnalités sociales complexes pour se concentrer sur l'essentiel
- **Réorganiser**: Concevoir l'expérience autour du glisser-déposer pour créer des tenues

#### Questions "How Might We"
J'ai formulé plusieurs questions clés pour orienter la réflexion:
- Comment pourrions-nous rendre l'ajout de vêtements à une application aussi simple que de prendre une photo?
- Comment pourrions-nous aider les utilisateurs à découvrir de nouvelles combinaisons dans leurs propres vêtements?
- Comment pourrions-nous simplifier le processus de création d'outfits tout en guidant les choix de couleurs?
- Comment pourrions-nous intégrer les tendances actuelles sans encourager la surconsommation?

### Recherche du Nom

Pour le nom de l'application, j'ai recherché un terme:
- Court et mémorisable
- En lien avec l'univers de la mode
- Facilement prononçable dans plusieurs langues
- Disponible en tant que nom de domaine et identifiant App Store

J'ai sélectionné "GARMI" dérivé du mot anglais "garment" (vêtement), qui répond à ces critères et possède une sonorité distinctive facile à retenir.

### Idées Considérées

Après ce processus de brainstorming, j'ai envisagé plusieurs concepts pour mon application:

#### Idée 1: GARMI - Garde-Robe Digitale
**Description**: Application iOS permettant aux utilisateurs de digitaliser leur garde-robe avec suppression automatique d'arrière-plan, créer des tenues facilement et recevoir des suggestions basées sur un système d'accords de couleurs.
**Forces**: Interface minimaliste, fonctionnalités distinctes, complexité technique modérée, forte utilité quotidienne.
**Statut**: Sélectionnée comme MVP.

#### Idée 2: StyleVault - Analyseur de Style Personnel
**Description**: Application analysant les préférences de style de l'utilisateur pour lui recommander des tenues basées sur son historique.
**Forces**: Personnalisation poussée, système d'apprentissage.
**Faiblesses**: Besoin d'une grande quantité de données utilisateur initiales, complexité de l'algorithme de recommandation.
**Raison du rejet**: Trop complexe pour un MVP, nécessite une base d'utilisateurs importante.

#### Idée 3: FitMatch - Réseau d'Échange de Conseils Mode
**Description**: Plateforme permettant aux utilisateurs de recevoir des conseils sur leurs tenues de la part d'autres utilisateurs.
**Forces**: Aspect communautaire, feedback authentique.
**Faiblesses**: Dépendance à une masse critique d'utilisateurs actifs, modération nécessaire.
**Raison du rejet**: Risques liés à la croissance organique de la communauté, feedback potentiellement peu constructif.

## 3. Idea Evaluation

Pour évaluer objectivement les différentes idées de projet, j'ai mis en place une méthodologie d'analyse structurée qui m'a permis de prendre une décision éclairée.

### Critères d'Évaluation

J'ai établi une matrice d'évaluation avec les critères suivants, chacun pondéré selon son importance:

| Critère | Description | Pondération |
|---------|-------------|-------------|
| **Faisabilité technique** | Difficulté de réalisation, alignement avec mes compétences en C et Python, apprentissage nécessaire de SwiftUI | 30% |
| **Différenciation** | Originalité par rapport aux solutions existantes | 25% |
| **Valeur utilisateur** | Utilité quotidienne, résolution d'un problème concret | 20% |
| **Design et UX** | Potentiel pour une expérience utilisateur élégante et intuitive | 15% |
| **Évolutivité** | Possibilité d'extension et d'amélioration post-MVP | 10% |

### Analyse SWOT des Concepts Finaux

Pour chaque idée finaliste, j'ai réalisé une analyse SWOT détaillée:

#### GARMI - Garde-Robe Digitale

**Forces (Strengths)**
- Solution à un problème quotidien concret (choix de tenues)
- Interface intuitive basée sur le glisser-déposer
- Fonctionnalité différenciante (suppression automatique d'arrière-plan)
- Guide de couleurs comme valeur ajoutée
- Modèle gratuit, contrairement à la concurrence qui utilise des systèmes d'abonnement payants

**Faiblesses (Weaknesses)**
- Défis techniques dans le traitement d'images
- Besoin d'une interface très soignée pour une expérience fluide
- Nécessité d'une masse critique de vêtements pour être utile

**Opportunités (Opportunities)**
- Potentiel d'évolution vers des fonctionnalités IA plus avancées
- Possibilités de partenariats avec des marques de mode
- Extension vers un aspect communautaire après validation du concept
- Monétisation future possible via des fonctionnalités premium tout en maintenant les fonctions de base gratuites

**Menaces (Threats)**
- Applications concurrentes existantes (bien que moins bien exécutées)
- Dépendance à la qualité des photos prises par l'utilisateur
- Risque d'abandon si l'ajout initial des vêtements est trop fastidieux
- Possibilité que les concurrents adoptent également un modèle gratuit pour contrer l'avantage

#### StyleVault - Analyseur de Style Personnel

**Forces**: Personnalisation poussée, apprentissage continu
**Faiblesses**: Complexité technique élevée, besoin important de données initiales
**Opportunités**: Potentiel d'intelligence artificielle avancée
**Menaces**: Difficulté à démontrer la valeur avant utilisation prolongée

#### FitMatch - Réseau d'Échange de Conseils Mode

**Forces**: Aspect social engageant, feedback humain authentique
**Faiblesses**: Dépendance à une communauté active dès le lancement
**Opportunités**: Potentiel viral si bien exécuté
**Menaces**: Modération complexe, risque de feedback négatif

### Matrice de Notation

J'ai évalué chaque concept sur une échelle de 1 à 5 pour chaque critère:

| Critère | Pondération | GARMI | StyleVault | FitMatch |
|---------|-------------|-------|------------|----------|
| Faisabilité technique | 30% | 4 | 2 | 3 |
| Différenciation | 25% | 4 | 5 | 3 |
| Valeur utilisateur | 20% | 5 | 4 | 3 |
| Design et UX | 15% | 5 | 3 | 4 |
| Évolutivité | 10% | 4 | 5 | 4 |
| **Score pondéré** | **100%** | **4.35** | **3.45** | **3.3** |

### Évaluation des Risques

Pour GARMI, j'ai identifié et évalué les principaux risques:

1. **Risque technique**: La suppression d'arrière-plan pourrait ne pas fonctionner parfaitement dans toutes les conditions
   - *Mitigation*: Utilisation des dernières API Vision d'Apple et ajout d'options d'édition manuelle

2. **Risque d'engagement**: Les utilisateurs pourraient ne pas compléter l'ajout initial de leur garde-robe
   - *Mitigation*: Conception d'un processus d'onboarding gamifié et progressif

3. **Risque de différenciation**: D'autres applications pourraient offrir des fonctionnalités similaires
   - *Mitigation*: Focus sur l'expérience utilisateur et l'esthétique minimaliste distinctive

### Validation du Concept

Pour valider davantage le concept GARMI, j'ai:
- Créé des wireframes basiques pour tester l'intuitivité du flux utilisateur
- Présenté le concept à 5 utilisateurs potentiels pour recueillir leurs impressions
- Benchmarké en détail les applications similaires pour identifier leurs lacunes

Les retours ont été majoritairement positifs, avec un intérêt particulier pour la simplicité d'utilisation et le système d'accords de couleurs.

## 4. Decision and Refinement

Suite à l'évaluation approfondie des différentes idées, le concept GARMI a été sélectionné comme MVP optimal. Cette section détaille le processus de décision et les étapes de raffinement du concept.

### Processus de Décision

Basé sur les scores de la matrice d'évaluation et l'analyse SWOT, GARMI s'est démarqué comme le choix le plus prometteur pour les raisons suivantes:

1. **Équilibre entre innovation et faisabilité**: Le concept offre des fonctionnalités différenciantes tout en restant réalisable techniquement avec les compétences disponibles.

2. **Forte valeur utilisateur**: GARMI résout un problème concret que de nombreuses personnes rencontrent quotidiennement (choisir et assembler des tenues).

3. **Potentiel de design distinctif**: L'application permet une approche minimaliste et élégante qui se démarque des interfaces surchargées des concurrents.

4. **Flexibilité d'évolution**: Le concept peut être développé par itérations, en commençant par un MVP solide puis en ajoutant progressivement des fonctionnalités plus avancées.

La décision finale a été prise le 15 avril 2025, après avoir pesé soigneusement les avantages comparatifs de chaque concept et leur alignement avec les objectifs du projet.

### Raffinement du Concept

Une fois GARMI sélectionné, j'ai procédé à un raffinement du concept pour définir précisément:

#### Définition du Problème Principal
"Les utilisateurs ont du mal à visualiser l'ensemble de leur garde-robe et à créer des combinaisons harmonieuses avec les vêtements qu'ils possèdent déjà."

#### Public Cible Affiné
- **Cœur de cible**: Adultes de 25-40 ans intéressés par la mode mais soucieux d'optimiser leur garde-robe existante
- **Cible secondaire**: Étudiants et jeunes professionnels avec un budget mode limité cherchant à maximiser leurs options

#### Fonctionnalités MVP Essentielles vs Optionnelles

**Fonctionnalités Essentielles (MVP)**:
- Capture photo avec suppression automatique d'arrière-plan
- Organisation par catégories de vêtements
- Création de tenues par glisser-déposer
- Guide basique d'accords de couleurs
- Sauvegarde des tenues créées

**Fonctionnalités Reportées (Post-MVP)**:
- Système de tags avancé
- Suggestions automatiques de tenues complètes
- Statistiques d'utilisation des vêtements
- Planification d'outfits par jour/semaine
- Reconnaissance avancée des vêtements par IA

#### Principes Fondamentaux de Design

J'ai établi 5 principes directeurs pour guider le développement:

1. **Simplicité avant tout**: Chaque fonctionnalité doit être immédiatement compréhensible
2. **Minimalisme visuel**: Interface épurée avec une attention particulière aux détails
3. **Fluidité d'utilisation**: Minimiser les frictions dans l'expérience utilisateur
4. **Feedback instantané**: Retour visuel immédiat pour chaque action
5. **Accessibilité**: Design inclusif prenant en compte différents types d'utilisateurs

#### Prototype Conceptuel

J'ai élaboré un premier prototype conceptuel pour visualiser le flux utilisateur principal:
1. **Écran d'accueil**: Vue simplifiée de la garde-robe et des tenues récentes
2. **Ajout de vêtement**: Processus en 3 étapes (photo, recadrage automatique, catégorisation)
3. **Créateur de tenues**: Interface de glisser-déposer avec suggestions de couleurs
4. **Bibliothèque d'outfits**: Galerie des tenues créées avec options de partage

Ces wireframes initiaux ont permis d'identifier des points d'amélioration et de tester le concept avant de passer aux maquettes détaillées.

## 5. Idea Development Documentation

Cette section synthétise l'ensemble du processus de développement de l'idée GARMI, depuis l'inspiration initiale jusqu'à la définition finale du MVP.

### Résumé du Processus Complet

Le développement du concept GARMI s'est déroulé selon un processus structuré:

1. **Phase d'inspiration**: Nourrie par ma passion pour la mode streetwear et les marques emblématiques comme Stüssy et Supreme, et par l'observation des lacunes dans les applications existantes.

2. **Phase de recherche**: Exploration des applications concurrentes, analyse de leurs forces et faiblesses, et identification d'un besoin non satisfait dans l'organisation et la visualisation de la garde-robe personnelle.

3. **Phase de brainstorming**: Utilisation de techniques comme le mind mapping, le framework SCAMPER et les questions "How Might We" pour générer et explorer diverses idées.

4. **Phase d'évaluation**: Application d'une matrice de décision avec critères pondérés et analyse SWOT pour comparer objectivement les concepts.

5. **Phase de décision**: Sélection du concept GARMI basée sur son équilibre optimal entre innovation, faisabilité technique et valeur utilisateur.

6. **Phase de raffinement**: Définition précise du problème à résoudre, du public cible, et des fonctionnalités essentielles vs secondaires.

### Documentation des Idées Rejetées

#### StyleVault - Analyseur de Style Personnel
Cette idée proposait un système d'analyse approfondie des préférences vestimentaires de l'utilisateur pour générer des recommandations personnalisées. Bien que prometteuse, elle a été rejetée principalement en raison de:
- La complexité technique élevée (algorithmes d'apprentissage machine avancés)
- La nécessité d'une grande quantité de données initiales pour être pertinente
- Le manque de valeur immédiate pour l'utilisateur (bénéfices visibles uniquement après usage prolongé)

#### FitMatch - Réseau d'Échange de Conseils Mode
Ce concept se concentrait sur l'aspect communautaire, permettant aux utilisateurs d'échanger des conseils sur leurs tenues. Il a été écarté pour:
- La dépendance critique à une masse d'utilisateurs actifs dès le lancement
- Les défis liés à la modération du contenu et au maintien d'une communauté bienveillante
- La difficulté à se différencier des plateformes sociales existantes centrées sur la mode

#### Autres Concepts Explorés
D'autres idées ont été considérées mais rapidement écartées:
- **VintageVault**: Application de suivi et valorisation de pièces vintage (trop niche)
- **OutfitCalendar**: Planificateur d'outfits basé sur la météo (fonctionnalité pouvant être intégrée à GARMI ultérieurement)
- **StyleMetrics**: Outil d'analyse statistique de l'utilisation des vêtements (intéressant mais secondaire par rapport au besoin principal)

### Rationale du MVP Final

GARMI dans sa version MVP répond à plusieurs principes fondamentaux:

1. **Principe de valeur minimale viable**: Offrir une valeur réelle et immédiate à l'utilisateur dès la première version.

2. **Principe de différenciation**: Se démarquer par une exécution soignée et une interface minimaliste, plutôt que par des fonctionnalités révolutionnaires.

3. **Principe d'évolutivité**: Concevoir une architecture permettant l'ajout fluide de fonctionnalités supplémentaires sans refonte majeure.

4. **Principe d'engagement**: Créer une expérience suffisamment satisfaisante pour encourager l'utilisation régulière et la recommandation.

Le MVP de GARMI se concentre sur l'essentiel: permettre aux utilisateurs de digitaliser facilement leur garde-robe et créer des tenues harmonieuses avec un minimum d'effort. Les fonctionnalités secondaires seront ajoutées progressivement dans les versions futures, en fonction des retours utilisateurs.

### Prochaines Étapes

Suite à cette phase de développement d'idée, les étapes immédiates sont:

1. **Phase d'apprentissage** (1 mois):
   - Formation accélérée à SwiftUI (tutoriels, documentation Apple, projets d'exercice)
   - Exploration des API Vision et CoreML pour la suppression d'arrière-plan
   - Familiarisation avec les bonnes pratiques de développement iOS

2. **Phase de conception** (2-3 semaines):
   - Création de maquettes détaillées pour chaque écran principal
   - Élaboration du système d'accords de couleurs
   - Prototypage du flux utilisateur complet

3. **Phase de développement initial** (2 mois):
   - Implémentation de l'architecture de base de l'application
   - Développement des fonctionnalités essentielles par ordre de priorité
   - Tests techniques de la suppression d'arrière-plan
   - Développement d'un premier prototype fonctionnel

4. **Phase de test et d'affinage** (1 mois):
   - Tests utilisateurs avec un groupe restreint
   - Corrections et optimisations
   - Préparation pour le déploiement

Ce planning prend en compte la nécessité d'apprendre SwiftUI tout en développant l'application, avec des périodes tampons intégrées pour faire face aux défis techniques potentiels.

### Conclusion

Le développement du concept GARMI illustre un processus décisionnel méthodique, équilibrant créativité et pragmatisme. Le MVP défini offre un point de départ solide, avec une vision claire des évolutions futures possibles.

L'application répond à un besoin concret des passionnés de mode: optimiser l'utilisation de leur garde-robe existante. En se concentrant sur une expérience utilisateur fluide et minimaliste, GARMI ambitionne de se démarquer dans un marché où les concurrents existants présentent souvent des interfaces complexes et peu élégantes.

Le succès de ce projet reposera sur l'exécution soignée des fonctionnalités essentielles, plutôt que sur la multiplication des options. Cette approche "less is more" guidera l'ensemble du développement, avec une attention particulière portée aux détails qui font la différence dans l'expérience quotidienne des utilisateurs.
