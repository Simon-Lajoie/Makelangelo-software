### Flags JVM Implémentés et Motivation

1. **MaxRAM (`-XX:MaxRAM=2g`)**
    - **Description et Motivation :**
    Limite la taille maximale du heap à 2 Go. Cela assure que l'application reste dans les contraintes de mémoire, améliorant ainsi la stabilité en empêchant l'application de dépasser les limites de mémoire.
    - Cela améliore la qualité car cela réduit le risque de crashs dus à une utilisation excessive de la mémoire.

2. **GCLogging (`-Xlog:gc*:file=gc.log`)**
    - **Description et Motivation :**
    Log et documente les informations détaillées de la gestion des garbage collections dans le fichier `gc.log`. Cela fournit des informations supplémentaires sur la gestion de la mémoire et aide à identifier les "bottleneck" des performances.
    - Cela améliore l'observabilité car les logs détaillés permettent une meilleure analyse des performances et facilitent le dépannage des problèmes liés à la gestion de la mémoire.

3. **ReservedCodeCache (`-XX:ReservedCodeCacheSize=1024M`)**
    - **Description et Motivation :**
    Augmente la taille du cache de code réservé à 1024 Mo. Cela améliore potentiellement les performances de l'application en réduisant la fréquence des garbage collections liées au cache de code, ce qui peut accélérer l'exécution.
    - Cela améliore la performance car moins de garbage collections sont nécessaires, ce qui permet une exécution plus fluide et rapide du code compilé.

4. **UseG1GC (`-XX:+UseG1GC`)**
    - **Description et Motivation :**
    Change le garbage collector en G1GC. Il offre plusieurs avantages tel que la réduction des pauses de garbage collection en effectuant le nettoyage de la mémoire de manière incrémentale et parallèle ce qui peut améliorer les performances de l'application.
    - Cela améliore la performance et l'observabilité car les pauses de garbage collection sont plus prévisibles, ce qui rend l'application plus performante et facilite l'analyse des performances.

5. **PrintCompilation (`-XX:+PrintCompilation`)**
    - **Description et Motivation :**
    Il génère des logs détaillés sur les optimisations automatiques effectuées par la JVM lors de l'exécution des tests. est utile pour une analyse plus approfondie des performances de l'application.
    - Cela améliore l'observabilité car les détails de la compilation permettent de comprendre quelles méthodes sont optimisées, facilitant ainsi l'analyse des performances.

6. **HeapDumpOnOutOfMemoryError (`-XX:+HeapDumpOnOutOfMemoryError`)**
    - **Description et Motivation :**
    Génère un dump de heap lors d'une `OutOfMemoryError`. Cela aide à identifier les fuites de mémoire et optimiser l'utilisation de la mémoire ce qui permet un débogage plus aprofondi.
    - Cela améliore l'observabilité et la qualité car le dump de heap permet d'analyser précisément les causes des problèmes de mémoire, facilitant ainsi le diagnostic et la résolution des bugs liés à la mémoire.

7. **UseStringDeduplication (`-XX:+UseStringDeduplication`)**
   - **Description et Motivation :**
     Active la déduplication des chaînes identiques dans le heap. Cela réduit la mémoire utilisé en éliminant les instances de chaînes dupliquées, améliorant la scalabilité de l'application.
   - **Fait suprenant:** +13,5 % de la mémoire gaspillée dans les applications Java est dû aux chaînes dupliquées. <br>
     **Source:** https://medium.com/@RamLakshmanan/simple-effective-g1-gc-tuning-tips-8fedbd40ab02

### Mesure de la Couverture
- **Outil :** JaCoCo
- **Description et motivation :**
    - La couverture est mesurée pour chaque build. Cela nous assure que la couverture a bien atteint un certain seuil spécifié pour maintenir la qualité du code.
    - Cela améliore la qualité car elle garantit que le code est bien testé, réduisant ainsi les risques de bugs.

### Élément d'Humour
- **Description et Motivation :** Un commentaire humoristique sur le débogage est affiché et inclus dans un fichier texte "humour.txt" pour ajouter une confirmation avec une touche d'humour. La présence de ce fichier "humour.txt" nous indique que tous les tests ont bien été exécutés avec succès.

## Instructions pour Exécuter le Workflow
- **Déclencheur :** Le workflow s'exécute à chaque push et pull request.
