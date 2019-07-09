---
title: Nouveautés de C++ dans Visual Studio
ms.date: 07/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: f02c5878f5f741c216499f619bfd1392483bfa86
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552345"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Nouveautés de C++ dans Visual Studio

::: moniker range=">=vs-2019"

Visual Studio 2019 comprend un grand nombre de mises à jour et de correctifs de l’environnement Microsoft C++. Nous avons résolu plusieurs bogues et problèmes dans le compilateur et les outils. Beaucoup de ces problèmes ont été soumis par des clients via les options [Signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) et [Faire une suggestion](https://developercommunity.visualstudio.com/spaces/62/index.html) sous **Envoyer des commentaires**. Merci d’avoir signalé ces bogues. Pour plus d’informations sur l’ensemble des nouveautés de Visual Studio, visitez [Nouveautés de Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2017, consultez [Nouveautés de C++ dans Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2015 et versions antérieures, consultez [Nouveautés de Visual C++ entre 2003 et 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>compilateur C++

- Une prise en charge améliorée des fonctionnalités et correctifs d’exactitude C++17, plus une prise en charge expérimentale de fonctionnalités C++20 comme les modules et les coroutines. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2019](cpp-conformance-improvements.md).

- L’option `/std:c++latest` inclut désormais les fonctionnalités de C++20 qui ne sont pas nécessairement complètes, notamment la prise en charge initiale de l’opérateur C++20 \<=> (« spaceship ») pour une comparaison triple.

- Le commutateur `/Gm` du compilateur C++ est maintenant déprécié. Envisagez de désactiver le commutateur `/Gm` dans vos scripts de build s’il y est défini explicitement. Vous pouvez cependant ignorer sans problème l’avertissement de dépréciation de `/Gm`, car il n’est pas traité en tant qu’erreur quand vous utilisez « Considérer les avertissements comme des erreurs » (`/WX`).

- Comme MSVC commence la mise en œuvre de fonctionnalités à partir du brouillon standard C++20 sous l’indicateur `/std:c++latest`, `/std:c++latest` est désormais incompatible avec `/clr` (toutes les saveurs), `/ZW`, et `/Gm`. Dans Visual Studio 2019, utilisez le mode `/std:c++17` ou `/std:c++14` lors de la compilation avec `/clr`, `/ZW` ou `/Gm` (consultez la liste à puces précédente).

- Les en-têtes précompilés ne sont plus générés par défaut pour les applications de bureau et console C++.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, sécurité, diagnostics et gestion des versions

Analyse améliorée avec `/Qspectre` afin de fournir une aide à l’atténuation des risques pour Spectre Variant 1 (CVE-2017-5753). Pour plus d’informations, consultez [Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Améliorations apportées à la bibliothèque standard C++

- Implémentation de nouvelles fonctionnalités de bibliothèque et de nouveaux correctifs d’exactitude C++17 et C++20. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2019](cpp-conformance-improvements.md).

- Le format clang a été appliqué aux en-têtes de la bibliothèque standard C++ pour une meilleure lisibilité.

- Étant donné que Visual Studio prend désormais en charge Uniquement mon code pour C++, la bibliothèque standard n’a plus besoin de fournir de mécanisme personnalisé pour `std::function` et `std::visit` pour obtenir le même effet. La suppression de ce mécanisme n’aura quasiment aucun effet visible par l’utilisateur. Une exception est que le compilateur ne produira plus de diagnostics indiquant les problèmes de ligne 15732480 ou 16707566 de \<type_traits > ou de \<variant>.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Améliorations de performances/débit dans le compilateur et la bibliothèque standard

- Améliorations du débit de la génération, notamment la gestion par l’éditeur de liens des E/S de fichier, et la durée de l’établissement des liens dans la création et la fusion des types PDB.

- Ajout de la prise en charge de base de la vectorisation SIMD OpenMP. Vous pouvez l’activer avec le nouveau commutateur de compilateur `-openmp:experimental`. Cette option permet la vectorisation potentielle des boucles annotées avec `#pragma omp simd`. La vectorisation n’est pas garantie, et les boucles annotées mais pas vectorisées génèrent un avertissement. Aucune clause SIMD n’est prise en charge ; elles sont ignorées et un avertissement est émis.

- Ajout d’un nouveau commutateur de ligne de commande d’incorporation (inlining) `-Ob3`, qui est une version plus agressive de `-Ob2`. `-O2` (optimiser le fichier binaire pour la vitesse) implique toujours `-Ob2` par défaut. Si vous trouvez que le compilateur n’incorpore pas de façon suffisamment agressive, envisagez de passer `-O2 -Ob3`.

- Pour prendre en charge la vectorisation manuelle des boucles avec des appels de fonctions de bibliothèque mathématique et certaines autres opérations telles que la division d’entiers, nous avons ajouté la prise en charge des fonctions intrinsèques SVML (Short Vector Math Library). Ces fonctions calculent les vecteurs équivalents 128 bits, 256 bits ou 512 bits. Pour obtenir les définitions des fonctions prises en charge, consultez le [Guide des intrinsèques Intel](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Optimisations nouvelles et améliorées :

  - Simplifications arithmétiques et de pliage de constante pour les expressions à l’aide d’intrinsèques de vecteur SIMD, pour les formes float et integer.

  - Analyse plus puissante pour extraire des informations de flux de contrôle (instructions if/else/switch) afin de supprimer les branches toujours prouvées comme étant true ou false.

  - Amélioration du déroulement de memset de façon à utiliser les instructions de vecteur SSE2.

  - Amélioration de la suppression des copies de struct/classes inutiles, en particulier pour les programmes C++ qui passent par valeur.

  - Amélioration de l’optimisation du code utilisant `memmove`, comme `std::copy` ou `std::vector` et une construction `std::string`.

- Optimisez la conception physique de la bibliothèque standard afin d’éviter de compiler des parties de la bibliothèque standard qui ne sont pas directement incluses. Cette modification réduit le temps de génération d’un fichier vide qui inclut uniquement \<vector> de moitié. En conséquence, vous devrez peut-être ajouter des directives `#include` pour les en-têtes qui précédemment étaient indirectement inclus. Par exemple, le code qui utilise `std::out_of_range` pourrait maintenant avoir à ajouter `#include <stdexcept>`. Le code qui utilise un opérateur d’insertion de flux doit maintenant ajouter `#include <ostream>`. L’avantage est que seule les unités de traduction qui utilisent réellement des composants \<stdexcept> ou \<ostream> payent le débit de coût pour les compiler.

- `if constexpr` a été appliqué à plusieurs endroits dans la bibliothèque standard pour un débit amélioré et une taille de code réduite dans les opérations de copie, dans les permutations comme l’inversion et la rotation et dans la bibliothèque d’algorithmes parallèles.

- La bibliothèque standard utilise désormais `if constexpr` en interne afin de réduire la compilation même en mode C++14.

- La détection de lien dynamique de runtime pour la bibliothèque d’algorithmes parallèles n’utilise plus une page entière pour stocker le tableau de pointeurs de fonction. Le marquage de cette mémoire en lecture seule n’est plus considéré comme pertinent pour des raisons de sécurité.

- `std::thread` du constructeur n’attend plus que le thread démarre, et n’insère plus autant de calques d’appels de fonction entre la bibliothèque C sous-jacente `_beginthreadex` et l’objet fourni pouvant être appelé. Précédemment `std::thread` mettait 6 fonctions entre `_beginthreadex` et l’objet fourni pouvant être appelé, ce nombre a été réduit à seulement 3 (dont 2 sont uniquement `std::invoke`). Ce changement résout également un bogue obscur de minutage qui bloquait le constructeur de `std::thread` si l’horloge du système avait été modifiée au moment précis où un `std::thread` était créé.

- Correction d’une régression des performances dans `std::hash` que nous avons introduit lors de l’implémentation `std::hash<std::filesystem::path>`.

- La bibliothèque standard utilise désormais dans plusieurs endroits, des destructeurs au lieu de blocs catch pour atteindre l’exactitude. Cette modification entraîne une meilleure interaction du débogueur : Les exceptions que vous levez via la bibliothèque standard dans les emplacements concernés apparaîtront désormais comme ayant été levés à partir de leur site de levée d’origine, plutôt que d’une nouvelle levée. Tous les blocs catch de bibliothèque standard n’ont pas été éliminées ; nous nous attendons à ce que le nombre de blocs catch soit réduit dans les versions ultérieures de MSVC.

- Un codegen non optimal dans `std::bitset` provoqué par une levée conditionnelle à l’intérieur d’une fonction noexcept a été résolu en factorisant le chemin d’accès levant.

- Les familles `std::list` et `std::unordered_*` utilisent des itérateurs de non débogage en interne dans plusieurs endroits.

- Plusieurs membres `std::list` ont été modifiés pour réutiliser les nœuds de la liste lorsque cela est possible au lieu de les libérer et de les redistribuer. Par exemple, dans le cas d’un `list<int>` qui possède déjà une taille de 3, un appel à `assign(4, 1729)` remplace maintenant les entiers dans les 3 premiers nœuds de la liste et alloue un nouveau nœud de liste avec la valeur 1 729.

- Tous les appels de la bibliothèque standard à `erase(begin(), end())` ont été remplacés par `clear()`.

- `std::vector` initialise et efface désormais les éléments plus efficacement dans certains cas.

- Améliorations apportées à `std::variant` pour le rendre plus adapté à l’optimiseur, ce qui entraîne la génération d’un meilleur code. L’incorporation (inlining) de code est désormais bien meilleure avec `std::visit`.

## <a name="c-ide"></a>IDE C++

### <a name="live-share-c-support"></a>Prise en charge de C++ par Live Share

[Live Share ](/visualstudio/liveshare/) prend désormais en charge C++, ce qui permet aux développeurs utilisant Visual Studio ou Visual Studio Code de collaborer en temps réel. Pour plus d’informations, consultez [Announcing Live Share for C++: Real-Time Sharing and Collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode pour C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

IntelliCode est une extension facultative qui exploite toutes ses données d’apprentissage et le contexte de votre code pour suggérer les éléments de code que vous êtes le plus susceptible d’utiliser en haut de votre liste de complétion. Il peut souvent vous éviter de faire défiler la liste vers le bas. Pour C++, IntelliCode est le plus performant quand vous utilisez des bibliothèques courantes comme la bibliothèque standard. Il est disponible comme composant de charge de travail dans le programme d’installation. Pour plus d’informations, consultez [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

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

### <a name="quickinfo-improvements"></a>Améliorations de Info express

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

L’info-bulle Info express respecte désormais la colorisation sémantique de votre éditeur. Il dispose également d’un nouveau lien de **recherche en ligne** qui recherche de la documentation en ligne pour en savoir plus sur la construction de code survolé. En ce qui concerne le code souligné en rouge, ce lien fourni par Info express effectue des recherches d’erreurs en ligne. De cette façon, vous n’avez pas besoin de retaper le message dans votre navigateur. Pour en savoir plus, consultez la section relative aux [améliorations de Info express dans Visual Studio 2019 : Colorisation et recherche en ligne](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>IntelliCode disponible dans la charge de travail C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

IntelliCode est désormais fourni en tant que composant facultatif dans la charge de travail **Développement Desktop en C++** . Pour en savoir plus, voir [IntelliCode C++ amélioré désormais fourni avec Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Prise en charge de CMake

- Prise en charge de CMake 3.14

- Visual Studio peut maintenant ouvrir les caches CMake existants générés par des outils externes, comme CMakeGUI, des systèmes de génération de métadonnées personnalisés ou des scripts de génération appelant eux-mêmes cmake.exe.

- Amélioration des performances d’IntelliSense.

- Un nouvel éditeur de paramètres fournit une alternative à la modification manuelle de CMakeSettings.json et offre une similarité avec CMakeGUI.

- Visual Studio vous aide à démarrer votre développement en C++ avec CMake sur Linux en détectant si vous avez une version compatible de CMake sur votre ordinateur Linux. Si ce n’est pas le cas, il propose de l’installer pour vous.

- Les paramètres incompatibles dans CMakeSettings, comme les incompatibilités d’architectures ou les paramètres de générateur CMake incompatibles, sont marqués par des tildes dans l’éditeur JSON et par des erreurs dans la liste d’erreurs.

- La chaîne d’outils vcpkg est automatiquement détectée et activée pour les projets CMake qui sont ouverts dans l’IDE, une fois que `vcpkg integrate install` a été exécuté. Ce comportement peut être désactivé en spécifiant un fichier de chaîne d’outils vide dans cmakesettings.

- Les projets CMake autorisent maintenant le débogage Uniquement mon code par défaut.

- Les avertissements d’analyse statique peuvent désormais être traités en arrière-plan et affichés dans l’éditeur pour les projets CMake.

- Messages de début et de fin de génération et de configuration plus clairs pour les projets CMake, et prise en charge de l’interface utilisateur de progression de la génération de Visual Studio. De plus, il existe désormais un paramètre de niveau de détail CMake dans **Outils > Options** pour personnaliser le niveau de détail des messages de génération et de configuration CMake dans la fenêtre Sortie.

- Le paramètre `cmakeToolchain` est désormais pris en charge dans CMakeSettings.json pour spécifier des chaînes d’outils sans modifier manuellement la ligne de commande CMake.

- Nouveau raccourci pour le menu **Tout générer** (**Ctrl+Maj+B**).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

- Prise en charge intégrée pour la modification, la génération et le débogage de projets CMake avec Clang/LLVM. Pour en savoir plus, voir [Prise en charge Clang/LLVM dans Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux et le sous-système Windows pour Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

- Prise en charge de [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) dans les projets d’inter-plateformes Linux et CMake. Pour en savoir plus, voir [AddressSanitizer (ASan) pour la charge de travail Linux dans Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Prise en charge intégrée de Visual Studio pour l’utilisation de C++ avec le sous-système Windows pour Linux (WSL). Pour en savoir plus, voir [ C++ avec Visual Studio 2019 et le sous-système Windows pour Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>Intégration d’IncrediBuild

IncrediBuild est désormais fourni en tant que composant facultatif dans la charge de travail **Développement Desktop en C++** . Le moniteur de build IncrediBuild est entièrement intégré à l’IDE de Visual Studio. Pour en savoir plus, voir [Visualiser votre build avec le moniteur de build d’IncrediBuild et Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

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

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

- Nouveaux correctifs rapides pour des vérifications de variables non initialisées. Pour en savoir plus, voir [Nouveaux correctifs rapides d’analyse de code pour la mémoire non initialisée (C6001) et les avertissements d’utilisation avant init (C26494)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Test unitaire

Le modèle de projet de test C++ managé n’est plus disponible. Vous pouvez continuer à utiliser le framework de test C++ managé dans vos projets existants. Pour les nouveaux tests unitaires, utilisez un des frameworks de test natifs pour lesquels Visual Studio fournit des modèles (MSTest, Google Test) ou le modèle de projet de test C# managé.

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 comprend un grand nombre de mises à jour et de correctifs de l’environnement C++. Nous avons résolu plus de 250 bogues et problèmes signalés dans le compilateur et les outils, beaucoup d’entre eux ayant été soumis par des clients via les options [Signaler un problème et Faire une suggestion](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) sous **Envoyer des commentaires**. Merci d’avoir signalé ces bogues. Pour plus d’informations sur l’ensemble des nouveautés de Visual Studio, visitez [Nouveautés de Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2019, consultez [Nouveautés de C++ dans Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2015 et versions antérieures, consultez [Nouveautés de Visual C++ entre 2003 et 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>compilateur C++

### <a name="c-conformance-improvements"></a>Améliorations de la conformité de C++

Dans cette version, nous avons mis à jour le compilateur C++ et la bibliothèque standard avec prise en charge améliorée des fonctionnalités C++11 et C++14, et nous avons ajouté la prise en charge préliminaire de certaines fonctionnalités prévues pour la version C++17 standard. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Le compilateur prend en charge environ 75 % des fonctionnalités nouvelles dans C++17, notamment les liaisons structurées, les expressions lambda `constexpr`, `if constexpr`, les variables inline, les expressions fold, et l’ajout de `noexcept` au système des types. Ces fonctionnalités sont disponibles sous l’option **/std:c++17**. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

L’ensemble d’outils du compilateur MSVC dans Visual Studio version 15.7 est désormais conforme à la norme C++. Pour plus d’informations, consultez [Announcing : MSVC Conforms to the C++ Standard](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) et [Conformité du langage Microsoft C++](../visual-cpp-language-conformance.md).

### <a name="new-compiler-options"></a>Nouvelles options du compilateur

- [/permissive-](../build/reference/permissive-standards-conformance.md) : permet d’activer toutes les options de compilateur de conformité aux normes strictes et de désactiver la plupart des extensions du compilateur spécifiques à Microsoft (mais par exemple pas `__declspec(dllimport)`). Cette option est activée par défaut dans Visual Studio 2017 version 15.5.  Le mode de conformité **/permissive-** inclut une prise en charge de la recherche de noms en deux phases. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio](cpp-conformance-improvements.md).

- [/diagnostics](../build/reference/diagnostics-compiler-diagnostic-options.md) : permet l’affichage du numéro de ligne, du numéro de ligne et de colonne, ou du numéro de ligne et de colonne avec un signe insertion sous la ligne de code où l’erreur ou l’avertissement de diagnostic a été trouvé.

- [/debug:fastlink](../build/reference/debug-generate-debug-info.md) : permet une édition de liens incrémentielle jusqu’à 30 % plus rapide (par rapport à Visual Studio 2015) en ne copiant pas toutes les informations de débogage dans le fichier PDB. À la place, le fichier PDB pointe vers les informations de débogage pour les fichiers objets et bibliothèques utilisés pour créer l’exécutable. Consultez [Faster C++ build cycle in VS "15" with /Debug:fastlink](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) et [Recommendations to speed C++ builds in Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Visual Studio 2017 permet l’utilisation de [/sdl](../build/reference/sdl-enable-additional-security-checks.md) avec [/await](../build/reference/await-enable-coroutine-support.md). Nous avons supprimé la limitation de [/RTC](../build/reference/rtc-run-time-error-checks.md) avec les coroutines.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- [/std:c++14 et /std:c++latest](../build/reference/std-specify-language-standard-version.md) : ces options du compilateur vous permettent de choisir des versions spécifiques du langage de programmation ISO C++ dans un projet. La plupart des nouvelles fonctionnalités standard préliminaires sont protégées par l’option **/std:c++latest**.

- [/std:c++17](../build/reference/std-specify-language-standard-version.md) active l’ensemble des fonctionnalités C++17 implémentées par le compilateur. Cette option désactive la prise en charge par le compilateur et la bibliothèque standard des fonctionnalités modifiées ou nouvelles dans les versions de Working Draft et les mises à jour des défauts de C++ Standard postérieures à C++17. Pour activer ces fonctionnalités, utilisez **/std:c ++latest**.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, sécurité, diagnostics et gestion des versions

Cette version apporte plusieurs améliorations à l’optimisation, à la génération de code, à la gestion de version de l’ensemble d’outils et aux diagnostics. Les améliorations notables sont les suivantes :

- Amélioration de la génération du code des boucles : prise en charge de la vectorisation automatique de la division d’entiers constants, optimisation de l’identification des modèles de memset.
- Amélioration de la sécurité du code : amélioration de la production du diagnostic de dépassement de mémoire tampon du compilateur ; [/guard:cf](../build/reference/guard-enable-control-flow-guard.md) protège désormais les instructions switch qui génèrent des tableaux de saut.
- Gestion des versions : La valeur de la macro de préprocesseur intégrée **\_MSC\_VER** est désormais mise à jour de façon monolithique à chaque mise à jour de l’ensemble d’outils Visual C++. Pour plus d’informations, consultez [Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nouvelle disposition de l’ensemble d’outils : le compilateur et les outils de génération connexes ont un nouvel emplacement et une structure de répertoire sur votre ordinateur de développement. La nouvelle disposition permet des installations côte à côte de plusieurs versions du compilateur. Pour plus d’informations, consultez [Compiler Tools Layout in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Amélioration des diagnostics : La fenêtre Sortie affiche maintenant la colonne où une erreur se produit. Pour plus d’informations, consultez [C++ compiler diagnostics improvements in VS "15" Preview 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Lors de l’utilisation de coroutines, le mot clé expérimental **yield** (disponible sous l’option **/await**) a été supprimé. Votre code doit être mis à jour pour utiliser `co_yield` à la place. Pour plus d’informations, consultez [Changement du mot clé `yield` en `co_yield` dans Visual Studio 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

Améliorations supplémentaires apportées aux diagnostics dans le compilateur. Pour plus d'informations, consultez [Diagnostic Improvements in Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Les performances d’exécution de Visual C++ continuent de s’améliorer grâce à une meilleure qualité du code généré. Maintenant, vous pouvez simplement recompiler votre code pour rendre votre application plus rapide. Certaines optimisations du compilateur sont nouvelles, comme la vectorisation des stockages de scalaires conditionnels, la combinaison des appels `sin(x)` et `cos(x)` en un nouveau `sincos(x)`, et la suppression des instructions redondantes dans l’optimiseur SSA. Les autres optimisations du compilateur concernent des améliorations qui ont été apportées à des fonctionnalités existantes, par exemple, les heuristiques du vectoriseur pour les expressions conditionnelles, les boucles optimisées et la génération de code avec des valeurs float min/max. L’éditeur de liens a une nouvelle implémentation de **/OPT:ICF** plus rapide, qui peut accélérer l’édition de liens de jusqu’à 9 %. D’autres correctifs ont été apportés pour améliorer les performances de la liaison incrémentielle. Pour plus d’informations, consultez [/OPT (Optimisations)](../build/reference/opt-optimizations.md) et [/INCREMENTAL (Lier par incrément)](../build/reference/incremental-link-incrementally.md).

Le compilateur Microsoft C++ prend en charge AVX-512 d’Intel, y compris les instructions Vector Length qui apportent de nouvelles fonctions dans AVX-512 pour les registres de largeur 128 et 256 bits.

Vous pouvez utiliser l’option [/Zc:noexceptTypes-](../build/reference/zc-noexcepttypes.md) pour rétablir la version C++14 de `noexcept` si vous utilisez généralement le mode C++17. Cette option vous permet de mettre à jour votre code source pour le rendre conforme à C++17 sans pour autant avoir à réécrire tout votre code `throw()`. Pour plus d’informations, consultez [Suppression des spécifications d’exceptions dynamiques et noexcept](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

- Le nouveau commutateur de compilateur [/Qspectre](../build/reference/qspectre.md) permet d’atténuer les attaques par canal auxiliaire à exécution spéculative. Pour plus d’informations, consultez [Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nouvel avertissement de diagnostic pour l’atténuation Spectre. Pour plus d’informations, consultez [Spectre diagnostic in Visual Studio 2017 Version 15.7 Preview 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Une nouvelle valeur pour /Zc, **/Zc:__cplusplus**, permet de créer des rapports corrects sur la prise en charge de la norme C++. Par exemple, quand le commutateur est défini et que le compilateur est en mode /std:c++17, la valeur affiche **201703L**. Pour plus d’informations, consultez [MSVC now correctly reports __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>Bibliothèque C++ Standard

### <a name="correctness-improvements"></a>Améliorations de l’exactitude

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (version 15.0)

- Améliorations mineures des diagnostics `basic_string` `_ITERATOR_DEBUG_LEVEL != 0`. Le déplacement d’une vérification IDL dans le système des chaînes signale désormais le comportement spécifique qui a provoqué le déplacement. Par exemple, au lieu de « itérateur de chaîne non déréférençable » vous recevez « impossible de déréférencer l’itérateur de chaîne car il est hors limites (par exemple un itérateur de fin) ».
- Correction de l’opérateur d’affectation de déplacement `std::promise`, qui pouvait provoquer le blocage définitif du code.
- Correction des erreurs du compilateur avec la conversion implicite de `atomic<T*>` en `T*`.
- `pointer_traits<Ptr>` détecte désormais `Ptr::rebind<U>` correctement.
- Correction d’un qualificateur `const` manquant dans l’opérateur de soustraction `move_iterator`.
- Correction d’un codegen incorrect sans déclenchement d’erreur pour les allocateurs avec état définis par l’utilisateur nécessitant `propagate_on_container_copy_assignment` et `propagate_on_container_move_assignment`.
- `atomic<T>` tolère désormais `operator&()` surchargé.
- Légère amélioration des diagnostics du compilateur pour les appels de `bind()` incorrects.

Pour obtenir une liste complète des améliorations de la bibliothèque standard dans Visual Studio 2017 RTM, consultez l’entrée de blog de l’équipe C++ [Standard Library Fixes In VS 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Les conteneurs de la bibliothèque standard limitent désormais leur `max_size()` à `numeric_limits<difference_type>::max()`, au lieu du `max()` de `size_type`. Ce changement garantit que le résultat de `distance()` sur les itérateurs de ce conteneur peut être représenté dans le type de retour de `distance()`.
- Correction de la spécialisation manquante `auto_ptr<void>`.
- Les algorithmes `for_each_n()`, `generate_n()` et `search_n()` échouaient précédemment lors de la compilation si l’argument de longueur n’était pas un type intégral ; ils tentent désormais de convertir les longueurs non intégrales en `difference_type` des itérateurs.
- `normal_distribution<float>` n’émet plus d’avertissements dans la bibliothèque standard à propos des conversions restrictives de double en float.
- Correction de certaines opérations `basic_string` qui utilisaient `npos` au lieu de `max_size()` lors de la vérification du dépassement de la taille maximale.
- `condition_variable::wait_for(lock, relative_time, predicate)` attendait pendant toute la durée relative dans le cas d’une fausse sortie de veille. Il attend désormais pendant un seul intervalle du temps relatif.
- `future::get()` invalide désormais `future`, conformément au standard.
- `iterator_traits<void *>` constituait une erreur matérielle, car il tentait de former `void&` ; il devient désormais une structure vide sans erreur pour permettre l’utilisation de `iterator_traits` dans les conditions SFINAE « is iterator ».
- Certains avertissements signalés par Clang **-Wsystem-headers** ont été corrigés.
- Le problème « la spécification d’exception dans la déclaration ne correspond pas à la déclaration précédente » signalé par Clang **-Wmicrosoft-exception-spec** a également été corrigé.
- Correction également des avertissements d’ordre mem-initializer-list signalés par Clang et C1XX.
- Les conteneurs non ordonnés ne permutaient pas leurs fonctions de hachage ou prédicats lorsque les conteneurs eux-mêmes étaient permutés. C’est le cas désormais.
- Plusieurs opérations de permutation de conteneur sont désormais marquées `noexcept` (car notre bibliothèque standard ne prévoit jamais de lever une exception lors de la détection de la condition de comportement non définie non-`propagate_on_container_swap` non-equal-allocator).
- De nombreuses opérations `vector<bool>` sont désormais marquées `noexcept`.
- La bibliothèque standard applique désormais un `value_type` d’allocateur correspondant (en mode C++17) avec une hachure d’échappement de refus.
- Correction de certaines conditions où self-range-insert dans `basic_string` désorganisait le contenu des chaînes. (Remarque : self-range-insert dans vectors est toujours interdit par la norme.)
- `basic_string::shrink_to_fit()` n’est plus affecté par le `propagate_on_container_swap` de l’allocateur.
- `std::decay` gère désormais des types de fonction abominable, c’est-à-dire des types de fonctions qualifiés par cv et/ou qualifiés par ref.
- Modification des directives include pour utiliser la casse appropriée et des barres obliques, et améliorer la portabilité.
- Correction de l’avertissement C4061 « L’énumérateur *énumérateur* dans le switch de l’énumération *énumération* n’est pas géré explicitement par une étiquette case ». Cet avertissement est désactivé par défaut et a été résolu en tant qu’exception à la stratégie générale de la bibliothèque standard pour les avertissements. (La bibliothèque standard est sans erreur **/W4**, mais n’essaie pas d’être sans erreur **/Wall**. Plusieurs avertissements désactivés par défaut sont très bruyants et ne sont pas destinés à être utilisés de manière régulière.)
- Amélioration des vérifications du débogage de `std::list`. Les itérateurs de liste vérifient désormais `operator->()`, et `list::unique()` marque maintenant les itérateurs comme non validés.
- Correction de la métaprogrammation de uses-allocator dans `tuple`.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- `std::partition` appelle maintenant le prédicat N fois au lieu de N + 1 fois, comme exigé par le standard.
- Les tentatives pour éviter les statiques magic dans la version 15.3 ont été résolues dans la version 15.5.
- `std::atomic<T>` ne nécessite plus que `T` soit constructible par défaut.
- Les algorithmes de segment de mémoire avec du temps logarithmique n’effectuent plus d’assertion de temps linéaire sur le fait que l’entrée est un segment de mémoire quand le débogage de l’itérateur est activé.
- `__declspec(allocator)` est maintenant protégé pour C1XX uniquement, afin d’éviter la génération d’avertissements par Clang qui ne comprend pas ce declspec.
- `basic_string::npos` est maintenant disponible comme constante au moment de la compilation.
- `std::allocator` en mode C++17 gère à présent correctement l’allocation de types suralignés, c’est-à-dire des types dont l’alignement est supérieur à `max_align_t`, sauf s’il est désactivé par **/Zc:alignedNew-** .  Par exemple, des vecteurs d’objets avec un alignement de 16 ou de 32 octets sont désormais correctement alignés pour les instructions SSE et AVX.

### <a name="conformance-improvements"></a>Améliorations de la conformité

- Nous avons ajouté \<any\>, \<string_view\>, `apply()`, `make_from_tuple()`.
- Ajout de \<optional\>, \<variant\>, `shared_ptr::weak_type` et \<cstdalign\>.
- Activation de `constexpr` de C++14 dans `min(initializer_list)`, `max(initializer_list)`, et `minmax(initializer_list)`, et `min_element()`, `max_element()` et `minmax_element()`.

Pour plus d'informations, consultez [Visual C++ Language Conformance](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Plusieurs autres fonctionnalités C++17 ont été implémentées. Pour plus d'informations, consultez [Visual C++ Language Conformance](cpp-conformance-improvements.md#improvements_153).
- Implémentation de P0602R0 « variant and optional should propagate copy/move triviality ».
- La bibliothèque standard tolère désormais officiellement la désactivation du RTTI dynamique via l’option [/GR-](../build/reference/gr-enable-run-time-type-information.md). `dynamic_pointer_cast()` et `rethrow_if_nested()` nécessitent tous deux par nature `dynamic_cast`, de sorte que la bibliothèque standard les marque désormais comme `=delete` sous **/GR-** .
- Même quand le RTTI dynamique a été désactivé via **/GR-** , le « RTTI statique » (sous la forme de `typeid(SomeType)`) est toujours disponible et sert de base à plusieurs composants de la bibliothèque standard. La bibliothèque standard prend désormais aussi en charge la désactivation de cette fonctionnalité, via **/D\_HAS\_STATIC\_RTTI=0**. Cet indicateur désactive également `std::any`, les fonctions membres `target()` et `target_type()` de `std::function`, et la fonction membre friend `get_deleter()` de `std::shared_ptr` et `std::weak_ptr`.
- La bibliothèque standard utilise désormais `constexpr` de C++14 de façon inconditionnelle, au lieu de macros définies de façon conditionnelle.
- La bibliothèque standard utilise désormais les modèles d’alias en interne.
- La bibliothèque standard utilise désormais `nullptr` en interne, au lieu de `nullptr_t{}`. (L’utilisation interne de NULL a été supprimée. L’utilisation interne de 0-as-null est en cours de nettoyage progressif.)
- La bibliothèque standard utilise désormais `std::move()` en interne, au lieu d’une mauvaise utilisation de `std::forward()` du point de vue du style.
- `static_assert(false, "message")` a été changé en `#error message`. Cette modification permet d’améliorer les diagnostics du compilateur, car `#error` arrête immédiatement la compilation.
- La bibliothèque standard ne marque plus les fonctions en tant que `__declspec(dllimport)`. La technologie de l’éditeur de liens moderne ne requiert plus cela.
- Extraction de SFINAE dans des arguments de modèle par défaut, ce qui réduit l’encombrement par rapport aux types de retour et aux types d’arguments de fonction.
- Les vérifications de débogage dans \<random\> utilisent désormais le mécanisme habituel de la bibliothèque standard, au lieu de la fonction interne `_Rng_abort()` qui appelait `fputs()` sur **stderr**. L’implémentation de cette fonction est conservée pour la compatibilité binaire, mais a été supprimée dans la prochaine version non compatible binaire de la bibliothèque standard.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- Plusieurs fonctionnalités de la bibliothèque standard ont été ajoutées, dépréciées ou supprimées conformément à la norme C++17. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio](cpp-conformance-improvements.md#improvements_155).
- Une prise en charge expérimentale est fournie pour les algorithmes parallèles suivants :
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- Les signatures pour les algorithmes parallèles suivants ont été ajoutées, mais sans être parallélisées. Le profilage n’a pas montré d’avantages à paralléliser les algorithmes qui ne font que déplacer ou permuter des éléments :
  - `copy`
  - `copy_n`
  - `fill`
  - `fill_n`
  - `move`
  - `reverse`
  - `reverse_copy`
  - `rotate`
  - `rotate_copy`
  - `swap_ranges`

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 version 15.6

- \<memory_resource>
- Library Fundamentals V1
- Suppression de l’affectation de `polymorphic_allocator`
- Amélioration de la déduction d’arguments de modèle de classe

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

- La prise en charge des algorithmes parallèles n’est plus expérimentale
- Une nouvelle implémentation de \<filesystem>
- Conversions de chaînes élémentaires (état partiel)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- Prévention des dégradations inutiles
- Fonctions mathématiques spéciales
- `constexpr char_traits`
- Guides de déduction pour la bibliothèque standard

Pour plus d'informations, consultez [Visual C++ Language Conformance](../visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Correctifs de performance et de débit

- Modification des surcharges `basic_string::find(char)` pour appeler `traits::find` une seule fois. Auparavant, cela était implémenté comme une recherche de chaîne générale d’une chaîne de longueur 1.
- `basic_string::operator==` vérifie désormais la taille de la chaîne avant de comparer le contenu des chaînes.
- Suppression du couplage des contrôles dans `basic_string`, qui rendait difficile l’analyse par l’optimiseur du compilateur. Pour toutes les chaînes courtes, l’appel de `reserve` a toujours un coût non nul pour ne rien faire.
- `std::vector` a été remanié pour un fonctionnement plus correct et de meilleures performances : les alias utilisés pour les opérations d’insertion et d’emplacement sont désormais gérés correctement conformément au standard, la garantie d’exception forte est désormais fournie conformément au standard via `move_if_noexcept()` et d’autres logiques, et insertion/emplacement réalise moins d’opérations sur les éléments.
- La bibliothèque C++ standard évite désormais de déréférencer les pointeurs fantômes Null.
- Amélioration des performances de `weak_ptr::lock()`.
- Pour augmenter le débit du compilateur, les en-têtes de la bibliothèque C++ standard évitent désormais d’inclure des déclarations de fonctions intrinsèques de compilateur inutiles.
- Amélioration d’un facteur supérieur à 3 des performances des constructeurs de déplacement `std::string` et `std::wstring`.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Interactions de contournement avec `noexcept` qui empêchaient l’incorporation de l’implémentation de `std::atomic` dans des fonctions utilisant la gestion des exceptions structurées (SEH, Structured Exception Handling).
- Modification de la fonction `_Deallocate()` interne de la bibliothèque standard pour l’optimiser en un code plus petit, ce qui lui permet d’être incorporée dans plus d’emplacements.
- Modification de `std::try_lock()` pour l’utilisation de l’expansion de package à la place de la récurrence.
- Amélioration de l’algorithme de prévention de blocage `std::lock()` pour l’utilisation d’opérations `lock()` au lieu d’effectuer une rotation sur `try_lock()` pour tous les verrous.
- Activation de l’optimisation de la valeur de retour nommée dans `system_category::message()`.
- `conjunction` et `disjunction` instancient désormais des types N + 1, au lieu de types 2N + 2.
- `std::function` n’instancie plus le mécanisme de prise en charge des allocateurs pour chaque type-erased pouvant être appelé, améliorant le débit et réduisant la taille des fichiers .obj dans les programmes qui passent beaucoup d’expressions lambda distinctes à `std::function`.
- `allocator_traits<std::allocator>` contient des opérations `std::allocator` incorporées manuellement, ce qui réduit la taille du code dans le code qui interagit avec `std::allocator` via `allocator_traits` uniquement (autrement dit, dans la plupart du code).
- L’interface d’allocateur minimale C++11 est désormais gérée directement par l’allocateur appelant de la bibliothèque standard `allocator_traits`, au lieu d’inclure l’allocateur dans une classe interne `_Wrap_alloc`. Ce changement réduit la taille du code généré pour la prise en charge de l’allocateur, améliore la capacité de l’optimiseur à traiter les conteneurs de la bibliothèque standard dans certains cas, et fournit une meilleure expérience de débogage (car vous voyez désormais votre type d’allocateur, au lieu de `_Wrap_alloc<your_allocator_type>` dans le débogueur).
- Suppression de la métaprogrammation pour une `allocator::reference` personnalisée, que les allocateurs ne sont pas autorisés à personnaliser. (Les allocateurs peuvent demander aux conteneurs d’utiliser des pointeurs fantaisistes mais pas des références fantaisistes.)
- Le serveur frontal du compilateur a appris à désencapsuler les itérateurs de débogage dans des opérations for-loops basées sur plage, pour améliorer les performances des versions de débogage.
- Le chemin shrink interne de `basic_string` pour `shrink_to_fit()` et `reserve()` n’est plus dans le chemin des opérations de réallocation, réduisant la taille du code pour tous les membres en mutation.
- Le chemin grow interne de `basic_string` n’est plus dans le chemin de `shrink_to_fit()`.
- Les opérations de mutation de `basic_string` sont désormais incluses dans les fonctions de chemin rapide de non-allocation et de chemin lent d’allocation, rendant plus probable l’incorporation du cas no-reallocate fréquent dans les appelants.
- Les opérations de mutation de `basic_string` construisent désormais des mémoires tampons réallouées dans l’état souhaité au lieu de les redimensionner sur place. Par exemple, l’insertion au début d’une chaîne déplace maintenant le contenu après l’insertion une seule fois (vers le bas ou vers la mémoire tampon qui vient d’être allouée), au lieu de deux fois dans le cas de la réaffectation (vers la mémoire tampon qui vient d’être allouée, puis vers le bas).
- Les opérations appelant la bibliothèque standard C dans \<string\> mettent maintenant en cache l’adresse de `errno` pour supprimer l’interaction répétée avec TLS.
- Simplification de l’implémentation de `is_pointer`.
- Fin de la modification de Expression SFINAE basée sur une fonction en une valeur basée sur `struct` et `void_t`.
- Désormais, les algorithmes de la bibliothèque standard évitent la post-incrémentation des itérateurs.
- Correction des avertissements de troncation lors de l’utilisation d’allocateurs 32 bits sur les systèmes 64 bits.
- L’affectation de déplacement `std::vector` est désormais plus efficace dans le cas non-POCMA non-equal-allocator grâce à la réutilisation du tampon quand c’est possible.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- `basic_string<char16_t>` implique désormais le même `memcmp`, le même `memcpy` et des optimisations similaires impliquant `basic_string<wchar_t>`.
- Une limitation de l’optimiseur a été corrigée. Elle empêchait l’exposition inline des pointeurs de fonctions par le travail « éviter de copier les fonctions » dans Visual Studio 2015 Update 3. Les performances de `lower_bound(iter, iter, function pointer)` se sont donc améliorées.
- Le travail supplémentaire de vérification de l’ordre des entrées `includes`, `set_difference`, `set_symmetric_difference` et `set_union` pour le débogage des itérateurs a été réduit en sortant les itérateurs du wrapper avant de vérifier l’ordre.
- `std::inplace_merge` ignore maintenant les éléments qui sont déjà en position.
- La construction de `std::random_device` n’effectue plus la construction suivie de la destruction de `std::string`.
- `std::equal` et `std::partition` avaient une passe d’optimisation des enchaînements de sauts (jump-threading) qui évitait une comparaison des itérateurs.
- Quand `std::reverse` reçoit des pointeurs vers un `T` copiable simplement, il réalise désormais une répartition vers une implémentation vectorisée manuscrite.
- `std::fill`, `std::equal` et `std::lexicographical_compare` répartissent correctement vers `memset` et `memcmp` pour `std::byte` et `gsl::byte` (et pour d’autres énumérations et classes d’énumérations de caractères). Comme `std::copy` effectue la répartition en utilisant `is_trivially_copyable`, il ne nécessitait aucune modification.
- La bibliothèque standard ne contient plus de destructeurs d’accolades vides dont le seul comportement était de rendre les types non destructibles de façon simple.

## <a name="other-libraries"></a>Autres bibliothèques

### <a name="open-source-library-support"></a>Prise en charge de la bibliothèque open source

**Vcpkg** est un outil en ligne de commande open source, qui simplifie grandement le processus d’acquisition et de création des bibliothèques statiques C++ open source et des DLL dans Visual Studio. Pour plus d’informations, consultez [vcpkg : Gestionnaire de package pour C++](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>SDK C++ REST 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Le SDK C++ REST, une API web multiplateforme pour C++, a été mis à jour vers la version 2.9.0. Pour plus d’informations, consultez [CppRestSDK 2.9.0 is available on GitHub](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- Un autre ensemble de corrections de la conformité de la recherche de noms
- Les constructeurs de déplacement et les opérateurs d’assignation de déplacement existants sont désormais correctement marqués comme ne levant pas d’exceptions
- Annulation de la suppression de l’avertissement valide C4640 sur l’initialisation sécurisée de thread des statiques locales dans atlstr.h
- L’initialisation sécurisée de thread des statiques locales était automatiquement désactivée dans le jeu d’outils XP avec utilisation d’ATL ET construction d’une DLL, mais ce n’est pas le cas actuellement. Vous pouvez ajouter **/Zc:threadSafeInit-** dans les paramètres de votre projet si vous voulez que l’initialisation sécurisée de thread soit désactivée.

### <a name="visual-c-runtime"></a>Runtime Visual C++

- Nouvel en-tête « cfguard.h » pour les symboles de protection de flux de contrôle.

## <a name="c-ide"></a>IDE C++

- Les performances des modifications de configuration sont désormais meilleures pour les projets natifs C++ et bien meilleures pour les projets C++/CLI. Quand une configuration de solution est activée pour la première fois, elle est désormais plus rapide et toutes les activations suivantes de cette configuration de solution sont presque instantanées.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Plusieurs Assistants de projet et de code ont été réécrits pour refléter le style particulier des boîtes de dialogue.
- **Ajouter une classe** lance désormais l’Assistant Ajouter une classe directement. Tous les autres éléments qui se trouvaient déjà ici sont maintenant disponibles sous **Ajouter > Nouvel élément**.
- Les projets Win32 se trouvent désormais sous la catégorie **Windows Desktop** dans la boîte de dialogue **Nouveau projet**.
- Les modèles **Console Windows** et **Application de poste de travail** créent à présent les projets sans afficher d’Assistant. Il existe un nouvel **Assistant Windows Desktop** sous la même catégorie, qui affiche les mêmes options que l’ancien **Assistant Console Win32**.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Plusieurs opérations C++ qui utilisent le moteur IntelliSense pour la refactorisation et la navigation dans le code s’exécutent beaucoup plus rapidement. Les valeurs suivantes sont basées sur la solution Visual Studio Chromium avec 3 500 projets :

|||
|-|-|
|Fonctionnalité|Amélioration des performances|
|Renommer|x 5,3|
|Changer la signature |x 4,5|
|Rechercher toutes les références|x 4,7|

C++ prend maintenant en charge la fonctionnalité **Atteindre la définition** avec Ctrl+clic, ce qui permet un accès rapide aux définitions à l’aide de la souris. Le visualiseur de structure du pack Productivity Power Tools est également inclus dans le produit par défaut.

## <a name="intellisense"></a>IntelliSense

- Le nouveau moteur de base de données SQLite est désormais celui utilisé par défaut. Ceci permet d’accélérer les opérations de base de données, comme **Atteindre la définition** ou **Rechercher toutes les références**, et d’améliorer considérablement le temps d’analyse de la solution initiale. Le paramètre a été déplacé dans **Outils > Options > Éditeur de texte > C/C++ > Avancé** (il se trouvait auparavant sous ...C/C++ | Expérimental).

- Nous avons amélioré les performances d’IntelliSense dans les projets et fichiers qui n’utilisent pas d’en-têtes précompilés : un en-tête précompilé automatique est créé pour les en-têtes du fichier en cours.

- Nous avons ajouté une fonctionnalité de filtrage des erreurs et une aide pour les erreurs IntelliSense figurant dans la liste d’erreurs. Le fait de cliquer sur la colonne d’erreur permet maintenant un filtrage. De plus, en cliquant sur une erreur spécifique ou sur F1, une recherche en ligne est lancée sur le message d’erreur concerné.

  ![Liste d’erreurs](media/ErrorList1.png "Liste d’erreurs")

  ![Liste d’erreurs filtrée](media/ErrorList2.png "Liste d’erreurs filtrée")

- Ajout de la possibilité de filtrer les éléments de la liste des membres par type.

  ![Filtrage de la liste des membres](media/mlfiltering.png "Filtrage de la liste des membres")

- Ajout d’une nouvelle fonctionnalité IntelliSense prédictive expérimentale qui fournit un filtrage en fonction du contexte de ce qui apparaît dans la liste des membres. Pour plus d’informations, consultez [C++ IntelliSense Improvements - Predictive IntelliSense & Filtering](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- **Rechercher toutes les références** (Maj+F12) vous aide maintenant à naviguer facilement, même dans des codes base complexes. Elle offre des options avancées de regroupement, de filtrage, de tri, de recherche dans les résultats et (pour certains langages) la colorisation, ce qui vous permet d’avoir une vision claire de vos références. Pour C++, la nouvelle interface utilisateur inclut des informations indiquant si nous lisons ou si nous écrivons dans une variable.
- La fonctionnalité IntelliSense Point par flèche a été changée de « expérimentale » en « avancée » et elle est maintenant activée par défaut. Les fonctionnalités de l’éditeur **Développer les étendues** et **Développer la priorité** ont également été passées de « expérimentales » en « avancées ».
- Les fonctionnalités de refactorisation expérimentales **Modifier la signature** et **Extraire la fonction** sont désormais disponibles par défaut.
- Ajout de la fonctionnalité expérimentale « Chargement accéléré des projets » pour les projets C++. La prochaine fois que vous ouvrirez un projet C++, celui-ci sera chargé plus rapidement, et la fois suivante *beaucoup* plus rapidement.
- Certaines de ces fonctionnalités sont communes à d’autres langages, et certaines sont spécifiques à C++. Pour plus d’informations sur ces nouvelles fonctionnalités, consultez [Announcing Visual Studio "15" Preview 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

- Ajout de la prise en charge de ClangFormat. Pour plus d’informations, consultez [ClangFormat Support in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projets non MSBuild avec Ouvrir le dossier

Visual Studio 2017 introduit la fonctionnalité **Ouvrir le dossier**, qui vous permet d’effectuer des opérations de codage, de génération et de débogage dans un dossier contenant le code source, sans avoir à créer des solutions ni des projets. Il est maintenant beaucoup plus simple de bien démarrer avec Visual Studio, même si votre projet n’est pas un projet MSBuild. Avec **Ouvrir le dossier**, vous pouvez accéder aux puissantes fonctionnalités de compréhension du code, de modification, de génération et de débogage que Visual Studio fournit déjà pour les projets MSBuild. Pour plus d’informations, consultez [Projets Dossier ouvert pour C++](../build/open-folder-projects-cpp.md).

- Améliorations de l’expérience de la fonctionnalité Ouvrir le dossier. Vous pouvez personnaliser l’expérience via ces fichiers .json :
  - CppProperties.json pour personnaliser l’expérience IntelliSense et l’expérience de navigation.
  - Tasks.json pour personnaliser les étapes de la génération.
  - Launch.json pour personnaliser l’expérience du débogage.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Amélioration de la prise en charge d’autres compilateurs et environnements de génération tels que MinGW et Cygwin. Pour plus d’informations, consultez [Using MinGW and Cygwin with Visual C++ and Open Folder](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Ajout de la prise en charge de la définition de variables d’environnement globales et spécifiques à la configuration dans CppProperties.json et CMakeSettings.json. Ces variables d’environnement peuvent être consommées par des configurations de débogage définies dans launch.vs.json et des tâches dans tasks.vs.json. Pour plus d’informations, consultez [Customizing your Environment with Visual C++ and Open Folder](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Amélioration de la prise en charge du générateur Ninja de CMake, y compris la possibilité de facilement cibler des plateformes 64 bits.

## <a name="cmake-support-via-open-folder"></a>Prise en charge de CMake via Ouvrir le dossier

Visual Studio 2017 introduit la prise en charge de l’utilisation de projets CMake sans les convertir en fichiers projet MSBuild (.vcxproj). Pour plus d’informations, consultez [Projets CMake dans Visual Studio](../build/cmake-projects-in-visual-studio.md). L’ouverture de projets CMake avec **Ouvrir le dossier** configure automatiquement l’environnement pour la modification, la génération et le débogage en C++.

- IntelliSense pour C++ fonctionne sans qu’il soit nécessaire de créer un fichier CppProperties.json dans le dossier racine. Nous avons également ajouté une nouvelle liste déroulante pour permettre aux utilisateurs de basculer facilement entre les configurations fournies par les fichiers CMake et CppProperties.json.

- Des options de configuration supplémentaires sont prises en charge via un fichier CMakeSettings.json qui se trouve dans le même dossier que le fichier CMakeLists.txt.

  ![CMake – Ouvrir le dossier](media/cmake-cpp.png "CMake – Ouvrir le dossier")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Ajout de la prise en charge du générateur Ninja de CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- Ajout de la prise en charge de l’importation des caches CMake existants.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- Ajout de la prise en charge de CMake 3.11, analyse du code dans les projets CMake, vue des cibles dans l’Explorateur de solutions, options de génération du cache et compilation de fichier unique. Pour plus d’informations, consultez [CMake Support in Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) et [Projets CMake en Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development-with-c"></a>Développement Windows Desktop avec C++

Nous fournissons à présent une expérience d’installation plus fine pour la charge de travail C++ d’origine. Nous avons ajouté des composants sélectionnables qui vous permettent d’installer uniquement les outils dont vous avez besoin. Les tailles d’installation indiquées pour les composants répertoriés dans l’interface utilisateur du programme d’installation ne sont pas exactes et sous-estiment la taille totale.

Pour créer correctement des projets Win32 dans la charge de travail de bureau C++, vous devez installer un ensemble d’outils et un SDK Windows. Installez les composants recommandés (sélectionnés) **Ensemble d’outils VC++ 2017 v141 (x86,x64)** et **SDK Windows 10 (10.0.nnnnn)** pour assurer le bon fonctionnement. Si les outils nécessaires ne sont pas installés, les projets ne sont pas correctement créés et l’Assistant se bloque.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Visual C++ Build Tools (disponible jusqu’ici comme produit autonome) est désormais fourni en tant que charge de travail dans Visual Studio Installer. Cette charge de travail installe uniquement les outils nécessaires pour générer des projets C++ sans installer l’IDE de Visual Studio. Les deux ensembles d’outils v140 et v141 sont inclus. L’ensemble d’outils v141 contient les dernières améliorations de Visual Studio 2017 version 15.5. Pour plus d’informations, consultez [Visual Studio Build Tools now include the VS2017 and VS2015 MSVC Toolsets](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Développement Linux avec C++

L’extension populaire [Visual C++ pour le développement Linux](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) fait désormais partie de Visual Studio. Cette installation fournit tout ce dont vous avez besoin pour développer et déboguer des applications C++ exécutées dans un environnement Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 version 15.2

Des améliorations ont été apportées au partage de code multiplateforme et à la visualisation des types. Pour plus d’informations, consultez [Linux C++ improvements for cross-platform code sharing and type visualization](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- La charge de travail Linux prend maintenant en charge **rsync** comme alternative à **sftp** pour la synchronisation des fichiers sur des machines Linux distantes.
- La compilation croisée ciblant les microcontrôleurs ARM est maintenant prise en charge. Pour activer cette fonctionnalité dans l’installation, choisissez la charge de travail **Développement Linux en C++** et sélectionnez l’option **Développement embarqué et IoT**. Cette option ajoute les outils de compilation croisée GCC ARM à votre installation. Pour plus d’informations, consultez [ARM GCC Cross Compilation in Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- La prise en charge de CMake a été améliorée. Vous pouvez maintenant utiliser votre base de code CMake existante sans avoir à la convertir en projet Visual Studio. Pour plus d’informations, consultez [Configurer un projet CMake Linux](../linux/cmake-linux-project.md).
- La prise en charge de l’exécution de tâches distantes a été améliorée. Vous pouvez exécuter des commandes sur un système distant qui est défini dans le Gestionnaire de connexions de Visual Studio. Avec les tâches distantes, vous pouvez également copier des fichiers sur le système distant.
Pour plus d’informations, consultez [Configurer un projet CMake Linux](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

- Diverses améliorations apportées aux scénarios de charge de travail Linux. Pour plus d’informations, consultez [Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- IntelliSense pour les en-têtes sur les connexions à distance en-tête Linux. Pour plus d’informations, consultez [IntelliSense for Remote Linux Headers](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) et [Configurer un projet CMake Linux](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Développement de jeux avec C++

Utilisez toute la puissance de C++ pour créer des jeux professionnels reposant sur DirectX ou Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Développement mobile en C++ (Android et iOS)

Vous pouvez désormais créer et déboguer des applications mobiles, à l’aide de Visual Studio, capables de cibler Android et iOS.

## <a name="universal-windows-apps"></a>Applications de la plateforme Windows universelle

C++ est fourni sous forme de composant facultatif pour la charge de travail Application Windows universelle.  Actuellement, la mise à niveau des projets C++ doit être effectuée manuellement. Si vous ouvrez un projet de plateforme Windows universelle (UWP) ciblé pour v140 dans Visual Studio 2017, vous devez sélectionner l’ensemble d’outils de plateforme v141 dans les pages des propriétés du projet si Visual Studio 2015 n’est pas installé.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nouvelles options pour C++ sur la plateforme Windows universelle (UWP)

Vous disposez maintenant de nouvelles options pour l’écriture et l’empaquetage d’applications C++ pour la plateforme Windows universelle et le Windows Store : vous pouvez utiliser l’infrastructure Desktop Bridge pour empaqueter votre application de bureau existante ou un objet COM pour le déploiement via le Windows Store ou via vos canaux existants par sideloading. Les nouvelles fonctionnalités de Windows 10 vous permettent d’ajouter une plateforme universelle Windows (UWP) à votre application de bureau de différentes manières. Pour plus d’informations, consultez [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Un modèle de **projet de création de packages d’application Windows**  a été ajouté et facilite considérablement l’empaquetage d’applications de bureau à l’aide de Desktop Bridge. Cette fonctionnalité est disponible sous **Fichier | Nouveau | Projet | Installé | Visual C++ | Plateforme Windows universelle**. Pour plus d’informations, consultez [Empaqueter une application à l’aide de Visual Studio (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Lors de l’écriture de nouveau code, vous pouvez désormais utiliser C++/WinRT, une projection de langage C++ standard pour Windows Runtime (WinRT) implémentée uniquement dans les fichiers d’en-tête. Il vous permet à la fois de créer et de consommer des API Windows Runtime à l’aide d’un compilateur C++ conforme aux normes. C++/WinRT est conçu pour offrir aux développeurs C++ un accès idéal à l’API Windows moderne. Pour plus d’informations, consultez [C++/WinRT : C++ moderne pour Windows Runtime](https://moderncpp.com/).

Dans la build 17025 du SDK Windows Insider Preview, C++/WinRT est inclus dans Microsoft Windows SDK. Pour plus d’informations, consultez [C++/WinRT is now included the Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Ensemble d’outils de plateforme Clang/C2

L’ensemble d’outils Clang/C2 fourni avec Visual Studio 2017 prend désormais en charge le commutateur **/bigobj**, qui est essentiel pour la création de gros projets. Il inclut également plusieurs résolutions de bogues importantes, à la fois au niveau du front-end et du back-end du compilateur.

## <a name="c-code-analysis"></a>Analyse du code C++

Les vérificateurs principaux C++ permettant d’appliquer les [directives principales C++](https://github.com/isocpp/CppCoreGuidelines) sont désormais distribués avec Visual Studio. Il suffit d’activer les vérificateurs dans la boîte de dialogue **Code Analysis Extensions** (Extensions d’analyse du code) dans les pages de propriétés du projet pour que les extensions soient incluses quand vous exécutez l’analyse du code. Pour plus d’informations, consultez [Using the C++ Core Guidelines checkers](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Page de propriétés CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Ajout de la prise en charge des règles liées à la gestion de ressources.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- Les nouvelles vérifications C++ Core Guidelines portent sur le caractère correct des pointeurs intelligents, sur l’utilisation correcte des initialiseurs globaux et sur le marquage des constructions utilisées comme `goto` et sur les casts incorrects.

- Certains numéros d’avertissement utilisés dans la version 15.3 ont été supprimés dans la version 15.5. Ces avertissements ont été remplacés par des vérifications plus spécifiques.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 version 15.6

- Ajout de la prise en charge de l’analyse de fichier unique et amélioration des performances d’analyse au moment de l’exécution. Pour plus d’informations, consultez [C++ Static Analysis Improvements for Visual Studio 2017 15.6 Preview 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

- Ajout de la prise en charge de [/analyze:ruleset](../build/reference/analyze-code-analysis.md) qui vous permet de spécifier les règles d’analyse de code à exécuter.
- Ajout de la prise en charge de règles C++ Core Guidelines supplémentaires.  Pour plus d’informations, consultez [Using the C++ Core Guidelines checkers](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Test unitaire

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Les adaptateurs Google Test Adapter et Boost.Test Adapter sont désormais disponibles comme composants du **Développement Desktop en C++** et sont intégrés à **l’Explorateur de tests**. La prise en charge de CTest a été ajoutée pour les projets Cmake (qui utilisent la fonctionnalité Ouvrir le dossier), mais l’intégration complète avec **l’Explorateur de tests** n’est pas encore disponible. Pour plus d’informations, consultez [Écriture de tests unitaires pour C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 version 15.6

- Ajout de la prise en charge de la bibliothèque dynamique Boost.Test.
- Un modèle d’élément Boost.Test est maintenant disponible dans l’IDE.

Pour plus d’informations, consultez [Boost.Test Unit Testing: Dynamic Library support and New Item Template](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

Ajout de la prise en charge de [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) pour les projets de test unitaire C++. Pour plus d’informations, consultez [Announcing CodeLens for C++ Unit Testing](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio Graphics Diagnostics

Visual Studio Graphics Diagnostics est un ensemble d’outils pour l’enregistrement, puis l’analyse des problèmes de rendu et de performances des applications Direct3D. Les fonctionnalités Graphics Diagnostics peuvent être utilisées sur les applications qui s’exécutent localement sur votre PC Windows, dans un émulateur d’appareil Windows, ou sur un PC ou un appareil distant.

- **Entrées et sorties pour les nuanceurs de sommets et de géométrie :** la possibilité d’afficher les entrées et sorties des nuanceurs de sommets et de géométrie a été l’une des fonctionnalités les plus demandées et est maintenant prise en charge dans les outils. Il vous suffit de sélectionner l’étape VS ou GS dans la vue Étapes de canalisation pour commencer à examiner ses entrées et sorties dans le tableau ci-dessous.

  ![Entrées/sorties pour les nuanceurs](media/io-shaders.png)

- **Recherche et filtrage dans la table des objets :** fournit un moyen rapide et facile de trouver les ressources que vous recherchez.

  ![Rechercher](media/search.png)

- **Historique des ressources :** cette nouvelle vue offre une façon simplifiée d’afficher tout l’historique des modifications d’une ressource utilisée pendant le rendu d’un frame capturé. Pour appeler l’historique d’une ressource, cliquez simplement sur l’icône de l’horloge en regard d’un lien hypertexte de ressource.

  ![Historique des ressources](media/resource-history.png)

  La nouvelle fenêtre de l’outil **Historique des ressources** s’affiche, montrant l’historique des modifications de la ressource.

  ![Modification de l’historique des ressources](media/resource-history-change.png)

  Si votre frame a été capturé avec la capture de pile des appels complète activée (**Visual Studio > Outils > Options** sous **Graphics Diagnostics**), le contexte de chaque événement de modification peut être rapidement déduit et inspecté dans votre projet Visual Studio.

- **Statistiques d’API :** affichez une synthèse générale de l’utilisation des API dans votre frame. Cela peut être pratique pour détecter des appels dont vous ne vous rendez pas compte ou des appels trop nombreux. Cette fenêtre est disponible via **View (Afficher) > Statistiques d’API** dans Visual Studio Graphics Analyzer.

  ![Statistiques d’API](media/api-stats.png)

- **Statistiques de la mémoire :** affichez la quantité de mémoire que le pilote alloue pour les ressources que vous créez dans le frame. Cette fenêtre est disponible via **Afficher > Statistiques de la mémoire** dans **Visual Studio Graphics Analyzer**. Vous pouvez copier les données dans un fichier CSV pour les afficher dans une feuille de calcul en cliquant avec le bouton droit et en choisissant **Copier tout**.

  ![Statistiques de la mémoire](media/memory-stats.png)

- **Validation du frame :** la nouvelle liste d’erreurs et d’avertissements facilite la navigation dans votre liste d’événements basée sur les éventuels problèmes détectés par la couche de débogage Direct3D. Cliquez sur **Afficher > Validation du frame** dans Visual Studio Graphics Analyzer pour ouvrir la fenêtre. Cliquez ensuite sur **Exécuter la validation** pour commencer l’analyse. L’opération peut prendre plusieurs minutes, selon la complexité du frame.

  ![Validation du frame](media/frame-validation.png)

- **Analyse des frames pour D3D12 :** Utilisez l’analyse des frames pour analyser les performances des appels de dessin avec des expériences de scénarios dirigées. Basculez vers l’onglet Analyse des frames et lancez l’analyse pour afficher le rapport. Pour plus de détails, regardez la vidéo [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool).

  ![Analyse des frames](media/frame-analysis.png)

- **Améliorations de l’utilisation du GPU :** Vous pouvez ouvrir les suivis effectués via le profileur de l’utilisation du GPU Visual Studio avec le mode GPU ou l’outil Windows Performance Analyzer (WPA) pour une analyse plus détaillée. Si Windows Performance Toolkit est installé, deux liens hypertexte s’affichent, un pour WPA et l’autre pour le mode GPU, en bas à droite de la vue d’ensemble de la session.

  ![Utilisation du GPU](media/gpu-usage.png)

  Les suivis ouverts en mode GPU via ce lien prennent en charge le zoom et le panoramique synchronisés dans la chronologie entre Visual Studio et le mode GPU. Une case à cocher dans Visual Studio permet de contrôler si la synchronisation est activée ou non.

  ![Mode GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Pour obtenir la liste complète des nouveautés jusqu’à Visual Studio 2015, Update 3, consultez [Visual C++ What’s New 2003 through 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015). Pour plus d’informations sur les nouveautés introduites dans toutes les versions de Visual Studio 2015, consultez les notes de publication liées disponibles dans [l’Historique des notes de publication de Visual Studio 2015](/visualstudio/releasenotes/vs2015-version-history). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2019, consultez [Nouveautés de C++ dans Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2017, consultez [Nouveautés de C++ dans Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017).

::: moniker-end
