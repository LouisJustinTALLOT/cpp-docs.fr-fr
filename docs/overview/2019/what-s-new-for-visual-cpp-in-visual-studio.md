---
title: Nouveautés de C++ dans Visual Studio 2019
ms.date: 04/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 493b96a8ce3359cc18287adbae8cbd6c374671ec
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779487"
---
<!--NOTE all https:// links to docs.microsoft.com need to be converted to site-relative links prior to publishing-->

# <a name="whats-new-for-c-in-visual-studio-2019"></a>Nouveautés de C++ dans Visual Studio 2019

Visual Studio 2019 comprend un grand nombre de mises à jour et de correctifs de l’environnement Microsoft C++. Nous avons résolu de nombreux bogues et problèmes signalés dans le compilateur et les outils, beaucoup d’entre eux ayant été soumis par des clients via les options [Signaler un problème](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) et [Faire une suggestion](https://developercommunity.visualstudio.com/spaces/62/index.html) sous **Envoyer des commentaires** . Merci d’avoir signalé ces bogues. Pour plus d’informations sur l’ensemble des nouveautés de Visual Studio, visitez [Nouveautés de Visual Studio](/visualstudio/ide/whats-new-visual-studio-2019).

## <a name="c-compiler"></a>compilateur C++

- L’option `/std:c++latest` inclut désormais les fonctionnalités de C++20 qui ne sont pas nécessairement complètes, notamment la prise en charge initiale de l’opérateur C ++ 20 <=> (« vaisseau spatial ») pour la comparaison tridirectionnelle.

- [P0941R2 - macros de test de fonctionnalité](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) est terminé, avec la prise en charge de `__has_cpp_attribute`. Les macros de test de fonctionnalité sont prises en charge dans tous les modes Standard.

- [C++20 P1008R1 - interdiction des agrégats avec les constructeurs déclarés par l’utilisateur](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) est également terminé.

- Prise en charge améliorée des fonctionnalités C++17, plus une prise en charge expérimentale de fonctionnalités C++20 comme les modules et les coroutines. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2019](../cpp-conformance-improvements.md).

- Le commutateur `/Gm` du compilateur C++ est maintenant déprécié. Envisagez de désactiver le commutateur `/Gm` dans vos scripts de build s’il y est défini explicitement. Vous pouvez cependant ignorer sans problème l’avertissement de dépréciation de `/Gm`, car il n’est pas traité en tant qu’erreur quand vous utilisez « Considérer les avertissements comme des erreurs » (`/WX`).

- Les en-têtes précompilés ne sont plus générés par défaut pour les applications de bureau et console C++.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, sécurité, diagnostics et gestion des versions

Analyse améliorée avec `/Qspectre` afin de fournir une aide à l’atténuation des risques pour Spectre Variant 1 (CVE-2017-5753). Pour plus d’informations, consultez [Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Améliorations apportées à la bibliothèque standard C++

- [C++20 P0550R2 \(remove_cvref)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) est terminé.

- \<charconv> to_chars() à virgule flottante de C++17 a été amélioré : chars_format::fixed le plus court est de 60 à 80 % plus rapide et chars_format::hex le plus court/précision est terminé.

- Davantage d’algorithmes ont des implémentations parallélisées : is_sorted(), is_sorted_until(), is_partitioned(), set_difference(), set_intersection(), is_heap(), is_heap_until().

- Améliorations apportées à `std::variant` pour le rendre plus adapté à l’optimiseur, ce qui entraîne la génération d’un meilleur code. L’incorporation (inlining) de code est désormais bien meilleure avec `std::visit`.

- Nous avons appliqué le format clang aux en-têtes de la bibliothèque standard C++ pour une meilleure lisibilité.

- Amélioration du débit quand plusieurs fonctionnalités de la bibliothèque standard sont compilées avec `if constexpr`.

- Optimisation de la conception physique de la bibliothèque standard afin d’éviter la compilation des parties de la bibliothèque standard qui ne sont pas dans un #include, ce qui réduit de moitié le temps de génération d’un fichier vide qui inclut seulement \<vector>.

## <a name="performancethroughput-fixes"></a>Correctifs de performances et de débit

- Améliorations du débit de la génération, notamment la gestion par l’éditeur de liens des E/S de fichier, et la durée de l’établissement des liens dans la création et la fusion des types PDB.

- Ajout de la prise en charge de base de la vectorisation SIMD OpenMP. Vous pouvez l’activer avec le nouveau commutateur CL `-openmp:experimental`. Cette option permet la vectorisation potentielle des boucles annotées avec `#pragma omp simd`. La vectorisation n’est pas garantie, et les boucles annotées mais pas vectorisées génèrent un avertissement. Aucune clause SIMD n’est prise en charge : elles sont simplement ignorées et un avertissement est généré.

- Ajout d’un nouveau commutateur de ligne de commande d’incorporation (inlining) `-Ob3`, qui est une version plus agressive de `-Ob2`. `-O2` (optimiser le fichier binaire pour la vitesse) implique toujours `-Ob2` par défaut. Si vous trouvez que le compilateur n’incorpore pas de façon suffisamment agressive, envisagez de passer `-O2 -Ob3`.

- Pour prendre en charge la vectorisation manuelle des boucles avec des appels de fonctions de bibliothèque mathématique et certaines autres opérations telles que la division d’entiers, nous avons ajouté la prise en charge des fonctions intrinsèques SVML (Short Vector Math Library). Ces fonctions calculent les vecteurs équivalents 128 bits, 256 bits ou 512 bits. Pour obtenir les définitions des fonctions prises en charge, consultez le [Guide des intrinsèques Intel](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Optimisations nouvelles et améliorées :

  - Simplifications arithmétiques et de pliage de constante pour les expressions à l’aide d’intrinsèques de vecteur SIMD, pour les formes float et integer.

  - Analyse plus puissante pour extraire des informations de flux de contrôle (instructions if/else/switch) afin de supprimer les branches toujours prouvées comme étant true ou false.

  - Amélioration du déroulement de memset de façon à utiliser les instructions de vecteur SSE2.

  - Amélioration de la suppression des copies de struct/classes inutiles, en particulier pour les programmes C++ qui passent par valeur.

  - Amélioration de l’optimisation du code utilisant `memmove`, comme `std::copy` ou `std::vector` et une construction `std::string`.

## <a name="c-ide"></a>IDE C++

### <a name="live-share-c-support"></a>Prise en charge de C++ par Live Share

[Live Share ](/visualstudio/liveshare/) prend désormais en charge C++, ce qui permet aux développeurs utilisant Visual Studio ou Visual Studio Code de collaborer en temps réel. Pour plus d’informations, consultez [Announcing Live Share for C++: Real-Time Sharing and Collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode pour C++

IntelliCode est une extension facultative qui exploite toutes ses données d’apprentissage et le contexte de votre code pour suggérer les éléments de code que vous êtes le plus susceptible d’utiliser en haut de votre liste de complétion. Il peut souvent vous éviter de faire défiler la liste vers le bas. Pour C++, IntelliCode est le plus performant quand vous utilisez des bibliothèques courantes comme la bibliothèque standard. Pour plus d’informations, consultez [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

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

## <a name="cmake-support"></a>Prise en charge de CMake

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

## <a name="debugging"></a>Débogage

- Pour les applications C++ exécutées sur Windows, les fichiers PDB se chargent désormais dans un processus 64 bits distinct. Ce changement résout plusieurs problèmes de plantage qui pouvaient survenir quand le débogueur manquait de mémoire au moment du débogage d’applications contenant de nombreux modules et fichiers PDB.

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

## <a name="unit-testing"></a>Test unitaire

Le modèle de projet de test C++ managé n’est plus disponible. Vous pouvez continuer à utiliser le framework de test C++ managé dans vos projets existants. Pour les nouveaux tests unitaires, utilisez un des frameworks de test natifs pour lesquels Visual Studio fournit des modèles (MSTest, Google Test) ou le modèle de projet de test C# managé.
