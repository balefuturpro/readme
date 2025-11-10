# # Challenge Frontend E-shop Gallery Kata
# Vue 3 + TypeScript + Vite
**Version: 1.0**
## 1. Contexte

Ce challenge kata est un **MVP d’un E-shop Gallery** construit avec **Vue 3, Vite, TypeScript**, optimisé pour le, **SSR**, la **performance**, et la **sécurité**.

L’objectif est de démontrer une architecture front-end de **niveau production**, respectant les bonnes pratiques de scalabilité, performance, et maintenabilité.

## 2. Fonctionnlités

**Page Liste des produits** avec recherche produits par des filtres multi-critères.
**Panier d'achats** avec la liste des prdouits commandés ainsi que leurs quantités, un résumé avec le prix total et la quantité total commandé.

## 3. Choix Technologique

| Technologies                   | Détails                                                                                                                     |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Vue 3** | simple, réactive et structure modulaire.                                                                                     |
| **Vite**        | build rapide et performant.                                                |
| **TypeScript**           | Sécurité de typage, code maintenable et s'intégre facilement avec Vue 3 et Vite.                                              |
| **Pinia**        | simplifie la gestion d'état global, réactive et s'intégre facilement à Vue 3.                                                                                |
| **Axios**        | simplifie les requêtes HTTP pour l'accès aux données, transformation automatique des données JSON et intégre la gestion des erreurs.                                                                                              |
| **Eslint**        | garantit la qualité du code et le respect des bonnes pratiques.                                                                                             |
| **Prettier**        | Assure une mise en forme de code cohérente et automatisé.                                                                                             |
| **Tailwind CSS**        | Simple, rapide, moderne et responsve design                                                                                            |
| **Axe-Core**        | Permet de tester l'accessibilité A11y de l'application.                                                                                             |
| **PWA Service Worker**        | Permet de gérer le mode offline avec le caching.                                                                                             |
| **Workbox-Window**        | Permet la configuration du caching, la mise à jour du service zorker et la gestion automatique des ressources offline.|
| **SSR**        | Permet d'améliorer le référencement SEO, le rendu initial et le temps de chargement des pages.|
| **Git**        | Permet le versionnement du code, la collaboration en équipe et le suivi des modifiications du projet.|
| **Composition API**        | Permet une meilleure organisation, réutilisqbilité et maintenabilité du code dans Vue 3.|

## 4. Architecture : Clean Architecture combinant un model hybride MVC, Pinia, SSR et PWA Service Worker

L’architecture est structurée en **5 couches principales**, garantissant une **séparation claire des responsabilités** et une **extensibilité à long terme**.

* **Diagramme d’Architecture**

![Clean Architecture SSR + Pinia + MVC + PWA](./docs/architecture-diagram.png)

> Diagramme illustrant la structure **hybride Clean Architecture** avec **SSR, PWA, MVC et Store Pinia**.

* **Détails** 

| Couche| Rôle                                                                                                                     |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Server-Side Rendering (SSR) Layer** | Permet de gérer le rendu initial des pages côté serveur via Express et Vite SSR Renderer, avant que Vue ne prenne le relais côté client.                                                                                     |
| **UI / Presentation Layer**        | C’est la vue du modèle MVC qui est responsable de l’affichage, de la navigation et de l’accessibilité. Elle consomme les données et les états fournis par la couche métier (Pinia).|
| **Infrastructure Layer**        | Cette couche permet de gérer tous les services transverses, techniques, et **hors logique métier** .|
| **Domain Layer**           | Cette couche définit comment les données doivent être manipulées, transformées et stockées globalement via Pinia.|
| **Data Layer**        | Cette couche est responsable de l’accès aux sources de données externes (API, localStorage, cache). Elle isole les appels réseau et gère les erreurs et transformationssimplifie la gestion d'état global, réactive et s'intégre facilement à Vue 3.|

## 5. Structure du projet

```bash
mini-ecomm-baa/
│
├── public/
│   ├── pwa-serviceworker.js      # Service Worker principal pour la PWA service worker pour la gestion cache et offline)
│   └── vite.svg                  # Logo par défaut utilisé dans index.html
│
├── server/
│   └── server.js                 # Serveur Express contenant le SSR et les CSP Headers
│
├── src/
│   ├── api/                      # Appels HTTP via Axios vers DummyJSON API
│   ├── assets/                   # Ressources statiques : images et fonts
│   ├── components/               # Contient les Composants UI réutilisables
│   ├── composables/              # Contient les Hooks Composition API
│   ├── model/                    # Modèles, types et interfaces TypeScript
│   ├── router/                   # Configuration du Vue Router
│   │   └── index.ts
│   ├── store/                    # Stores Pinia contenant Store Cart et Product
│   │   ├── cartStore.ts
│   │   └── productStore.ts
│   ├── utils/                    # Contient les Fonctions utilitaires réutilisables dans tout le projet
│   │   └── cacheUtils.ts         # Gère les stratégies de cache
│   ├── views/                    # Pages principales
│   │   ├── CartView.vue          # Panier d’achat
│   │   └── ProductView.vue       # Page liste produits avec recherche et filtres multi-critères
│   ├── app.ts                    # Point d’entrée SSR côté serveur
│   ├── App.vue                   # Composant racine de l’application
│   ├── entry-server.ts           # Entrée pour le rendu côté serveur (SSR)
│   ├── main.ts                   # Entrée client-side pour l’hydratation Vue
│   ├── registerServiceWorker.ts  # Enregistrement du Service Worker
│   ├── style.css                 # Style global CSS avec Tailwind
│   └── vite-env.d.ts             # Déclarations TypeScript pour Vite
│
├── .editorconfig                 # Normalisation du format de code entre IDE
├── .env.local                    # Configuration des variables d’environnement local
├── .gitignore                    # Fichiers et dossiers exclus du dépôt Git
├── .prettierrc                   # Configuration Prettier
├── eslint.config.js              # Configuration ESLint
├── index.html                    # Point d’entrée HTML de l’application
├── package-lock.json             # Lockfile des dépendances NPM
├── package.json                  # contient l'ensemble des dépendances
├── README.md                     # Documentation principale du projet
├── tsconfig.app.json             # Configuration TypeScript spécifique à l’app Vue
├── tsconfig.json                 # Configuration TypeScript principale
├── tsconfig.node.json            # Configuration TypeScript pour le serveur et outils Node
└── vite.config.ts                # Configuration principale Vite










