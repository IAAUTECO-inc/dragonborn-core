# Dragonborn Core

Ce projet est une application Android nommée "Wheels".

## Configuration du projet

Le projet utilise Gradle comme système de build. Pour garantir la cohérence entre les environnements de développement, il est configuré pour utiliser le Gradle Wrapper.

---

## Sécurité du Build

La sécurité du processus de build est essentielle pour garantir l'intégrité du logiciel. Les mesures suivantes ont été mises en place.

### 1. Mise à jour du Gradle Wrapper

Le projet a été mis à jour pour utiliser **Gradle 8.4**. L'utilisation d'une version récente de Gradle est cruciale pour bénéficier des derniers correctifs de sécurité et des améliorations de performance.

La configuration du wrapper (`gradle/wrapper/gradle-wrapper.properties`) a été modifiée pour utiliser une URL sécurisée (`https`) pour le téléchargement de la distribution Gradle.

- **Avant :** `http://services.gradle.org/distributions/gradle-5.1.1-all.zip`
- **Après :** `https://services.gradle.org/distributions/gradle-8.4-all.zip`

Ce changement protège le processus de build contre les attaques de type "Man-in-the-Middle" (MitM) lors du téléchargement de Gradle.

### 2. Bonnes pratiques pour l'environnement d'exécution

Le script de démarrage `gradlew.bat` dépend de l'environnement système pour trouver l'exécutable Java. Pour minimiser les risques d'exécution de code malveillant, il est fortement recommandé de :

- **Définir la variable d'environnement `JAVA_HOME`** pour qu'elle pointe explicitement vers une installation Java de confiance.
- **Auditer régulièrement la variable `PATH`** pour s'assurer qu'aucun répertoire non fiable ne précède les répertoires système légitimes.