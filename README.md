# Minigrep

Minigrep est un outil de commande de lignes d'interface (CLI tool) qui recrée avec le language Rust une version simplifiée de la commande _grep_.

L'outil permet donc de trouver des occurences de textes dans des fichiers par le biais de la commande suivante

cargo run -- _query_ _./chemin_fichier.txt_

La recherche par défaut est case sensitive mais la commande peut prendre les options suivantes:

- En argument:
  - _--sensitive_ pour une recherche case sensitive (ex: les occurrences "rUst", "Rust"... ne fonctionneront pas pour la recherche "rust")
  - _--insensitive_ pour une recherche case insensitive (ex: les occurrences "rUst", "Rust"... fonctionneront pour la recherche "rust")
- En variable d'environnement:
  - _IGNORE_CASE=1_ pour une recherche case insensitive

## Utilisation de Rust

Le code reprend des concepts clés de Rust:

- La gestion de l'_ownership_
- L'error handling des éléments du programme pouvant causer une erreur
- L'utilisation d'un _struct_ pour regrouper des données qui font sens ensemble et l'implémentation de méthode par le biais de _impl_
- Gestion des _lifetimes_ pour éviter les problème de références perdues (dangling references)
- Utilisation des _iterators_ et _closures_ dans les fonctions de recherche pour un code plus court et élégant

## Structure

Le projet inclut l'implémentation des fonctionnalité par le le biais du TDD (Test-Driven Development) pour s'assurer du bon fonctionnement du code grâce aux tests.

Le code dans _main.rs_ contient la récupération des arguments du CLI, la configuration du programme ainsi que la la gestion d'erreurs, tandis que lib.rs contient la logique de l'application ainsi que les tests unitaires liées aux fonctions du projet.

### Testez par vous-mêmes

Après avoir récupérer le projet, vous pouvez tester le projet à l'aide des commande suivantes:

- _cargo run -- query ./chemin_fichier.txt_ pour essayer une recherche (pensez bien à vous placer dans le dossier du projet)
- _cargo test_ pour lancer les tests unitaires

Par défaut, l'output de la recherche se fait directement dans le terminal. Pour obtenir le résultat dans un fichier, utilisez _> nom_fichier.txt_ (le fichier output.txt présent dans le projet est un exemple de résultat de poem.txt)

### Crédits

Ce projet minigrep a été réalisé en suivant le projet du Chapitre 12 du livre officiel du language Rust: [_The Rust programming Language_](https://doc.rust-lang.org/book/ch12-00-an-io-project.html)

Quelques modifications ont été apportés pour améliorer le code, notamment:

- le remplacement du clonage de certaines variables par
- l'utilisation des lifetimes pour une question de performances, ainsi que l'ajout des options de case par le biais des arguments
