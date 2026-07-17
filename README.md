# AEM AD0-E128 — Projet de récapitulatif transversal

Projet personnel de préparation à la certification **Adobe Experience Manager Sites Developer Professional AD0-E128**.

L’objectif est de reconstruire, dans un projet AEM neuf, les principales briques de développement étudiées pendant la formation : templates, policies, composants, HTL, Sling Models, services OSGi, client libraries et Style System.

> Ce dépôt correspond à un exercice personnel réalisé à partir d’un scénario entièrement fictif.
> Il ne contient aucun code, contenu, identifiant ou élément provenant d’un projet client ou employeur.

## Scénario

L’entreprise fictive **Aurelia** souhaite créer un site AEM destiné à présenter ses services aux professionnels.

Le site doit initialement proposer deux types de pages :

### Pages éditoriales

Ces pages servent à publier des articles et des actualités.

Chaque nouvelle page doit proposer une structure éditoriale cohérente, avec certains contenus présents dès sa création. Les auteurs peuvent ensuite enrichir le contenu avec une sélection contrôlée de composants.

### Pages de campagne

Ces pages servent à présenter des offres ponctuelles.

Le contenu central est initialement vide afin de permettre des compositions plus libres, tout en limitant les auteurs à une liste de composants validés.

### Structure commune

Toutes les pages possèdent :

* un en-tête imposé ;
* un pied de page imposé ;
* une zone centrale éditable ;
* des règles de composants autorisés adaptées au type de page.

Le projet doit être entièrement reproductible à partir de Git.

## Méthode de travail

Le projet est réalisé sous la forme d’un exercice semi-guidé.

Pour chaque évolution :

1. un besoin fonctionnel est présenté ;
2. une proposition d’architecture AEM est formulée ;
3. la proposition est validée ou corrigée ;
4. l’intégration est réalisée de manière autonome ;
5. le code et le résultat obtenu dans AEM sont revus ;
6. une aide progressive est fournie uniquement en cas de blocage.

Les solutions ne sont donc pas fournies à l’avance. Chaque mécanisme AEM doit être justifié par le besoin fonctionnel.

## Compétences travaillées

Le projet doit progressivement mobiliser :

* l’AEM Project Archetype et la structure Maven ;
* les modules `core`, `ui.apps`, `ui.content`, `ui.config` et `ui.frontend` ;
* les Template Types ;
* les Editable Templates ;
* la structure et le contenu initial des templates ;
* les content policies ;
* les composants autorisés ;
* les Core Components ;
* les Proxy Components ;
* les composants custom ;
* les dialogs et configurations d’édition ;
* HTL ;
* les Sling Models ;
* les injections Sling Models ;
* le Sling Delegation Pattern ;
* les services OSGi ;
* les tests unitaires et AEM Mocks ;
* les Client Libraries ;
* le chargement des ressources front-end ;
* le Style System ;
* le build et l’installation sur une instance AEM locale.

## Répartition du travail

Le code spécifique à AEM est réalisé dans le cadre de l’exercice :

* XML FileVault et JCR ;
* définitions de composants ;
* dialogs ;
* HTL ;
* Sling Models ;
* services OSGi ;
* configurations AEM ;
* tests AEM.

Le CSS, le SCSS, le JavaScript et le TypeScript ne constituent pas l’objet principal de l’exercice. Ils peuvent être générés séparément lorsque leur intégration devient nécessaire.

La décision d’utiliser une clientlib, une variante de style ou un comportement JavaScript reste néanmoins une décision d’architecture AEM à justifier.

## Modules principaux

* `core` : Sling Models, services OSGi et tests Java ;
* `ui.apps` : composants, dialogs, HTL, proxies et clientlibs installés sous `/apps` ;
* `ui.content` : templates, policies et contenu initial sous `/conf` et `/content` ;
* `ui.config` : configurations OSGi ;
* `ui.frontend` : sources SCSS, JavaScript et TypeScript ;
* `dispatcher` : configuration Dispatcher ;
* `all` : package global d’installation.

## Construction du projet

Construire l’ensemble du projet :

```bash
mvn clean install
```

Construire et installer le package global sur l’instance Author locale :

```bash
mvn clean install -PautoInstallSinglePackage
```

Exécuter les tests du module Java :

```bash
mvn test -pl core
```

Construire les ressources front-end :

```bash
cd ui.frontend
npm ci
npm run prod
```

## Prérequis

* une version compatible de Java ;
* Maven ;
* Node.js et npm ;
* une instance locale du SDK AEM as a Cloud Service.

Le SDK AEM, le Quickstart Jar, les Dispatcher Tools et les autres binaires propriétaires Adobe ne sont pas distribués dans ce dépôt.

## Sécurité du dépôt

Les éléments suivants ne doivent jamais être versionnés :

* mots de passe et jetons d’accès ;
* clés privées et certificats ;
* fichiers `.env` contenant des secrets ;
* identifiants Cloud Manager ;
* URLs ou configurations d’environnements professionnels ;
* exports provenant de projets clients ;
* contenus, assets ou documents confidentiels ;
* binaires du SDK AEM.

## Statut

Projet éducatif en cours de développement.

Aurelia est une entreprise fictive créée uniquement pour ce scénario.

Ce projet n’est ni affilié ni approuvé par Adobe ou par un employeur.

## Licence

Ce projet conserve la licence Apache License 2.0 fournie avec l’AEM Project Archetype.
