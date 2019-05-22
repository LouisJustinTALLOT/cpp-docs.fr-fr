---
title: Nouveautés de C++ dans Visual Studio 2019
ms.date: 05/13/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 19eaa9d4ed1cf12e721825f998fa674363eda488
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934140"
---
# <a name="whats-new-for-c-in-visual-studio-2019"></a>Nouveautés de C++ dans Visual Studio 2019

Visual Studio 2019 comprend un grand nombre de mises à jour et de correctifs de l’environnement Microsoft C++. Nous avons résolu de nombreux bogues et problèmes dans le compilateur et les outils, beaucoup d’entre eux ayant été soumis par des clients via les options [Signaler un problème](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) et [Faire une suggestion](https://developercommunity.visualstudio.com/spaces/62/index.html) sous **Envoyer des commentaires**. Merci d’avoir signalé ces bogues. Pour plus d’informations sur l’ensemble des nouveautés de Visual Studio, visitez [Nouveautés de Visual Studio](/visualstudio/ide/whats-new-visual-studio-2019).

## <a name="c-compiler"></a>compilateur C++

- Une prise en charge améliorée des fonctionnalités et correctifs d’exactitude C++17, plus une prise en charge expérimentale de fonctionnalités C++20 comme les modules et les coroutines. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2019](../cpp-conformance-improvements.md).

- L’option `/std:c++latest` inclut désormais les fonctionnalités de C++20 qui ne sont pas nécessairement complètes, notamment la prise en charge initiale de l’opérateur C++20 \<=> (« spaceship ») pour une comparaison triple.

- Le commutateur `/Gm` du compilateur C++ est maintenant déprécié. Envisagez de désactiver le commutateur `/Gm` dans vos scripts de build s’il y est défini explicitement. Vous pouvez cependant ignorer sans problème l’avertissement de dépréciation de `/Gm`, car il n’est pas traité en tant qu’erreur quand vous utilisez « Considérer les avertissements comme des erreurs » (`/WX`).

- Comme MSVC commence la mise en œuvre de fonctionnalités à partir du brouillon standard C++20 sous l’indicateur `/std:c++latest`, `/std:c++latest` est désormais incompatible avec `/clr` (toutes les saveurs), `/ZW`, et `/Gm`. Dans Visual Studio 2019, utilisez le mode `/std:c++17` ou `/std:c++14` lors de la compilation avec `/clr`, `/ZW` ou `/Gm` (consultez la liste à puces précédente).

- Les en-têtes précompilés ne sont plus générés par défaut pour les applications de bureau et console C++.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, sécurité, diagnostics et gestion des versions

Analyse améliorée avec `/Qspectre` afin de fournir une aide à l’atténuation des risques pour Spectre Variant 1 (CVE-2017-5753). Pour plus d’informations, consultez [Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Améliorations apportées à la bibliothèque standard C++

- Implémentation de nouvelles fonctionnalités de bibliothèque et de nouveaux correctifs d’exactitude C++17 et C++20. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2019](../cpp-conformance-improvements.md).

- Le format clang a été appliqué aux en-têtes de la bibliothèque standard C++ pour une meilleure lisibilité.

- Étant donné que Visual Studio prend désormais en charge Uniquement mon code pour C++, la bibliothèque standard n’a plus besoin de fournir de mécanisme personnalisé pour `std::function` et `std::visit` pour obtenir le même effet. La suppression de ce mécanisme n’a en grande partie aucun effet visible par l’utilisateur, à ceci près que le compilateur ne produira plus de diagnostics indiquant les problèmes de ligne 15732480 ou 16707566 de \<type_traits > ou de \<variant>.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Améliorations de performances/débit dans le compilateur et la bibliothèque standard

- Améliorations du débit de la génération, notamment la gestion par l’éditeur de liens des E/S de fichier, et la durée de l’établissement des liens dans la création et la fusion des types PDB.

- Ajout de la prise en charge de base de la vectorisation SIMD OpenMP. Vous pouvez l’activer avec le nouveau commutateur de compilateur `-openmp:experimental`. Cette option permet la vectorisation potentielle des boucles annotées avec `#pragma omp simd`. La vectorisation n’est pas garantie, et les boucles annotées mais pas vectorisées génèrent un avertissement. Aucune clause SIMD n’est prise en charge : elles sont simplement ignorées et un avertissement est généré.

- Ajout d’un nouveau commutateur de ligne de commande d’incorporation (inlining) `-Ob3`, qui est une version plus agressive de `-Ob2`. `-O2` (optimiser le fichier binaire pour la vitesse) implique toujours `-Ob2` par défaut. Si vous trouvez que le compilateur n’incorpore pas de façon suffisamment agressive, envisagez de passer `-O2 -Ob3`.

- Pour prendre en charge la vectorisation manuelle des boucles avec des appels de fonctions de bibliothèque mathématique et certaines autres opérations telles que la division d’entiers, nous avons ajouté la prise en charge des fonctions intrinsèques SVML (Short Vector Math Library). Ces fonctions calculent les vecteurs équivalents 128 bits, 256 bits ou 512 bits. Pour obtenir les définitions des fonctions prises en charge, consultez le [Guide des intrinsèques Intel](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Optimisations nouvelles et améliorées :

  - Simplifications arithmétiques et de pliage de constante pour les expressions à l’aide d’intrinsèques de vecteur SIMD, pour les formes float et integer.

  - Analyse plus puissante pour extraire des informations de flux de contrôle (instructions if/else/switch) afin de supprimer les branches toujours prouvées comme étant true ou false.

  - Amélioration du déroulement de memset de façon à utiliser les instructions de vecteur SSE2.

  - Amélioration de la suppression des copies de struct/classes inutiles, en particulier pour les programmes C++ qui passent par valeur.

  - Amélioration de l’optimisation du code utilisant `memmove`, comme `std::copy` ou `std::vector` et une construction `std::string`.

- Optimisation de la conception physique de la bibliothèque standard afin d’éviter la compilation des parties de la bibliothèque standard qui ne sont pas dans un #include, ce qui réduit de moitié le temps de génération d’un fichier vide qui inclut seulement \<vector>. En conséquence de cette modification, vous devrez peut-être ajouter des directives #include pour les en-têtes qui précédemment étaient indirectement inclus. Par exemple, le code qui utilise `std::out_of_range` doit maintenant #include \<stdexcept>. Le code qui utilise un opérateur d’insertion de flux doit maintenant #include \<ostream>. L’avantage est que seule les unités de traduction qui utilisent réellement des composants \<stdexcept> ou \<ostream> payent le débit de coût pour les compiler.

- `if constexpr` a été appliqué à plusieurs endroits dans la bibliothèque standard pour un débit amélioré et une taille de code réduite dans les opérations de copie, dans les permutations comme l’inversion et la rotation et dans la bibliothèque d’algorithmes parallèles. 

- La bibliothèque standard utilise désormais `if constexpr` en interne afin de réduire la compilation même en mode C++14.

- La détection de lien dynamique de runtime pour la bibliothèque d’algorithmes parallèles n’utilise plus une page entière pour stocker le tableau de pointeurs de fonction. Le marquage de cette mémoire en lecture seule n’est plus considéré comme pertinent pour des raisons de sécurité.

- `std::thread` du constructeur n’attend plus que le thread démarre, et n’insère plus autant de calques d’appels de fonction entre la bibliothèque C sous-jacente `_beginthreadex` et l’objet fourni pouvant être appelé. Précédemment `std::thread` mettait 6 fonctions entre `_beginthreadex` et l’objet fourni pouvant être appelé, ce nombre a été réduit à seulement 3 (dont 2 sont uniquement `std::invoke`). Cela résout également un bogue obscur de minutage qui bloquait le constructeur de `std::thread` si l’horloge du système avait été modifiée au moment précis où un `std::thread` était créé.

- Correction d’une régression des performances dans `std::hash` que nous avons introduit lors de l’implémentation `std::hash<std::filesystem::path>`.

- La bibliothèque standard utilise désormais dans plusieurs endroits, des destructeurs au lieu de blocs catch pour atteindre l’exactitude. Il en résulte une meilleure interaction du débogueur ; les exceptions que vous levez via la bibliothèque standard dans les emplacements concernés apparaîtront désormais comme ayant été levés à partir de leur site de levée d’origine, plutôt que d’une nouvelle levée. Tous les blocs catch de bibliothèque standard n’ont pas tous été éliminées ; nous nous attendons à ce que le nombre de blocs catch soit réduit dans les versions ultérieures de MSVC.

- Un codegen non optimal dans `std::bitset` provoqué par une levée conditionnelle à l’intérieur d’une fonction noexcept a été résolu en factorisant le chemin d’accès levant.

- Les familles `std::list` et `std::unordered_*` utilisent des itérateurs de non débogage en interne dans plusieurs endroits.

- Plusieurs membres `std::list` ont été modifiés pour réutiliser les nœuds de la liste lorsque cela est possible au lieu de les libérer et de les redistribuer. Par exemple, considérant un `list<int>` dont la taille est déjà de 3, un appel à `assign(4, 1729)` remplacera maintenant les entiers dans les trois premiers nœuds de liste et allouera un nouveau nœud de liste avec la valeur 1 729, plutôt que de libérer les trois nœuds de liste, puis d’allouer quatre nouveaux nœuds de liste avec la valeur 1 729.

- Tous les appels de la bibliothèque standard à `erase(begin(), end())` ont été remplacés par `clear()`.

- `std::vector` initialise et efface désormais les éléments plus efficacement dans certains cas.

- Améliorations apportées à `std::variant` pour le rendre plus adapté à l’optimiseur, ce qui entraîne la génération d’un meilleur code. L’incorporation (inlining) de code est désormais bien meilleure avec `std::visit`.

## <a name="c-ide"></a>IDE C++

### <a name="live-share-c-support"></a>Prise en charge de C++ par Live Share

[Live Share ](/visualstudio/liveshare/) prend désormais en charge C++, ce qui permet aux développeurs utilisant Visual Studio ou Visual Studio Code de collaborer en temps réel. Pour plus d’informations, consultez [Announcing Live Share for C++: Real-Time Sharing and Collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode pour C++

IntelliCode est une extension facultative (ajoutée comme un composant de charge de travail dans 16.1) qui exploite toutes ses données de formation et le contexte de votre code pour suggérer les éléments de code que vous êtes le plus susceptible d’utiliser en haut de votre liste de saisie semi-automatique. Il peut souvent vous éviter de faire défiler la liste vers le bas. Pour C++, IntelliCode est le plus performant quand vous utilisez des bibliothèques courantes comme la bibliothèque standard. Pour plus d’informations, consultez [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>Modèle IntelliSense

La **barre de modèles** utilise maintenant l’interface utilisateur de la **fenêtre d’aperçu** au lieu d’une fenêtre modale, prend en charge les modèles imbriqués et prérenseigne les arguments par défaut dans la **fenêtre d’aperçu**. Pour plus d’informations, consultez [Template IntelliSense Improvements for Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/). Une liste déroulante **Utilisés le plus récemment** dans la **barre de modèles** vous permet de basculer rapidement entre des ensembles antérieurs d’exemples d’arguments.

### <a name="new-start-window-experience"></a>Nouvelle fenêtre de démarrage

Lors du lancement de l’IDE, une nouvelle fenêtre de démarrage s’affiche avec des options pour ouvrir des projets récents, cloner le code à partir du contrôle de code source, ouvrir du code local en tant que solution ou dossier, ou créer un projet. La boîte de dialogue Nouveau projet a également été repensée pour permettre une expérience de recherche en premier avec possibilité de filtrage.

### <a name="new-names-for-some-project-templates"></a>Nouveaux noms pour certains modèles de projet

Nous avons renommé plusieurs noms de modèles de projet et changé certaines descriptions en raison de la mise à jour de la boîte de dialogue Nouveau projet.

### <a name="various-productivity-improvements"></a>Différentes améliorations de la productivité

Visual Studio 2019 inclut les fonctionnalités suivantes qui rendent le codage plus facile et plus intuitif :

- Corrections rapides pour :
  - Ajouter les #include manquants
  - NULL en nullptr
  - Ajouter un point-virgule manquant
  - Résoudre l’absence d’un espace de noms ou d’une étendue
  - Remplacer les opérandes d’indirection incorrects (\* en & et & en \*)
- Info express pour un bloc en plaçant le curseur sur l’accolade fermante
- Afficher un aperçu de l’en-tête / du fichier de code
- Atteindre la définition sur un #include ouvre le fichier

Pour plus d’informations, consultez [C++ Productivity Improvements in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/).

**Visual Studio 2019 version 16.1**

### <a name="quickinfo-improvements"></a>Améliorations de Info express

L’info-bulle Info express respecte désormais la colorisation sémantique de votre éditeur. Il dispose également d’un nouveau lien de **recherche en ligne** qui recherche de la documentation en ligne pour en savoir plus sur la construction de code survolé. En ce qui concerne le code souligné en rouge, ce lien fourni par Info express effectue des recherches d’erreurs en ligne. De cette façon, vous n’avez pas besoin de retaper le message dans votre navigateur. Pour en savoir plus, consultez la section relative aux [améliorations de Info express dans Visual Studio 2019 : Colorisation et recherche en ligne](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>IntelliCode disponible dans la charge de travail C++

IntelliCode est désormais fourni en tant que composant facultatif dans la charge de travail **Développement Desktop en C++**. Pour en savoir plus, voir [IntelliCode C++ amélioré désormais fourni avec Visual Studio 2019](https://devblogs.microsoft.com/cppblog/).

## <a name="cmake-support"></a>Prise en charge de CMake

- Prise en charge de CMake 3.14

- Visual Studio peut maintenant ouvrir les caches CMake existants générés par des outils externes, comme CMakeGUI, des systèmes de génération de métadonnées personnalisés ou des scripts de génération appelant eux-mêmes cmake.exe.

- Amélioration des performances d’IntelliSense.

- Un nouvel éditeur de paramètres fournit une alternative à la modification manuelle de CMakeSettings.json et offre une similarité avec CMakeGUI.

- Visual Studio vous aide à démarrer votre développement en C++ avec CMake sur Linux en détectant si vous avez une version compatible de CMake sur votre machine Linux, et ne vous propose pas de l’installer pour vous.

- Les paramètres incompatibles dans CMakeSettings, comme les incompatibilités d’architectures ou les paramètres de générateur CMake incompatibles, sont marqués par des tildes dans l’éditeur JSON et par des erreurs dans la liste d’erreurs.

- La chaîne d’outils vcpkg est automatiquement détectée et activée pour les projets CMake qui sont ouverts dans l’IDE, une fois que `vcpkg integrate install` a été exécuté. Ce comportement peut être désactivé en spécifiant un fichier de chaîne d’outils vide dans cmakesettings.

- Les projets CMake autorisent maintenant le débogage Uniquement mon code par défaut.

- Les avertissements d’analyse statique peuvent désormais être traités en arrière-plan et affichés dans l’éditeur pour les projets CMake.

- Messages de début et de fin de génération et de configuration plus clairs pour les projets CMake, et prise en charge de l’interface utilisateur de progression de la génération de Visual Studio. De plus, il existe désormais un paramètre de niveau de détail CMake dans **Outils > Options** pour personnaliser le niveau de détail des messages de génération et de configuration CMake dans la fenêtre Sortie.

- Le paramètre `cmakeToolchain` est désormais pris en charge dans CMakeSettings.json pour spécifier des chaînes d’outils sans modifier manuellement la ligne de commande CMake.

- Nouveau raccourci pour le menu **Tout générer** (**Ctrl+Maj+B**).

**Visual Studio 2019 version 16.1**

- Prise en charge intégrée pour la modification, la génération et le débogage de projets CMake avec Clang/LLVM. Pour en savoir plus, voir [Prise en charge Clang/LLVM dans Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-wsl"></a>Linux et WSL

**Visual Studio 2019 version 16.1**

- Prise en charge de [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) dans les projets d’inter-plateformes Linux et CMake. Pour en savoir plus, voir [AddressSanitizer (ASan) pour la charge de travail Linux dans Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Prise en charge intégrée de Visual Studio pour l’utilisation de C++ avec le sous-système Windows pour Linux (WSL). Pour en savoir plus, voir [ C++ avec Visual Studio 2019 et le sous-système Windows pour Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>Intégration d’IncrediBuild

IncrediBuild est désormais fourni en tant que composant facultatif dans la charge de travail **Développement Desktop en C++**. Le moniteur de build IncrediBuild est entièrement intégré à l’IDE de Visual Studio. Pour en savoir plus, voir [Visualiser votre build avec le moniteur de build d’IncrediBuild et Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).
 
## <a name="debugging"></a>Débogage

- Pour les applications C++ exécutées sur Windows, les fichiers PDB se chargent désormais dans un processus 64 bits distinct. Ce changement résout plusieurs problèmes de plantage qui pouvaient survenir quand le débogueur manquait de mémoire au moment du débogage d’applications contenant de nombreux modules et fichiers PDB.

- La recherche est activée dans les fenêtres **Espion**, **Autos**, et **Variables locales**.

## <a name="windows-desktop-development-with-c"></a>Développement Windows Desktop avec C++

- Ces Assistants C++ ATL/MFC suivants ne sont plus disponibles :

  - Assistant Composant COM+ 1.0 ATL
  - Assistant Composant ASP ATL
  - Assistant Fournisseur OLEDB ATL
  - Assistant Page de propriétés ATL
  - Assistant Consommateur OLEDB ATL
  - Consommateur ODBC MFC
  - Classe MFC à partir d’un contrôle ActiveX
  - Classe MFC à partir d’une bibliothèque de types.

  Les exemples de code pour ces technologies sont archivés dans Microsoft Docs et dans le dépôt GitHub VCSamples.

- Le SDK Windows 8.1 n’est plus disponible dans le programme d’installation de Visual Studio. Nous vous recommandons de mettre à niveau vos projets C++ vers la dernière version du SDK Windows 10. Si vous avez une dépendance dure envers la version 8.1, vous pouvez la télécharger à partir de l’archive du SDK Windows.

- Le ciblage de Windows XP ne sera plus disponible pour le dernier ensemble d’outils C++. Le ciblage de XP avec des bibliothèques et le compilateur MSVC de niveau Visual Studio 2017 est toujours pris en charge et peut être installé par le biais de « Composants individuels ».

- Notre documentation décourage activement l’utilisation de Fusionner les modules pour le déploiement Visual C++ Runtime. Dans cette version, nous allons encore un peu plus loin en marquant nos MSM comme étant dépréciés. Envisagez la migration de votre déploiement central VCRuntime des MSM vers le package redistribuable.

## <a name="mobile-development-with-c-android-and-ios"></a>Développement mobile en C++ (Android et iOS)

L’expérience Android C++ utilise désormais Android SDK 25 et Android NDK 16b par défaut.

## <a name="clangc2-platform-toolset"></a>Ensemble d’outils de plateforme Clang/C2

Le composant expérimental Clang/C2 a été supprimé. Utilisez l’ensemble d’outils MSVC pour garantir une totale conformité aux standards C++ avec `/permissive-` et `/std:c++17`, ou la chaîne d’outils Clang/LLVM pour Windows.

## <a name="code-analysis"></a>Analyse du code

- L’analyse du code s’exécute désormais automatiquement en arrière-plan. Les avertissements sont marqués par des tildes verts dans l’éditeur à mesure que vous tapez. Pour plus d’informations, consultez [In-editor code analysis in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/).

- Nouvelles règles ConcurrencyCheck expérimentales pour les types de bibliothèques standard courantes à partir de l’en-tête \<mutex>. Pour plus d’informations, consultez [Concurrency Code Analysis in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Une implémentation partielle mise à jour du [vérificateur de profil de durée de vie](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), qui détecte les références et les pointeurs non résolus. Pour plus d’informations, consultez [Lifetime Profile Update in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Plus de vérifications liées aux coroutines, notamment C26138, C26810, C26811 et la règle expérimentale C26800. Pour plus d’informations, consultez [New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

**Visual Studio 2019 version 16.1**

Nouveaux correctifs rapides pour des vérifications de variables non initialisées. Pour en savoir plus, voir [Nouveaux correctifs rapides d’analyse de code pour la mémoire non initialisée (C6001) et les avertissements d’utilisation avant init (C26494)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Test unitaire

Le modèle de projet de test C++ managé n’est plus disponible. Vous pouvez continuer à utiliser le framework de test C++ managé dans vos projets existants. Pour les nouveaux tests unitaires, utilisez un des frameworks de test natifs pour lesquels Visual Studio fournit des modèles (MSTest, Google Test) ou le modèle de projet de test C# managé.
