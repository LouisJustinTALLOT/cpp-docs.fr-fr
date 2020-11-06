---
title: Nouveautés de C++ dans Visual Studio
description: Les nouvelles fonctionnalités et les correctifs du compilateur et des outils Microsoft C/C++ dans Visual Studio.
ms.date: 05/19/2020
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
ms.openlocfilehash: db328a5806ecb3e48a934d65854c14d424e018f1
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334167"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Nouveautés de C++ dans Visual Studio

::: moniker range=">=msvc-160"

Visual Studio 2019 comprend un grand nombre de mises à jour et de correctifs de l’environnement Microsoft C++. Nous avons résolu plusieurs bogues et problèmes dans le compilateur et les outils. Beaucoup de ces problèmes ont été soumis par des clients via les options [Signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019&preserve-view=true) et [Faire une suggestion](https://aka.ms/feedback/suggest?space=62) sous **Envoyer des commentaires**. Merci d’avoir signalé ces bogues. Pour plus d’informations sur l’ensemble des nouveautés de Visual Studio, visitez [Nouveautés de Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2017, consultez [Nouveautés de C++ dans Visual Studio 2017](?preserve-view=true&view=msvc-150). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2015 et versions antérieures, consultez [Nouveautés de Visual C++ entre 2003 et 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

## <a name="c-compiler"></a>compilateur C++

- Une prise en charge améliorée des fonctionnalités et correctifs d’exactitude C++17, plus une prise en charge expérimentale de fonctionnalités C++20 comme les modules et les coroutines. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2019](cpp-conformance-improvements.md).

- L' `/std:c++latest` option inclut désormais des fonctionnalités c++ 20 qui ne sont pas nécessairement complètes, notamment la prise en charge initiale de l’opérateur c++ 20 \<=> (« Space ») pour la comparaison tridirectionnelle.

- Le commutateur `/Gm` du compilateur C++ est maintenant déprécié. Envisagez de désactiver le commutateur `/Gm` dans vos scripts de build s’il y est défini explicitement. Vous pouvez cependant ignorer sans problème l’avertissement de dépréciation de `/Gm`, car il n’est pas traité en tant qu’erreur quand vous utilisez « Considérer les avertissements comme des erreurs » (`/WX`).

- Comme MSVC commence la mise en œuvre de fonctionnalités à partir du brouillon standard C++20 sous l’indicateur `/std:c++latest`, `/std:c++latest` est désormais incompatible avec `/clr` (toutes les saveurs), `/ZW`, et `/Gm`. Dans Visual Studio 2019, utilisez le mode `/std:c++17` ou `/std:c++14` lors de la compilation avec `/clr`, `/ZW` ou `/Gm` (consultez la liste à puces précédente).

- Les en-têtes précompilés ne sont plus générés par défaut pour les applications de bureau et console C++.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, sécurité, diagnostics et gestion des versions

Analyse améliorée avec `/Qspectre` afin de fournir une aide à l’atténuation des risques pour Spectre Variant 1 (CVE-2017-5753). Pour plus d’informations, consultez [Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Améliorations apportées à la bibliothèque standard C++

- Implémentation de nouvelles fonctionnalités de bibliothèque et de nouveaux correctifs d’exactitude C++17 et C++20. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2019](cpp-conformance-improvements.md).

- Le format clang a été appliqué aux en-têtes de la bibliothèque standard C++ pour une meilleure lisibilité.

- Étant donné que Visual Studio prend désormais en charge Uniquement mon code pour C++, la bibliothèque standard n’a plus besoin de fournir de mécanisme personnalisé pour `std::function` et `std::visit` pour obtenir le même effet. La suppression de ce mécanisme n’aura quasiment aucun effet visible par l’utilisateur. Une exception est que le compilateur ne produit plus de diagnostics qui indiquent des problèmes à la ligne 15732480 ou 16707566 de \<type_traits> ou \<variant> .

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Améliorations de performances/débit dans le compilateur et la bibliothèque standard

- Améliorations du débit de la génération, notamment la gestion par l’éditeur de liens des E/S de fichier, et la durée de l’établissement des liens dans la création et la fusion des types PDB.

- Ajout de la prise en charge de base de la vectorisation SIMD OpenMP. Vous pouvez l’activer à l’aide du nouveau commutateur du compilateur **`/openmp:experimental`** . Cette option permet la vectorisation potentielle des boucles annotées avec `#pragma omp simd`. La vectorisation n’est pas garantie, et les boucles annotées mais pas vectorisées génèrent un avertissement. Aucune clause SIMD n’est prise en charge ; elles sont ignorées et un avertissement est émis.

- Ajout d’un nouveau commutateur de ligne de commande inline **`/Ob3`** , qui est une version plus agressive de **`/Ob2`** . **`/O2`** (optimiser le binaire pour la vitesse) implique toujours **`/Ob2`** par défaut. Si vous constatez que le compilateur n’est pas Inline assez agressivement, envisagez de passer **`/O2 -Ob3`** .

- Nous avons ajouté la prise en charge des fonctions intrinsèques SVML (Short Vector Math Library). Ces fonctions calculent les vecteurs équivalents 128 bits, 256 bits ou 512 bits. Nous les avons ajoutés pour prendre en charge la vectorisation manuelle des boucles avec des appels aux fonctions de bibliothèque mathématique, et certaines autres opérations telles que la Division d’entier. Pour obtenir les définitions des fonctions prises en charge, consultez le [Guide des intrinsèques Intel](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Optimisations nouvelles et améliorées :

  - Simplifications arithmétiques et de pliage de constante pour les expressions à l’aide d’intrinsèques de vecteur SIMD, pour les formes float et integer.

  - Analyse plus puissante pour extraire des informations de flux de contrôle (instructions if/else/switch) afin de supprimer les branches toujours prouvées comme étant true ou false.

  - Amélioration du déroulement de memset de façon à utiliser les instructions de vecteur SSE2.

  - Amélioration de la suppression des copies de struct/classes inutiles, en particulier pour les programmes C++ qui passent par valeur.

  - Amélioration de l’optimisation du code utilisant `memmove`, comme `std::copy` ou `std::vector` et une construction `std::string`.

- Optimisez la conception physique de la bibliothèque standard afin d’éviter de compiler des parties de la bibliothèque standard qui ne sont pas directement incluses. Cette modification permet de réduire la durée de la génération d’un fichier vide qui comprend uniquement une \<vector> demi-partie. En conséquence, vous devrez peut-être ajouter des directives `#include` pour les en-têtes qui précédemment étaient indirectement inclus. Par exemple, le code qui utilise `std::out_of_range` pourrait maintenant avoir à ajouter `#include <stdexcept>`. Le code qui utilise un opérateur d’insertion de flux doit maintenant ajouter `#include <ostream>`. L’avantage est que seules les unités de traduction qui utilisent réellement \<stdexcept> \<ostream> des composants ou paient le coût du débit pour les compiler.

- `if constexpr` a été appliqué à plusieurs endroits dans la bibliothèque standard pour un débit amélioré et une taille de code réduite dans les opérations de copie, dans les permutations comme l’inversion et la rotation et dans la bibliothèque d’algorithmes parallèles.

- La bibliothèque standard utilise désormais `if constexpr` en interne afin de réduire la compilation même en mode C++14.

- La détection de lien dynamique de runtime pour la bibliothèque d’algorithmes parallèles n’utilise plus une page entière pour stocker le tableau de pointeurs de fonction. Le marquage de cette mémoire en lecture seule n’est plus considéré comme pertinent pour des raisons de sécurité.

- `std::thread` du constructeur n’attend plus que le thread démarre, et n’insère plus autant de calques d’appels de fonction entre la bibliothèque C sous-jacente `_beginthreadex` et l’objet fourni pouvant être appelé. `std::thread`Placez précédemment six fonctions entre `_beginthreadex` et l’objet pouvant être appelé fourni. Ce nombre a été réduit à seulement trois, deux d’entre eux `std::invoke` . Cette modification résout également un bogue de minutage obscur, où un `std::thread` constructeur cesserait de répondre si l’horloge système a changé au moment précis où le `std::thread` était en cours de création.

- Correction d’une régression des performances dans `std::hash` que nous avons introduit lors de l’implémentation `std::hash<std::filesystem::path>`.

- La bibliothèque standard utilise désormais dans plusieurs endroits, des destructeurs au lieu de blocs catch pour atteindre l’exactitude. Cette modification entraîne une meilleure interaction du débogueur : les exceptions que vous levez via la bibliothèque standard dans les emplacements affectés s’affichent désormais comme étant levées à partir de leur site de levée d’origine, au lieu de notre nouvelle levée. Tous les blocs catch de la bibliothèque standard n’ont pas été éliminés. Nous pensons que le nombre de blocs catch doit être réduit dans les versions ultérieures de MSVC.

- Un codegen non optimal dans `std::bitset` provoqué par une levée conditionnelle à l’intérieur d’une fonction noexcept a été résolu en factorisant le chemin d’accès levant.

- Les familles `std::list` et `std::unordered_*` utilisent des itérateurs de non débogage en interne dans plusieurs endroits.

- Plusieurs membres `std::list` ont été modifiés pour réutiliser les nœuds de la liste lorsque cela est possible au lieu de les libérer et de les redistribuer. Par exemple, étant donné un `list<int>` qui a déjà une taille de 3, un appel à `assign(4, 1729)` maintenant remplace les ints dans les trois premiers nœuds de liste, et alloue un nouveau nœud de liste avec la valeur 1729.

- Tous les appels de la bibliothèque standard à `erase(begin(), end())` ont été remplacés par `clear()`.

- `std::vector` initialise et efface désormais les éléments plus efficacement dans certains cas.

- Améliorations apportées à `std::variant` pour le rendre plus adapté à l’optimiseur, ce qui entraîne la génération d’un meilleur code. L’incorporation (inlining) de code est désormais bien meilleure avec `std::visit`.

## <a name="c-ide"></a>IDE C++

### <a name="live-share-c-support"></a>Prise en charge de C++ par Live Share

[Live Share ](/visualstudio/liveshare/) prend désormais en charge C++, ce qui permet aux développeurs utilisant Visual Studio ou Visual Studio Code de collaborer en temps réel. Pour plus d’informations, consultez [annonce de Live share pour C++ : Real-Time le partage et la collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode pour C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

IntelliCode utilise sa propre formation complète et votre contexte de code pour mettre ce que vous êtes le plus susceptible d’utiliser en haut de votre liste de saisie semi-automatique. Il peut souvent vous éviter de faire défiler la liste vers le bas. Pour C++, IntelliCode est le plus performant quand vous utilisez des bibliothèques courantes comme la bibliothèque standard. IntelliCode est une extension facultative disponible en tant que composant de charge de travail dans le programme d’installation. Pour plus d’informations, consultez [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>Modèle IntelliSense

La **barre de modèles** utilise maintenant l’interface utilisateur de la **fenêtre d’aperçu** au lieu d’une fenêtre modale, prend en charge les modèles imbriqués et prérenseigne les arguments par défaut dans la **fenêtre d’aperçu**. Pour plus d’informations, consultez [Template IntelliSense Improvements for Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/). Une liste déroulante **Utilisés le plus récemment** dans la **barre de modèles** vous permet de basculer rapidement entre des ensembles antérieurs d’exemples d’arguments.

### <a name="new-start-window-experience"></a>Nouvelle fenêtre de démarrage

Lors du lancement de l’IDE, une nouvelle fenêtre de démarrage s’affiche. Il offre des options permettant d’ouvrir des projets récents, de cloner du code à partir du contrôle de code source, d’ouvrir le code local en tant que solution ou dossier, ou de créer un projet. La boîte de dialogue Nouveau projet a également été repensée pour permettre une expérience de recherche en premier avec possibilité de filtrage.

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

L’info-bulle Info express respecte désormais la colorisation sémantique de votre éditeur. Il dispose également d’un nouveau lien de **recherche en ligne** qui recherche de la documentation en ligne pour en savoir plus sur la construction de code survolé. Le lien fourni par Info Express pour le code rouge-squiggled recherche l’erreur en ligne. De cette façon, vous n’avez pas besoin de retaper le message dans votre navigateur. Pour plus d’informations, consultez [améliorations des informations rapides dans Visual Studio 2019 : colorisation et recherche en ligne](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>IntelliCode disponible dans la charge de travail C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

IntelliCode est désormais fourni en tant que composant facultatif dans la charge de travail **Développement Desktop en C++**. Pour en savoir plus, voir [IntelliCode C++ amélioré désormais fourni avec Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Prise en charge de CMake

- Prise en charge de CMake 3.14

- Visual Studio peut maintenant ouvrir les caches CMake existants générés par des outils externes, comme CMakeGUI, des systèmes de génération de métadonnées personnalisés ou des scripts de génération appelant eux-mêmes cmake.exe.

- Amélioration des performances d’IntelliSense.

- Un nouvel éditeur de paramètres fournit une alternative à la modification manuelle de CMakeSettings.json et offre une similarité avec CMakeGUI.

- Visual Studio vous aide à démarrer votre développement en C++ avec CMake sur Linux en détectant si vous avez une version compatible de CMake sur votre ordinateur Linux. Si ce n’est pas le cas, il propose de l’installer pour vous.

- Les paramètres incompatibles dans CMakeSettings, comme les incompatibilités d’architectures ou les paramètres de générateur CMake incompatibles, sont marqués par des tildes dans l’éditeur JSON et par des erreurs dans la liste d’erreurs.

- La chaîne d’outils vcpkg est automatiquement détectée et activée pour les projets CMake qui sont ouverts dans l’IDE, une fois que `vcpkg integrate install` a été exécuté. Ce comportement peut être désactivé en spécifiant un fichier de chaîne d’outils vide dans cmakesettings.

- Les projets CMake autorisent maintenant le débogage Uniquement mon code par défaut.

- Les avertissements d’analyse statique sont maintenant traités en arrière-plan et s’affichent dans l’éditeur pour les projets CMake.

- Messages de début et de fin de génération et de configuration plus clairs pour les projets CMake, et prise en charge de l’interface utilisateur de progression de la génération de Visual Studio. De plus, il existe désormais un paramètre de niveau de détail CMake dans **Outils > Options** pour personnaliser le niveau de détail des messages de génération et de configuration CMake dans la fenêtre Sortie.

- Le paramètre `cmakeToolchain` est désormais pris en charge dans CMakeSettings.json pour spécifier des chaînes d’outils sans modifier manuellement la ligne de commande CMake.

- Nouveau raccourci pour le menu **Tout générer** ( **Ctrl+Maj+B** ).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

- Prise en charge intégrée pour la modification, la génération et le débogage de projets CMake avec Clang/LLVM. Pour en savoir plus, voir [Prise en charge Clang/LLVM dans Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux et le sous-système Windows pour Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

- Prise en charge de [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) dans les projets d’inter-plateformes Linux et CMake. Pour en savoir plus, voir [AddressSanitizer (ASan) pour la charge de travail Linux dans Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Prise en charge intégrée de Visual Studio pour l’utilisation de C++ avec le sous-système Windows pour Linux (WSL). Pour en savoir plus, voir [ C++ avec Visual Studio 2019 et le sous-système Windows pour Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>Intégration d’IncrediBuild

IncrediBuild est désormais fourni en tant que composant facultatif dans la charge de travail **Développement Desktop en C++**. Le moniteur de build IncrediBuild est entièrement intégré à l’IDE de Visual Studio. Pour plus d’informations, consultez visualiser [votre build avec IncrediBuild Build Monitor et Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Débogage

- Pour les applications C++ exécutées sur Windows, les fichiers PDB se chargent désormais dans un processus 64 bits distinct. Cette modification résout une plage de pannes provoquée par le débogueur qui manque de mémoire. Par exemple, lors du débogage d’applications qui contiennent un grand nombre de modules et de fichiers PDB.

- La recherche est activée dans les fenêtres **Espion** , **Autos** , et **Variables locales**.

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

- Le kit de développement logiciel (SDK) Windows 8.1 n’est plus disponible dans le programme d’installation de Visual Studio. Nous vous recommandons de mettre à niveau vos projets C++ vers la dernière version du SDK Windows 10. Si vous avez une dépendance dure envers la version 8.1, vous pouvez la télécharger à partir de l’archive du SDK Windows.

- Le ciblage de Windows XP ne sera plus disponible pour le dernier ensemble d’outils C++. Le ciblage de XP avec des bibliothèques et le compilateur MSVC de niveau Visual Studio 2017 est toujours pris en charge et peut être installé par le biais de « Composants individuels ».

- Notre documentation décourage activement l’utilisation de Fusionner les modules pour le déploiement Visual C++ Runtime. Dans cette version, nous allons encore un peu plus loin en marquant nos MSM comme étant dépréciés. Envisagez la migration de votre déploiement central VCRuntime des MSM vers le package redistribuable.

## <a name="mobile-development-with-c-android-and-ios"></a>Développement mobile en C++ (Android et iOS)

L’expérience Android C++ utilise désormais Android SDK 25 et Android NDK 16b par défaut.

## <a name="clangc2-platform-toolset"></a>Ensemble d’outils de plateforme Clang/C2

Le composant expérimental Clang/C2 a été supprimé. Utilisez l’ensemble d’outils MSVC pour garantir une totale conformité aux standards C++ avec `/permissive-` et `/std:c++17`, ou la chaîne d’outils Clang/LLVM pour Windows.

## <a name="code-analysis"></a>Analyse du code

- L’analyse du code s’exécute désormais automatiquement en arrière-plan. Les avertissements sont marqués par des tildes verts dans l’éditeur à mesure que vous tapez. Pour plus d’informations, consultez [In-editor code analysis in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/).

- Nouvelles règles ConcurrencyCheck expérimentales pour les types de bibliothèque standard connus de l' \<mutex> en-tête. Pour plus d’informations, consultez [Concurrency Code Analysis in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Une implémentation partielle mise à jour du [vérificateur de profil de durée de vie](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), qui détecte les références et les pointeurs non résolus. Pour plus d’informations, consultez [Lifetime Profile Update in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Plus de vérifications liées aux coroutines, notamment C26138, C26810, C26811 et la règle expérimentale C26800. Pour plus d’informations, consultez [New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

- Nouveaux correctifs rapides pour des vérifications de variables non initialisées. Pour en savoir plus, voir [Nouveaux correctifs rapides d’analyse de code pour la mémoire non initialisée (C6001) et les avertissements d’utilisation avant init (C26494)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Effectuer des tests unitaires

Le modèle de projet de test C++ managé n’est plus disponible. Vous pouvez continuer à utiliser le framework de test C++ managé dans vos projets existants. Pour les nouveaux tests unitaires, utilisez un des frameworks de test natifs pour lesquels Visual Studio fournit des modèles (MSTest, Google Test) ou le modèle de projet de test C# managé.

::: moniker-end

::: moniker range="=msvc-150"

Visual Studio 2017 comprend un grand nombre de mises à jour et de correctifs de l’environnement C++. Nous avons corrigé plus de 250 bogues et signalé des problèmes dans le compilateur et les outils. Un grand nombre d’entre eux ont été envoyés par les clients par le biais du [rapport un problème et fournissent des options de suggestion](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017&preserve-view=true) sous **Envoyer des commentaires**. Merci d’avoir signalé ces bogues. Pour plus d’informations sur l’ensemble des nouveautés de Visual Studio, visitez [Nouveautés de Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017&preserve-view=true). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2019, consultez [Nouveautés de C++ dans Visual Studio](?preserve-view=true&view=msvc-160). Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2015 et versions antérieures, consultez [Nouveautés de Visual C++ entre 2003 et 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

## <a name="visual-studio-2017-c-compiler"></a>Compilateur C++ Visual Studio 2017

### <a name="c-conformance-improvements"></a>Améliorations de la conformité de C++

Nous avons mis à jour le compilateur C++ et la bibliothèque standard dans cette version avec une prise en charge améliorée des fonctionnalités C++ 11 et C++ 14. Il comprend également une prise en charge préliminaire de certaines fonctionnalités attendues dans la norme C++ 17. Pour plus d’informations, consultez [Améliorations de la conformité de C++ dans Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Le compilateur prend en charge environ 75% des fonctionnalités nouvelles dans C++ 17, notamment les liaisons structurées, **`constexpr`** `if constexpr` les expressions lambda,, les variables Inline, les expressions Fold et **`noexcept`** l’ajout au système de type. Ces fonctionnalités sont disponibles sous l' **`/std:c++17`** option. Pour plus d’informations, consultez [améliorations de la conformité de C++ dans Visual Studio 2017](cpp-conformance-improvements.md)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

L’ensemble d’outils du compilateur MSVC dans Visual Studio version 15.7 est désormais conforme à la norme C++. Pour plus d’informations, consultez [annonce de : MSVC est conforme à la norme c++ et à la conformité du](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) [langage Microsoft c++](./visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017 version 15.8

Le [`/experimental:preprocessor`](../build/reference/experimental-preprocessor.md) commutateur du compilateur active le nouveau préprocesseur MSVC expérimental qui finit par se conformer à toutes les normes C et C++ applicables. Pour plus d’informations, consultez [vue d’ensemble du nouveau préprocesseur MSVC](../preprocessor/preprocessor-experimental-overview.md).

### <a name="new-compiler-options"></a>Nouvelles options du compilateur

- [`/permissive-`](../build/reference/permissive-standards-conformance.md): Activez toutes les options de compilateur de conformité strictes et désactivez la plupart des extensions du compilateur spécifiques à Microsoft (mais pas `__declspec(dllimport)` , par exemple). Cette option est activée par défaut dans Visual Studio 2017 version 15.5.  Le **`/permissive-`** mode de conformité prend en charge la recherche de nom en deux phases. Pour plus d’informations, consultez [améliorations de la conformité de C++ dans Visual Studio](cpp-conformance-improvements.md).

- [`/diagnostics`](../build/reference/diagnostics-compiler-diagnostic-options.md): Active l’affichage de l’emplacement d’erreur ou d’avertissement de diagnostic de trois façons différentes : uniquement le numéro de ligne, le numéro de ligne et la colonne, ou le numéro de ligne et la colonne, avec un signe insertion sous la ligne de code incriminée.

- [`/debug:fastlink`](../build/reference/debug-generate-debug-info.md): Activez jusqu’à 30% de temps de liaison incrémentiel plus rapide (par rapport à Visual Studio 2015) en ne copiant pas toutes les informations de débogage dans le fichier PDB. À la place, le fichier PDB pointe vers les informations de débogage pour les fichiers objets et bibliothèques utilisés pour créer l’exécutable. Consultez [cycle de génération C++ plus rapide dans vs « 15 `/Debug:fastlink` » avec](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) et [recommandations pour accélérer les builds c++ dans Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Visual Studio 2017 permet l’utilisation [`/sdl`](../build/reference/sdl-enable-additional-security-checks.md) de avec [`/await`](../build/reference/await-enable-coroutine-support.md) . Nous avons supprimé la [`/RTC`](../build/reference/rtc-run-time-error-checks.md) limitation avec les coroutines.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- [ `/std:c++14` et `/std:c++latest` ](../build/reference/std-specify-language-standard-version.md): ces options du compilateur vous permettent de vous abonner à des versions spécifiques du langage de programmation ISO C++ dans un projet. La plupart des nouvelles fonctionnalités standard sont protégées par l' **`/std:c++latest`** option.

- [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) active l’ensemble des fonctionnalités C++ 17 implémentées par le compilateur. Cette option désactive la prise en charge du compilateur et de la bibliothèque standard pour les fonctionnalités après C++ 17 : celles qui sont modifiées ou nouvelles dans les versions ultérieures du brouillon de travail, ainsi que les mises à jour de défauts de la norme C++. Pour activer ces fonctionnalités, utilisez **`/std:c++latest`** .

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, sécurité, diagnostics et gestion des versions

Cette version apporte plusieurs améliorations à l’optimisation, à la génération de code, à la gestion de version de l’ensemble d’outils et aux diagnostics. Les améliorations notables sont les suivantes :

- Amélioration de la génération du code des boucles : prise en charge de la vectorisation automatique de la division d’entiers constants, optimisation de l’identification des modèles de memset.
- Amélioration de la sécurité du code : amélioration de l’émission des diagnostics du compilateur de dépassement de mémoire tampon et [`/guard:cf`](../build/reference/guard-enable-control-flow-guard.md) protection à présent des instructions Switch qui génèrent des tables de saut.
- Contrôle de version : la valeur de la macro de préprocesseur intégrée **\_ MSC \_ ver** est désormais mise à jour de façon monotone à chaque mise à jour de Visual C++ ensemble d’outils. Pour plus d’informations, consultez [Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nouvelle disposition de l’ensemble d’outils : le compilateur et les outils de génération connexes ont un nouvel emplacement et une structure de répertoire sur votre ordinateur de développement. La nouvelle disposition permet des installations côte à côte de plusieurs versions du compilateur. Pour plus d’informations, consultez [Compiler Tools Layout in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Amélioration des diagnostics : la fenêtre Sortie affiche maintenant la colonne où une erreur se produit. Pour plus d’informations, consultez [améliorations des diagnostics du compilateur C++ dans Visual Studio « 15 » Preview 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Lors de l’utilisation de coroutines, le **rendement** du mot clé expérimental (disponible sous l' **`/await`** option) a été supprimé. Votre code doit être mis à jour pour utiliser `co_yield` à la place. Pour plus d’informations, consultez [ `yield` mot clé pour devenir `co_yield` dans vs 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

Améliorations supplémentaires apportées aux diagnostics dans le compilateur. Pour plus d'informations, consultez [Diagnostic Improvements in Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Visual C++ les performances du runtime continuent d’augmenter grâce à une meilleure qualité du code généré. Maintenant, vous pouvez simplement recompiler votre code pour rendre votre application plus rapide. Certaines optimisations du compilateur sont nouvelles, comme la vectorisation des stockages de scalaires conditionnels, la combinaison des appels `sin(x)` et `cos(x)` en un nouveau `sincos(x)`, et la suppression des instructions redondantes dans l’optimiseur SSA. D’autres optimisations du compilateur sont des améliorations apportées à des fonctionnalités existantes, telles que : heuristique vectoriseur pour les expressions conditionnelles, meilleures optimisations de boucle et type de contenu float min/max. L’éditeur de liens a une implémentation nouvelle et plus rapide **`/OPT:ICF`** , qui peut entraîner jusqu’à 9% d’accélérations au moment de la liaison, et il existe d’autres correctifs de performances dans les liens incrémentiels. Pour plus d’informations, consultez [/OPT (Optimisations)](../build/reference/opt-optimizations.md) et [/INCREMENTAL (Lier par incrément)](../build/reference/incremental-link-incrementally.md).

Le compilateur Microsoft C++ prend en charge AVX-512 d’Intel. Il contient des instructions de longueur vectorielle qui apportent de nouvelles fonctions dans AVX-512 à des registres larges 128 bits et 256 bits.

L’option [/Zc : noexceptTypes-](../build/reference/zc-noexcepttypes.md) peut être utilisée pour revenir à la version c++ 14 de **`noexcept`** en mode c++ 17 en général. Cette option vous permet de mettre à jour votre code source pour le rendre conforme à C++17 sans pour autant avoir à réécrire tout votre code `throw()`. Pour plus d’informations, consultez [Suppression des spécifications d’exceptions dynamiques et noexcept](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

- Nouveau commutateur de compilateur [/Qspectre](../build/reference/qspectre.md) pour aider à atténuer les attaques par canal latéral d’exécution spéculative. Pour plus d’informations, consultez [atténuations de spectre dans MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nouvel avertissement de diagnostic pour l’atténuation Spectre. Pour plus d’informations, consultez [Spectre diagnostic in Visual Studio 2017 Version 15.7 Preview 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Une nouvelle valeur pour/Zc, **`/Zc:__cplusplus`** , active la création de rapports corrects de la prise en charge de la norme C++. Par exemple, lorsque le commutateur est défini et que le compilateur est en **`/std:c++17`** mode, la valeur se développe à **`201703L`** . Pour plus d’informations, consultez [MSVC now correctly reports __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>Bibliothèque C++ Standard

### <a name="correctness-improvements"></a>Améliorations de l’exactitude

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (version 15.0)

- Améliorations mineures des `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` Diagnostics. Lorsqu’une vérification IDL est déclenchée dans les machines à chaîne, elle signale maintenant le comportement spécifique qui a provoqué la course. Par exemple, au lieu de « itérateur de chaîne non déréférençable » vous recevez « impossible de déréférencer l’itérateur de chaîne car il est hors limites (par exemple un itérateur de fin) ».
- Correction de l’opérateur d’affectation de déplacement `std::promise`, qui pouvait provoquer le blocage définitif du code.
- Correction des erreurs du compilateur avec la conversion implicite de `atomic<T*>` en `T*`.
- `pointer_traits<Ptr>` détecte désormais `Ptr::rebind<U>` correctement.
- Correction d’un **`const`** qualificateur manquant dans l' `move_iterator` opérateur de soustraction.
- Correction d’un codegen incorrect sans déclenchement d’erreur pour les allocateurs avec état définis par l’utilisateur nécessitant `propagate_on_container_copy_assignment` et `propagate_on_container_move_assignment`.
- `atomic<T>` tolère désormais `operator&()` surchargé.
- Légère amélioration des diagnostics du compilateur pour les appels de `bind()` incorrects.

Il existe d’autres améliorations de la bibliothèque standard dans Visual Studio 2017 RTM. Pour obtenir une liste complète, consultez l’entrée de blog de l’équipe C++ [correctifs de la bibliothèque standard dans Visual studio 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Les conteneurs de la bibliothèque standard limitent désormais leur `max_size()` à `numeric_limits<difference_type>::max()`, au lieu du `max()` de `size_type`. Ce changement garantit que le résultat de `distance()` sur les itérateurs de ce conteneur peut être représenté dans le type de retour de `distance()`.
- Correction de la spécialisation manquante `auto_ptr<void>`.
- Les `for_each_n()` `generate_n()` `search_n()` algorithmes, et n’ont pas pu être compilés précédemment si l’argument de longueur n’était pas un type intégral. Ils tentent désormais de convertir les longueurs non intégrales en itérateurs `difference_type` .
- `normal_distribution<float>` n’émet plus d’avertissements dans la bibliothèque standard à propos des conversions restrictives de double en float.
- Correction de certaines opérations `basic_string` qui utilisaient `npos` au lieu de `max_size()` lors de la vérification du dépassement de la taille maximale.
- `condition_variable::wait_for(lock, relative_time, predicate)` attend l’heure relative entière s’il y avait une sortie parasite. À présent, il attend uniquement un seul intervalle de l’heure relative.
- `future::get()` invalide désormais `future`, conformément au standard.
- `iterator_traits<void *>` constituait une erreur matérielle, car il tentait de former `void&` ; il devient désormais une structure vide sans erreur pour permettre l’utilisation de `iterator_traits` dans les conditions SFINAE « is iterator ».
- Certains avertissements signalés par Clang **-wsystem-headers** ont été corrigés.
- « La spécification d’exception dans la déclaration ne correspond pas à la déclaration précédente » signalée par Clang **-Wmicrosoft-exception-spec**.
- Correction également des avertissements d’ordre mem-initializer-list signalés par Clang et C1XX.
- Les conteneurs non ordonnés ne permutaient pas leurs fonctions de hachage ou prédicats lorsque les conteneurs eux-mêmes étaient permutés. C’est le cas désormais.
- De nombreuses opérations de permutation de conteneur sont désormais marquées **`noexcept`** (car notre bibliothèque standard ne prévoit jamais de lever une exception lors de la détection de la condition de comportement non définie non- `propagate_on_container_swap` équivalent-Allocator).
- De nombreuses `vector<bool>` opérations sont désormais marquées **`noexcept`** .
- La bibliothèque standard applique désormais un `value_type` d’allocateur correspondant (en mode C++17) avec une hachure d’échappement de refus.
- Correction de certaines conditions où self-range-insert dans `basic_string` désorganisait le contenu des chaînes. (Remarque : self-range-insert dans vectors est toujours interdit par la norme.)
- `basic_string::shrink_to_fit()` n’est plus affecté par le `propagate_on_container_swap` de l’allocateur.
- `std::decay` gère désormais des types de fonctions abominable, autrement dit des types de fonction CV, Ref-Qualified, ou les deux.
- Modification des directives include pour utiliser la casse appropriée et des barres obliques, et améliorer la portabilité.
- Correction de l’avertissement C4061 « L’énumérateur *énumérateur* dans le switch de l’énumération *énumération* n’est pas géré explicitement par une étiquette case ». Cet avertissement est désactivé par défaut et a été résolu en tant qu’exception à la stratégie générale de la bibliothèque standard pour les avertissements. (La bibliothèque standard est **`/W4`** propre, mais ne tente pas d’être **`/Wall`** nettoyée. De nombreux avertissements désactivés par défaut sont rarement bruyants et ne sont pas destinés à être utilisés régulièrement.)
- Amélioration des vérifications du débogage de `std::list`. Les itérateurs de liste vérifient désormais `operator->()`, et `list::unique()` marque maintenant les itérateurs comme non validés.
- Correction de la métaprogrammation de uses-allocator dans `tuple`.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- `std::partition` appelle maintenant le prédicat `N` au lieu de `N + 1` Times, comme le requiert la norme.
- Les tentatives pour éviter les statiques magic dans la version 15.3 ont été résolues dans la version 15.5.
- `std::atomic<T>` ne nécessite plus que `T` soit constructible par défaut.
- Les algorithmes de tas qui prennent un temps logarithmique se comportent différemment quand le débogage d’itérateur est activé. Ils n’effectuent plus d’assertion de temps linéaire indiquant que l’entrée est en fait un tas.
- `__declspec(allocator)` est maintenant protégé pour C1XX uniquement, afin d’éviter la génération d’avertissements par Clang qui ne comprend pas ce declspec.
- `basic_string::npos` est maintenant disponible comme constante au moment de la compilation.
- `std::allocator` en mode C++ 17 gère désormais correctement l’allocation des types sur-alignés, autrement dit des types dont l’alignement est supérieur à `max_align_t` , sauf s’ils sont désactivés par **`/Zc:alignedNew-`** .  Par exemple, des vecteurs d’objets avec un alignement de 16 ou de 32 octets sont désormais correctement alignés pour les instructions SSE et AVX.

### <a name="conformance-improvements"></a>Améliorations de la conformité

- Nous avons ajouté \<any\> , \<string_view\> , `apply()` , `make_from_tuple()` .
- Ajout \<optional\> de, de, de \<variant\> `shared_ptr::weak_type` et de \<cstdalign\> .
- Activé C++ 14 **`constexpr`** dans `min(initializer_list)` , `max(initializer_list)` , et `minmax(initializer_list)` , et `min_element()` , `max_element()` et `minmax_element()` .

Pour plus d’informations, consultez [table de conformité du langage Microsoft C++](./visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Plusieurs autres fonctionnalités C++17 ont été implémentées. Pour plus d’informations, consultez [table de conformité du langage Microsoft C++](cpp-conformance-improvements.md#improvements_153).
- Implémentation de P0602R0 « variant and optional should propagate copy/move triviality ».
- La bibliothèque standard tolère désormais officiellement la désactivation du RTTI dynamique via l’option [/GR-](../build/reference/gr-enable-run-time-type-information.md). `dynamic_pointer_cast()`Et `rethrow_if_nested()` **`dynamic_cast`** , par nature, nécessitent, de sorte que la bibliothèque standard les marque à présent comme `=delete` sous **`/GR-`** .
- Même lorsque le RTTI dynamique a été désactivé via **`/GR-`** , « RTTI statique » sous la forme de `typeid(SomeType)` est toujours disponible et alimente plusieurs composants de la bibliothèque standard. La bibliothèque standard prend désormais en charge la désactivation de cette fonctionnalité, via **`/D_HAS_STATIC_RTTI=0`** . Cet indicateur désactive également `std::any`, les fonctions membres `target()` et `target_type()` de `std::function`, et la fonction membre friend `get_deleter()` de `std::shared_ptr` et `std::weak_ptr`.
- La bibliothèque standard utilise désormais C++ 14 sans **`constexpr`** condition, au lieu de macros définies de façon conditionnelle.
- La bibliothèque standard utilise désormais les modèles d’alias en interne.
- La bibliothèque standard utilise désormais **`nullptr`** en interne, au lieu de `nullptr_t{}` . (L’utilisation interne de NULL a été supprimée. L’utilisation interne de 0-as-null est en cours de nettoyage progressif.)
- La bibliothèque standard utilise désormais `std::move()` en interne, au lieu d’une mauvaise utilisation de `std::forward()` du point de vue du style.
- `static_assert(false, "message")` a été changé en `#error message`. Cette modification permet d’améliorer les diagnostics du compilateur, car `#error` arrête immédiatement la compilation.
- La bibliothèque standard ne marque plus les fonctions en tant que `__declspec(dllimport)`. La technologie de l’éditeur de liens moderne ne requiert plus cela.
- Extraction de SFINAE dans des arguments de modèle par défaut, ce qui réduit l’encombrement par rapport aux types de retour et aux types d’arguments de fonction.
- Les vérifications de débogage dans \<random\> utilisent désormais les machines habituelles de la bibliothèque standard, au lieu de la fonction interne `_Rng_abort()` , qui est appelée `fputs()` à **stderr**. L’implémentation de cette fonction a été conservée pour la compatibilité binaire. Nous la supprimerons dans la prochaine version non compatible binaire de la bibliothèque standard.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- Plusieurs fonctionnalités de la bibliothèque standard ont été ajoutées, dépréciées ou supprimées selon la norme C++ 17. Pour plus d’informations, consultez [améliorations de la conformité de C++ dans Visual Studio](cpp-conformance-improvements.md#improvements_155).
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
- Les signatures pour les algorithmes parallèles suivants sont ajoutées mais non parallèles pour l’instant. Le profilage n’a montré aucun avantage pour les algorithmes de parallélisation qui déplacent uniquement les éléments de déplacement ou de permutation :
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

Pour plus d’informations, consultez [table de conformité du langage Microsoft C++](./visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Correctifs de performance et de débit

- Modification des surcharges `basic_string::find(char)` pour appeler `traits::find` une seule fois. Auparavant, cela était implémenté comme une recherche de chaîne générale d’une chaîne de longueur 1.
- `basic_string::operator==` vérifie désormais la taille de la chaîne avant de comparer le contenu des chaînes.
- Suppression du couplage des contrôles dans `basic_string`, qui rendait difficile l’analyse par l’optimiseur du compilateur. Pour toutes les chaînes courtes, l’appel de `reserve` a toujours un coût non nul pour ne rien faire.
- `std::vector` a été repensée pour l’exactitude et les performances : l’utilisation d’alias pendant les opérations Insert et emplace est maintenant correctement gérée comme requis par la norme, la garantie d’exception forte est désormais fournie quand elle est requise par la norme via `move_if_noexcept()` et d’autres logiques, et INSERT et emplace effectuent moins d’opérations d’éléments.
- La bibliothèque C++ standard évite désormais de déréférencer les pointeurs fantômes Null.
- Amélioration des performances de `weak_ptr::lock()`.
- Pour augmenter le débit du compilateur, les en-têtes de la bibliothèque C++ standard évitent désormais d’inclure des déclarations de fonctions intrinsèques de compilateur inutiles.
- Amélioration d’un facteur supérieur à 3 des performances des constructeurs de déplacement `std::string` et `std::wstring`.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- A fonctionné autour des interactions avec **`noexcept`** , ce qui a empêché l’incorporation de l' `std::atomic` implémentation dans des fonctions qui utilisent la gestion structurée des exceptions (SEH).
- Modification de la fonction `_Deallocate()` interne de la bibliothèque standard pour l’optimiser en un code plus petit, ce qui lui permet d’être incorporée dans plus d’emplacements.
- Modification de `std::try_lock()` pour l’utilisation de l’expansion de package à la place de la récurrence.
- Amélioration de l’algorithme de prévention de blocage `std::lock()` pour l’utilisation d’opérations `lock()` au lieu d’effectuer une rotation sur `try_lock()` pour tous les verrous.
- Activation de l’optimisation de la valeur de retour nommée dans `system_category::message()`.
- `conjunction` et `disjunction` maintenant instancier `N + 1` des types, plutôt que des `2N + 2` types.
- `std::function` n’instancie plus le mécanisme de prise en charge des allocateurs pour chaque type-erased pouvant être appelé, améliorant le débit et réduisant la taille des fichiers .obj dans les programmes qui passent beaucoup d’expressions lambda distinctes à `std::function`.
- `allocator_traits<std::allocator>` contient des opérations `std::allocator` incorporées manuellement, ce qui réduit la taille du code dans le code qui interagit avec `std::allocator` via `allocator_traits` uniquement (autrement dit, dans la plupart du code).
- L’interface d’allocateur minimale C++11 est désormais gérée directement par l’allocateur appelant de la bibliothèque standard `allocator_traits`, au lieu d’inclure l’allocateur dans une classe interne `_Wrap_alloc`. Ce changement réduit la taille du code généré pour la prise en charge de l’allocateur, améliore la capacité de l’optimiseur à traiter les conteneurs de la bibliothèque standard dans certains cas, et fournit une meilleure expérience de débogage (car vous voyez désormais votre type d’allocateur, au lieu de `_Wrap_alloc<your_allocator_type>` dans le débogueur).
- Suppression de la programmation de `allocator::reference` la personnalisation, que les allocateurs ne sont pas autorisés à personnaliser. (Les allocateurs peuvent demander aux conteneurs d’utiliser des pointeurs fantaisistes mais pas des références fantaisistes.)
- Le serveur frontal du compilateur a appris à désencapsuler les itérateurs de débogage dans des opérations for-loops basées sur plage, pour améliorer les performances des versions de débogage.
- Le chemin shrink interne de `basic_string` pour `shrink_to_fit()` et `reserve()` n’est plus dans le chemin des opérations de réallocation, réduisant la taille du code pour tous les membres en mutation.
- Le chemin grow interne de `basic_string` n’est plus dans le chemin de `shrink_to_fit()`.
- Les opérations de mutation de `basic_string` sont désormais incluses dans les fonctions de chemin rapide de non-allocation et de chemin lent d’allocation, rendant plus probable l’incorporation du cas no-reallocate fréquent dans les appelants.
- Les `basic_string` opérations de mutation créent désormais des tampons réalloués dans l’État par défaut plutôt que de les redimensionner sur place. Par exemple, une instruction INSERT au début d’une chaîne déplace maintenant le contenu après l’insertion exactement une fois. Elle est déplacée vers le dessous ou vers la mémoire tampon nouvellement allouée. Elle n’est plus déplacée deux fois dans le cas de réallocation, d’abord vers la mémoire tampon qui vient d’être allouée, puis inversée.
- Les opérations appelant la bibliothèque standard C dans prennent \<string\> maintenant en cache l' `errno` adresse pour supprimer l’interaction répétée avec TLS.
- Simplification de l’implémentation de `is_pointer`.
- Fin de la modification de l’expression SFINAE basée sur une fonction vers **`struct`** et `void_t` basé sur.
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
- L’initialisation thread-safe des statiques locales a été automatiquement désactivée dans l’ensemble d’outils XP lors de l’utilisation d’ATL pour générer une DLL. Ce n’est pas le moment. Vous pouvez ajouter **`/Zc:threadSafeInit-`** dans les paramètres de votre projet si vous ne souhaitez pas l’initialisation thread-safe.

### <a name="visual-c-runtime"></a>Runtime Visual C++

- Nouvel en-tête « cfguard.h » pour les symboles de protection de flux de contrôle.

## <a name="visual-studio-2017-c-ide"></a>IDE Visual Studio 2017 C++

- Les performances des modifications de configuration sont désormais meilleures pour les projets natifs C++ et bien meilleures pour les projets C++/CLI. Quand une configuration de solution est activée pour la première fois, elle est désormais plus rapide et toutes les activations suivantes de cette configuration de solution sont presque instantanées.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Plusieurs Assistants de projet et de code ont été réécrits pour refléter le style particulier des boîtes de dialogue.
- **Ajouter une classe** lance désormais l’Assistant Ajouter une classe directement. Tous les autres éléments qui se trouvaient déjà ici sont maintenant disponibles sous **Ajouter > Nouvel élément**.
- Les projets Win32 se trouvent désormais sous la catégorie **Windows Desktop** dans la boîte de dialogue **nouveau projet** .
- La **console Windows** et les modèles d' **application de bureau** créent désormais les projets sans afficher d’Assistant. Il existe un nouvel **Assistant Windows Desktop** sous la même catégorie, qui affiche les mêmes options que l’ancien **Assistant Console Win32**.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Plusieurs opérations C++ qui utilisent le moteur IntelliSense pour la refactorisation et la navigation dans le code s’exécutent beaucoup plus rapidement. Les valeurs suivantes sont basées sur la solution Visual Studio Chromium avec 3 500 projets :

| Fonctionnalité | Amélioration des performances |
|--|--|
| Renommer | x 5,3 |
| Changer la signature | x 4,5 |
| Rechercher toutes les références | x 4,7 |

C++ prend maintenant en charge la fonctionnalité **Atteindre la définition** avec Ctrl+clic, ce qui permet un accès rapide aux définitions à l’aide de la souris. Le visualiseur de structure du pack Productivity Power Tools est également inclus dans le produit par défaut.

## <a name="intellisense"></a>IntelliSense

- Le nouveau moteur de base de données SQLite est désormais celui utilisé par défaut. Le nouveau moteur accélère les opérations de base de données comme **atteindre la définition** et **Rechercher toutes les références**. Cela améliore considérablement le temps d’analyse de la solution initiale. Le paramètre a été déplacé vers **outils > Options > éditeur de texte > C/C++ > avancé**. (Anciennement sous... C/C++ > expérimental.)

- Nous avons amélioré les performances d’IntelliSense dans les projets et fichiers qui n’utilisent pas d’en-têtes précompilés : un en-tête précompilé automatique est créé pour les en-têtes du fichier en cours.

- Nous avons ajouté une fonctionnalité de filtrage des erreurs et une aide pour les erreurs IntelliSense figurant dans la liste d’erreurs. Le fait de cliquer sur la colonne d’erreur permet maintenant un filtrage. De plus, en cliquant sur une erreur spécifique ou sur F1, une recherche en ligne est lancée sur le message d’erreur concerné.

  ![Liste d'erreurs](media/ErrorList1.png "Liste d'erreurs")

  ![Liste d’erreurs filtrée](media/ErrorList2.png "Liste d’erreurs filtrée")

- Ajout de la possibilité de filtrer les éléments de la liste des membres par type.

  ![Filtrage de la liste des membres](media/mlfiltering.png "Filtrage de la liste des membres")

- Ajout d’une nouvelle fonctionnalité IntelliSense prédictive expérimentale qui fournit un filtrage en fonction du contexte de ce qui apparaît dans la liste des membres. Pour plus d’informations, consultez [C++ IntelliSense Improvements - Predictive IntelliSense & Filtering](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- **Rechercher toutes les références** (Maj + F12) vous aide maintenant à vous retrouver facilement, même dans des codes base complexes. Elle offre des options avancées de regroupement, de filtrage, de tri, de recherche dans les résultats et (pour certains langages) la colorisation, ce qui vous permet d’avoir une vision claire de vos références. Pour C++, la nouvelle interface utilisateur inclut des informations indiquant si nous lisons ou si nous écrivons dans une variable.
- La fonctionnalité IntelliSense Point par flèche a été changée de « expérimentale » en « avancée » et elle est maintenant activée par défaut. Les fonctionnalités de l’éditeur **développer les étendues** et **développer la priorité** ont également été déplacées de expérimentale à avancé.
- Les fonctionnalités de refactorisation expérimentales **modifient la signature** et l' **extraction de fonction** sont désormais disponibles par défaut.
- Ajout de la fonctionnalité expérimentale « Chargement accéléré des projets » pour les projets C++. La prochaine fois que vous ouvrirez un projet C++, celui-ci sera chargé plus rapidement, et la fois suivante *beaucoup* plus rapidement.
- Certaines de ces fonctionnalités sont communes à d’autres langages, et certaines sont spécifiques à C++. Pour plus d’informations sur ces nouvelles fonctionnalités, consultez [Announcing Visual Studio "15" Preview 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

- Ajout de la prise en charge de ClangFormat. Pour plus d’informations, consultez [ClangFormat Support in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projets non MSBuild avec Ouvrir le dossier

Visual Studio 2017 introduit la fonctionnalité **ouvrir le dossier** . Elle vous permet de coder, de générer et de déboguer dans un dossier contenant du code source sans avoir à créer de solution ou de projet. Il est maintenant beaucoup plus simple de bien démarrer avec Visual Studio, même si votre projet n’est pas un projet MSBuild. **Ouvrir un dossier** vous donne accès à de puissantes fonctionnalités de compréhension du code, de modification, de génération et de débogage. Ils sont identiques à ceux que Visual Studio fournit déjà pour les projets MSBuild. Pour plus d’informations, consultez [Projets Dossier ouvert pour C++](../build/open-folder-projects-cpp.md).

- Améliorations de l’expérience de la fonctionnalité Ouvrir le dossier. Vous pouvez personnaliser l’expérience via ces fichiers .json :
  - CppProperties.json pour personnaliser l’expérience IntelliSense et l’expérience de navigation.
  - Tasks.json pour personnaliser les étapes de la génération.
  - Launch.json pour personnaliser l’expérience du débogage.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Amélioration de la prise en charge d’autres compilateurs et environnements de génération tels que MinGW et Cygwin. Pour plus d’informations, consultez [Using MinGW and Cygwin with Visual C++ and Open Folder](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Ajout de la prise en charge de la définition de variables d’environnement globales et spécifiques à la configuration dans CppProperties.json et CMakeSettings.json. Ces variables d’environnement peuvent être consommées par des configurations de débogage définies dans launch.vs.json et des tâches dans tasks.vs.json. Pour plus d’informations, consultez [Customizing your Environment with Visual C++ and Open Folder](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Amélioration de la prise en charge du générateur Ninja de CMake, y compris la possibilité de facilement cibler des plateformes 64 bits.

## <a name="cmake-support-via-open-folder"></a>Prise en charge de CMake via Ouvrir le dossier

Visual Studio 2017 introduit la prise en charge de l’utilisation de projets CMake sans les convertir en fichiers projet MSBuild (.vcxproj). Pour plus d’informations, consultez [Projets CMake dans Visual Studio](../build/cmake-projects-in-visual-studio.md). L’ouverture de projets CMake avec **ouvrir un dossier** configure automatiquement l’environnement pour la modification, la génération et le débogage en C++.

- IntelliSense pour C++ fonctionne sans qu’il soit nécessaire de créer un fichier CppProperties.json dans le dossier racine. Nous avons également ajouté une nouvelle liste déroulante pour permettre aux utilisateurs de basculer facilement entre les configurations fournies par les fichiers CMake et CppProperties.json.

- Des options de configuration supplémentaires sont prises en charge via un fichier CMakeSettings.json qui se trouve dans le même dossier que le fichier CMakeLists.txt.

  ![CMake ouvrir le dossier](media/cmake-cpp.png "CMake ouvrir le dossier")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Ajout de la prise en charge du générateur Ninja de CMake.

##### <a name="visual-studio-2017-version-154"></a>Visual Studio 2017 version 15.4

- Ajout de la prise en charge de l’importation des caches CMake existants.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- Ajout de la prise en charge de CMake 3.11, analyse du code dans les projets CMake, vue des cibles dans l’Explorateur de solutions, options de génération du cache et compilation de fichier unique. Pour plus d’informations, consultez [CMake Support in Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) et [Projets CMake en Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development"></a>Développement du Bureau Windows

Nous fournissons à présent une expérience d’installation plus fine pour la charge de travail C++ d’origine. Nous avons ajouté des composants sélectionnables qui vous permettent d’installer uniquement les outils dont vous avez besoin. Les tailles d’installation indiquées pour les composants répertoriés dans l’interface utilisateur du programme d’installation sont incorrectes et sous-estiment la taille totale.

Pour créer correctement des projets Win32 dans la charge de travail de bureau C++, vous devez installer un ensemble d’outils et un SDK Windows. Installez les composants recommandés (sélectionnés) **Ensemble d’outils VC++ 2017 v141 (x86,x64)** et **SDK Windows 10 (10.0.nnnnn)** pour assurer le bon fonctionnement. Si les outils nécessaires ne sont pas installés, les projets ne seront pas créés correctement et l’Assistant ne répondra plus.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Visual C++ Build Tools (disponible jusqu’ici comme produit autonome) est désormais fourni en tant que charge de travail dans Visual Studio Installer. Cette charge de travail installe uniquement les outils nécessaires pour générer des projets C++ sans installer l’IDE de Visual Studio. Les deux ensembles d’outils v140 et v141 sont inclus. L’ensemble d’outils v141 contient les dernières améliorations de Visual Studio 2017 version 15.5. Pour plus d’informations, consultez [Visual Studio Build Tools now include the VS2017 and VS2015 MSVC Toolsets](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Développement Linux avec C++

L’extension populaire [Visual C++ pour le développement Linux](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.VisualCforLinuxDevelopment) fait désormais partie de Visual Studio. Cette installation fournit tout ce dont vous avez besoin pour développer et déboguer des applications C++ exécutées dans un environnement Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 version 15.2

Des améliorations ont été apportées au partage de code multiplateforme et à la visualisation des types. Pour plus d’informations, consultez [Linux C++ improvements for cross-platform code sharing and type visualization](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- La charge de travail Linux a ajouté la prise en charge de la **synchronisation** d’accès en tant qu’alternative à **SFTP** pour la synchronisation des fichiers sur des machines Linux distantes.
- La compilation croisée ciblant les microcontrôleurs ARM est maintenant prise en charge. Pour activer cette fonctionnalité dans l’installation, choisissez la charge de travail **Développement Linux en C++** et sélectionnez l’option **Développement embarqué et IoT**. Cette option ajoute les outils de compilation croisée GCC ARM à votre installation. Pour plus d’informations, consultez [ARM GCC Cross Compilation in Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- La prise en charge de CMake a été améliorée. Vous pouvez maintenant utiliser votre base de code CMake existante sans avoir à la convertir en projet Visual Studio. Pour plus d’informations, consultez [Configurer un projet CMake Linux](../linux/cmake-linux-project.md).
- La prise en charge de l’exécution de tâches distantes a été améliorée. Cette fonctionnalité vous permet d’exécuter n’importe quelle commande sur un système distant défini dans le gestionnaire de connexions de Visual Studio. Avec les tâches distantes, vous pouvez également copier des fichiers sur le système distant.
Pour plus d’informations, consultez [Configurer un projet CMake Linux](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

- Diverses améliorations apportées aux scénarios de charge de travail Linux. Pour plus d’informations, consultez [Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- IntelliSense pour les en-têtes sur les connexions à distance en-tête Linux. Pour plus d’informations, consultez [IntelliSense for Remote Linux Headers](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) et [Configurer un projet CMake Linux](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Développement de jeux avec C++

Utilisez toute la puissance de C++ pour créer des jeux professionnels reposant sur DirectX ou Cocos2d.

## <a name="mobile-development-with-c-for-android-and-ios"></a>Développement mobile en C++ pour Android et iOS

Vous pouvez désormais créer et déboguer des applications mobiles, à l’aide de Visual Studio, capables de cibler Android et iOS.

## <a name="universal-windows-apps"></a>Applications de la plateforme Windows universelle

C++ est fourni sous forme de composant facultatif pour la charge de travail Application Windows universelle. Actuellement, vous devez mettre à niveau les projets C++ manuellement. Vous pouvez ouvrir un projet de plateforme Windows universelle ciblé V140 dans Visual Studio 2017. Toutefois, vous devez sélectionner l’ensemble d’outils de plateforme V141 dans les pages de propriétés du projet si Visual Studio 2015 n’est pas installé.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nouvelles options pour C++ sur la plateforme Windows universelle (UWP)

Vous disposez maintenant de nouvelles options pour l’écriture et l’empaquetage d’applications C++ pour le plateforme Windows universelle et le Windows Store : l’infrastructure de pont de bureau vous permet de créer un package pour votre application de bureau existante ou votre objet COM pour le déploiement via le Windows Store. Ou, pour le déploiement via vos canaux existants via le chargement indépendant. Les nouvelles fonctionnalités de Windows 10 vous permettent d’ajouter une plateforme universelle Windows (UWP) à votre application de bureau de différentes manières. Pour plus d’informations, consultez [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Un modèle de **projet de création de packages d’application Windows** a été ajouté et facilite considérablement l’empaquetage d’applications de bureau à l’aide de Desktop Bridge. Cette fonctionnalité est disponible sous **Fichier | Nouveau | Projet | Installé | Visual C++ | Plateforme Windows universelle**. Pour plus d’informations, consultez [Empaqueter une application à l’aide de Visual Studio (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Lors de l’écriture de nouveau code, vous pouvez désormais utiliser C++/WinRT, une projection de langage C++ standard pour Windows Runtime (WinRT) implémentée uniquement dans les fichiers d’en-tête. Elle vous permet de consommer et de créer des API Windows Runtime à l’aide d’un compilateur C++ conforme aux normes. C++/WinRT est conçu pour offrir aux développeurs C++ un accès idéal à l’API Windows moderne. Pour plus d’informations, consultez [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/).

À partir de la build 17025 du SDK Windows Insider Preview, C++/WinRT est inclus dans le SDK Windows. Pour plus d’informations, consultez [C++/WinRT is now included the Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="the-clangc2-platform-toolset"></a>Ensemble d’outils de plateforme Clang/C2

L’ensemble d’outils Clang/C2 fourni avec Visual Studio 2017 prend désormais en charge le **`/bigobj`** commutateur, ce qui est essentiel pour la création de projets volumineux. Il comprend également plusieurs correctifs de bogues importants, à la fois dans le frontal et le back-end du compilateur.

## <a name="c-code-analysis"></a>Analyse du code C++

Les vérificateurs principaux C++ permettant d’appliquer les [directives principales C++](https://github.com/isocpp/CppCoreGuidelines) sont désormais distribués avec Visual Studio. Activez les contrôleurs dans la page extensions de l' **analyse du code** des pages de propriétés du projet. Les extensions sont alors incluses lorsque vous exécutez l’analyse du code. Pour plus d’informations, consultez [Using the C++ Core Guidelines checkers](../code-quality/using-the-cpp-core-guidelines-checkers.md).

![Capture d’écran de la boîte de dialogue pages de propriétés qui affiche les propriétés de configuration > l’analyse du code > général sélectionnée et un certain nombre de contrôles principaux figurant dans la section exécuter cet ensemble de règles.](media/CppCoreCheck.png "Page de propriétés CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Ajout de la prise en charge des règles liées à la gestion de ressources.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

- Les nouvelles vérifications de C++ Core Guidelines couvrent l’exactitude du pointeur intelligent, l’utilisation correcte des initialiseurs globaux et le marquage des utilisations des constructions comme **`goto`** et des casts incorrects.

- Certains numéros d’avertissement utilisés dans la version 15.3 ont été supprimés dans la version 15.5. Ces avertissements ont été remplacés par des vérifications plus spécifiques.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 version 15.6

- Ajout de la prise en charge de l’analyse de fichier unique et amélioration des performances d’analyse au moment de l’exécution. Pour plus d’informations, consultez [C++ Static Analysis Improvements for Visual Studio 2017 15.6 Preview 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

- Prise en charge ajoutée pour [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md) , qui vous permet de spécifier les règles d’analyse du code à exécuter.
- Ajout de la prise en charge de règles C++ Core Guidelines supplémentaires.  Pour plus d’informations, consultez [Using the C++ Core Guidelines checkers](../code-quality/using-the-cpp-core-guidelines-checkers.md).

## <a name="unit-testing-in-visual-studio-2017"></a>Tests unitaires dans Visual Studio 2017

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 version 15.5

Les adaptateurs de Google Test et Boost. test sont désormais disponibles en tant que composants de la charge de travail **développement Desktop en C++** . Ils sont intégrés à l' **Explorateur de tests**. La prise en charge de CTest est ajoutée pour les projets CMake (à l’aide d’un dossier ouvert), bien que l’intégration complète avec l' **Explorateur de tests** ne soit pas encore disponible. Pour plus d’informations, consultez [écriture de tests unitaires pour C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 version 15.6

- Prise en charge ajoutée pour la `Boost.Test` prise en charge de bibliothèque dynamique.
- Un `Boost.Test` modèle d’élément est désormais disponible dans l’IDE.

Pour plus d’informations, consultez [ `Boost.Test` tests unitaires : prise en charge des bibliothèques dynamiques et nouveau modèle d’élément](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 version 15.7

Ajout de la prise en charge de [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) pour les projets de test unitaire C++. Pour plus d’informations, consultez [Announcing CodeLens for C++ Unit Testing](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio Graphics Diagnostics

Outils Visual Studio Graphics Diagnostics : vous pouvez les utiliser pour enregistrer et analyser les problèmes de rendu et de performances dans les applications Direct3D. Utilisez-les sur les applications qui s’exécutent localement sur votre PC Windows, dans un émulateur d’appareil Windows, ou sur un PC ou un appareil distant.

- **Sortie de & d’entrée pour les nuanceurs vertex et Geometry :** La possibilité d’afficher l’entrée et la sortie des nuanceurs de sommets et des nuanceurs de géométrie a été l’une des fonctionnalités les plus demandées. Il est désormais pris en charge dans les outils. Sélectionnez l’étape VS ou GS dans la vue étapes du pipeline pour commencer l’inspection de son entrée et de sa sortie dans le tableau ci-dessous.

  ![Entrées/sorties pour les nuanceurs](media/io-shaders.png)

- **Recherche et filtrage dans la table des objets :** fournit un moyen rapide et facile de trouver les ressources que vous recherchez.

  ![Capture d’écran de la section table objet avec la liste déroulante type et la zone de texte Rechercher appelée out.](media/search.png)

- **Historique des ressources :** cette nouvelle vue offre une façon simplifiée d’afficher tout l’historique des modifications d’une ressource utilisée pendant le rendu d’un frame capturé. Pour appeler l’historique d’une ressource, cliquez sur l’icône d’horloge en regard de n’importe quel lien hypertexte de ressource.

  ![Historique des ressources](media/resource-history.png)

  Elle affiche la fenêtre outil **historique des ressources** , remplie avec l’historique des modifications de la ressource.

  ![Modification de l’historique des ressources](media/resource-history-change.png)

  Vous pouvez capturer des frames avec la capture de pile des appels complète activée. Cela vous permet de déduire rapidement le contexte de chaque événement de modification et de l’inspecter dans votre projet Visual Studio. Définissez l’option capture de pile complète dans la boîte de dialogue **options de > des outils** Visual Studio sous **Graphics Diagnostics**.

- **Statistiques d’API :** affichez une synthèse générale de l’utilisation des API dans votre frame. Il est pratique de découvrir des appels que vous n’êtes pas en train de faire, ou les appels que vous faites trop souvent. Cette fenêtre est disponible via **afficher > statistiques des API** dans Visual Studio Graphics Analyzer.

  ![Statistiques d’API](media/api-stats.png)

- **Statistiques de la mémoire :** Affichez la quantité de mémoire allouée par le pilote pour les ressources que vous créez dans le frame. Cette fenêtre est disponible via **afficher les statistiques de la mémoire >** dans **Visual Studio Graphics Analyzer**. Pour copier des données dans un fichier CSV pour les afficher dans une feuille de calcul, cliquez avec le bouton droit et choisissez **copier tout**.

  ![Statistiques de la mémoire](media/memory-stats.png)

- **Validation du frame :** la nouvelle liste d’erreurs et d’avertissements facilite la navigation dans votre liste d’événements basée sur les éventuels problèmes détectés par la couche de débogage Direct3D. Cliquez sur **afficher > validation du frame** dans Visual Studio Graphics Analyzer pour ouvrir la fenêtre. Cliquez ensuite sur **Exécuter la validation** pour commencer l’analyse. L’opération peut prendre plusieurs minutes, selon la complexité du frame.

  ![Validation du frame](media/frame-validation.png)

- **Analyse des frames pour D3D12 :** Utilisez l’analyse des frames pour analyser les performances des appels de dessin avec des expériences « simulations » redirigées. Basculez vers l’onglet Analyse des frames et lancez l’analyse pour afficher le rapport. Pour plus d’informations, regardez la vidéo [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool).

  ![Analyse des frames](media/frame-analysis.png)

- **Améliorations de l’utilisation du GPU :** Les traces ouvertes peuvent être effectuées via le profileur d’utilisation du GPU Visual Studio avec la vue GPU ou l’outil Windows Performance Analyzer (WPA) pour une analyse plus détaillée. Si Windows performance Toolkit est installé, il existe deux liens hypertexte : un pour WPA et un autre pour la vue GPU, en bas à droite de la vue d’ensemble de la session.

  ![Utilisation du GPU](media/gpu-usage.png)

  Les traces que vous ouvrez dans la vue GPU par le biais de ce lien prennent en charge le zoom et le panoramique des chronologies synchronisées et de la vue GPU. Une case à cocher dans VS contrôle si la synchronisation est activée ou non.

  ![Mode GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=msvc-140"

Pour obtenir la liste complète des nouveautés jusqu’à Visual Studio 2015, Update 3, consultez [Visual C++ What’s New 2003 through 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

Pour plus d’informations sur les nouveautés de Visual Studio 2015, consultez les notes de publication. Elles sont liées à partir de [l’historique des notes de publication de Visual Studio 2015](/visualstudio/releasenotes/vs2015-version-history).

Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2019, consultez [Nouveautés de c++ dans Visual studio 2019](?preserve-view=true&view=msvc-160).

Pour plus d’informations sur les nouveautés de C++ dans Visual Studio 2017, consultez [Nouveautés de C++ dans Visual Studio 2017](?preserve-view=true&view=msvc-150).

::: moniker-end
