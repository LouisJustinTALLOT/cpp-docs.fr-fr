---
title: Utilisation des vérificateurs C++ Core Guidelines
description: Comment configurer et utiliser les règles d’analyse du code Microsoft C++ pour C++ Core Guidelines.
ms.date: 07/27/2020
ms.topic: conceptual
dev_langs:
- CPP
ms.openlocfilehash: 4fb06b0f78c93e6b76e0b8d64d7dfbdc541cf299
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334141"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Utiliser les vérificateurs de C++ Core Guidelines

Les C++ Core Guidelines sont un ensemble portable d’instructions, de règles et de meilleures pratiques concernant le codage en C++ créé par les experts et les concepteurs C++. Visual Studio prend actuellement en charge un sous-ensemble de ces règles dans le cadre de ses outils d’analyse du code pour C++. Les contrôleurs d’instructions de base sont installés par défaut dans Visual Studio 2017 et Visual Studio 2019. Ils sont [disponibles sous la forme d’un package NuGet pour Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Projet C++ Core Guidelines

Créé par Bjarne Stroustrup et d’autres, les C++ Core Guidelines sont un guide d’utilisation du C++ moderne en toute sécurité et de manière efficace. Les directives insistent sur la sécurité des types statiques et la sécurité des ressources. Ils identifient les moyens d’éliminer ou de réduire les parties les plus sujettes aux erreurs du langage. Ils indiquent également comment rendre votre code plus simple, plus fiable et plus performant. Ces recommandations sont gérées par la base C++ standard. Pour plus d’informations, consultez la documentation, [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)et accéder aux fichiers de projet de documentation C++ Core Guidelines sur [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Activer les instructions de C++ Core Check dans l’analyse du code

::: moniker range="<=msvc-150"

Un sous-ensemble de règles de C++ Core Check est inclus dans l’ensemble de règles Microsoft Native recommended. C’est le RuleSet qui s’exécute par défaut lorsque l’analyse du code est activée.

### <a name="to-enable-code-analysis-on-your-project"></a>Pour activer l’analyse du code sur votre projet

1. Ouvrez la boîte de dialogue  **pages de propriétés** de votre projet.

1. Sélectionnez la page de propriétés **configuration** de l' > **analyse du code** .

1. Cochez la case **activer l’analyse du code sur la build** .

![Page de propriétés pour les paramètres généraux de l’analyse du code](media/cppcorecheck_codeanalysis_general.png)

Pour activer des règles de contrôle de noyau supplémentaires, ouvrez la liste déroulante et choisissez les ensembles de règles que vous souhaitez inclure :

![Liste déroulante pour les ensembles de règles de C++ Core Check supplémentaires](media/cppcorecheck_codeanalysis_extensions.png)

::: moniker-end
::: moniker range=">=msvc-160"

Un sous-ensemble de règles de C++ Core Check est inclus dans l’ensemble de règles Microsoft Native recommended. C’est le RuleSet qui s’exécute par défaut lorsque Microsoft Code Analysis est activé.

### <a name="to-enable-code-analysis-on-your-project"></a>Pour activer l’analyse du code sur votre projet :

1. Ouvrez la boîte de dialogue  **pages de propriétés** de votre projet.

1. Sélectionnez la page de propriétés **configuration** de l' > **analyse du code** .

1. Définissez les propriétés **activer l’analyse du code sur la build** et activer l’analyse du **code Microsoft** .

Vous pouvez également choisir d’exécuter toutes les règles de C++ Core Check prises en charge ou de sélectionner votre propre sous-ensemble à exécuter :

### <a name="to-enable-additional-core-check-rules"></a>Pour activer des règles de contrôle de base supplémentaires

1. Ouvrez la boîte de dialogue  **pages de propriétés** de votre projet.

1. Sélectionnez la page de propriétés données de **configuration** > **analyse du code** > **Microsoft** .

1. Ouvrez la liste déroulante **règles actives** et sélectionnez **choisir plusieurs ensembles de règles**.

1. Dans la boîte de dialogue **Ajouter ou supprimer des ensembles de règles** , choisissez les ensembles de règles que vous souhaitez inclure.

::: moniker-end

## <a name="examples"></a>Exemples

Voici un exemple de certains problèmes que les règles de C++ Core Check peuvent trouver :

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

Cet exemple illustre quelques-uns des avertissements que les règles de C++ Core Check peuvent trouver :

- C26494 est de type règle. 5 : Initialise toujours un objet.

- C26485 est une limite de règle. 3 : aucune atténuation de tableau à pointeur.

- C26481 est une limite de règle. 1 : n’utilisez pas l’arithmétique de pointeur. Utilisez `span` à la place.

Installez et activez les ensembles de règles d’analyse du code C++ Core Check, puis compilez ce code. L’analyse du code génère les deux premiers avertissements et supprime le troisième. Voici la sortie de la génération de l’exemple de code dans Visual Studio 2015 :

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Les C++ Core Guidelines sont là pour vous aider à écrire du code plus sécurisé. Toutefois, il se peut que vous trouviez une instance dans laquelle une règle ou un profil ne doit pas être appliqué. Il est facile de le supprimer directement dans le code. Vous pouvez utiliser l' `[[gsl::suppress]]` attribut pour empêcher C++ Core Check de détecter et de signaler toute violation d’une règle dans le bloc de code suivant. Vous pouvez marquer des instructions individuelles pour supprimer des règles spécifiques. Vous pouvez même supprimer le profil de limites entier en écrivant `[[gsl::suppress(bounds)]]` sans inclure un numéro de règle spécifique.

## <a name="supported-rule-sets"></a>Ensembles de règles pris en charge

À mesure que de nouvelles règles sont ajoutées à l’outil de vérification de C++ Core Guidelines, le nombre d’avertissements produits pour le code préexistant peut augmenter. Vous pouvez utiliser des ensembles de règles prédéfinis pour filtrer les genres de règles à activer. Vous trouverez des Articles de référence pour la plupart des règles sous [Visual Studio C++ Core Check référence](code-analysis-for-cpp-corecheck.md).

- **Règles arithmétiques** : règles de détection des [dépassements](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow)arithmétiques, [des opérations non](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned)signées et des [manipulations de bits](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative). <sup>15,6</sup>

- **Règles de limites** : appliquez le [profil de limites de l’C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile). <sup>15,3</sup>

- **Règles de classe** : quelques règles qui se concentrent sur l’utilisation correcte des fonctions membres spéciales et des spécifications virtuelles. Il s’agit d’un sous-ensemble des vérifications recommandées pour les [classes et les hiérarchies](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class)de classes. <sup>15,5</sup>

- **Règles de concurrence** : une seule règle, qui intercepte les déclarations d’objet de protection incorrectes. Pour plus d’informations, consultez [instructions relatives à l’accès concurrentiel](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency). <sup>15,5</sup>

- **Règles const** : appliquez [les vérifications liées à const à partir de la C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability). <sup>15,3</sup>

- **Règles de déclaration** : deux règles des instructions des [interfaces](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) qui se concentrent sur la façon dont les variables globales sont déclarées. <sup>15,5</sup>

- **Règles d’énumération** : ces règles appliquent [des vérifications relatives aux énumérations à partir du C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum). <sup>16,3</sup>

- **Règles expérimentales** Il s’agit de règles de C++ Core Check expérimentales qui sont utiles, mais qui ne sont pas prêtes pour une utilisation quotidienne. Essayez-les et [fournissez vos commentaires](https://aka.ms/feedback/suggest?space=62). <sup>16,0</sup>

- **Règles de fonction** : deux contrôles qui facilitent l’adoption du **`noexcept`** spécificateur. Elles font partie des instructions relatives à la conception et à l’implémentation de la [fonction Clear](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions). <sup>15,5</sup>

- **Règles GSL** : ces règles appliquent les vérifications liées à la [bibliothèque de prise en charge des instructions à partir de la C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl). <sup>15,7</sup>

- **Règles de durée de vie** : ces règles appliquent le [profil de durée de vie du C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile). <sup>15,7</sup>

- **Règles du pointeur propriétaire** : applique [les vérifications de gestion des ressources liées au propriétaire \<T> à partir de la C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). <sup> 15,3</sup>

- **Règles de pointeur brut** : appliquez [les vérifications de gestion des ressources liées aux pointeurs bruts à partir du C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). <sup>15,3</sup>

- **Règles de pointeur partagé** : elles font partie de l’application des instructions de [gestion des ressources](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) . <sup>15,5</sup> nous avons ajouté quelques règles spécifiques à la façon dont les pointeurs partagés sont passés dans des fonctions ou utilisés localement.

- **Règles STL** : ces règles appliquent les vérifications liées à la [bibliothèque standard C++ (STL) à partir de la C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib). <sup>15,7</sup>

- **Règles de style** : un contrôle simple mais important, qui interdit l’utilisation de [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). <sup>15,5</sup> il s’agit de la première étape pour améliorer votre style de codage et l’utilisation des expressions et des instructions en C++.

- **Règles de type** : appliquez le [profil de type du C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile). <sup>15,3</sup>

- **Règles de pointeur uniques** : appliquez [les vérifications de gestion des ressources liées aux types avec une sémantique de pointeur unique à partir de la C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). <sup>15,3</sup>

- **Règles de C++ Core Check** : cet ensemble de règles contient toutes les vérifications actuellement implémentées du [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines), à l’exception des règles expérimentales.

<sup>15,3</sup> ces règles sont d’abord apparues dans Visual Studio 2017 version 15,3 \
<sup>15,5</sup> ces règles sont d’abord apparues dans Visual Studio 2017 version 15,5 \
<sup>15,6</sup> ces règles sont d’abord apparues dans Visual Studio 2017 version 15,6 \
<sup>15,7</sup> ces règles sont d’abord apparues dans Visual Studio 2017 version 15,7 \
<sup>16,0</sup> ces règles sont d’abord apparues dans Visual Studio 2019 version 16,0 \
<sup>16,3</sup> ces règles sont d’abord apparues dans Visual Studio 2019 version 16,3

Vous pouvez choisir de limiter les avertissements à un seul ou à quelques groupes. Les ensembles de règles natifs **minimum** et **natif recommandés** incluent des règles de C++ Core Check et d’autres vérifications prérapides.

::: moniker range="<=msvc-150"

Pour afficher les ensembles de règles disponibles, ouvrez la boîte de dialogue **Propriétés du projet** . Dans la boîte de dialogue **pages de propriétés** , sélectionnez la page **Propriétés de configuration** général de l'  >  **analyse du code**  >  **General** . Ensuite, ouvrez la liste déroulante de la zone de liste déroulante **ensembles de règles** pour afficher les ensembles de règles disponibles. Pour créer une combinaison personnalisée d’ensembles de règles, sélectionnez **choisir plusieurs ensembles de règles**. La boîte de dialogue **Ajouter ou supprimer des ensembles de règles** répertorie les règles que vous pouvez choisir. Pour plus d’informations sur l’utilisation d’ensembles de règles dans Visual Studio, consultez [utiliser des ensembles de règles pour spécifier les règles C++ à exécuter](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

::: moniker-end
::: moniker range=">=msvc-160"

Pour afficher les ensembles de règles disponibles, ouvrez la boîte de dialogue **Propriétés du projet** . Dans la boîte de dialogue **pages de propriétés** , sélectionnez la page **Propriétés de configuration**  >  **analyse du code**  >  **Microsoft** . Ensuite, ouvrez la liste déroulante dans la zone de liste déroulante **règles actives** pour afficher les ensembles de règles disponibles. Pour créer une combinaison personnalisée d’ensembles de règles, sélectionnez **choisir plusieurs ensembles de règles**. La boîte de dialogue **Ajouter ou supprimer des ensembles de règles** répertorie les règles que vous pouvez choisir. Pour plus d’informations sur l’utilisation d’ensembles de règles dans Visual Studio, consultez [utiliser des ensembles de règles pour spécifier les règles C++ à exécuter](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

::: moniker-end

## <a name="macros"></a>Macros

Le vérificateur de C++ Core Guidelines est fourni avec un fichier d’en-tête, qui définit des macros qui facilitent la suppression des catégories entières d’avertissements dans le code :

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Ces macros correspondent aux ensembles de règles et se développent en une liste de numéros d’avertissement séparés par des espaces. En utilisant les constructions de pragma appropriées, vous pouvez configurer l’ensemble de règles effectif qui est intéressant pour un projet ou une section de code. Dans l’exemple suivant, l’analyse du code n’avertit que les modificateurs de constante manquants :

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attributs

Le compilateur Microsoft C++ a une prise en charge limitée de l' `[[gsl::suppress]]` attribut. Il peut être utilisé pour supprimer des avertissements sur les instructions d’expression et de bloc dans les fonctions.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>Supprimer l’analyse à l’aide des options de ligne de commande

Au lieu de #pragmas, vous pouvez utiliser les options de ligne de commande dans la page de propriétés du fichier pour supprimer les avertissements d’un projet ou d’un fichier unique. Par exemple, pour désactiver l’avertissement C26400 pour un fichier :

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier et choisissez **Propriétés**.

1. Dans la boîte de dialogue **pages de propriétés** , sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Dans la zone d’édition **options supplémentaires** , ajoutez *`/wd26400`* .

Vous pouvez utiliser l’option de ligne de commande pour désactiver temporairement l’ensemble de l’analyse du code pour un fichier en spécifiant **`/analyze-`** . Vous verrez un avertissement *D9025 remplaçant'/Analyze’par'/Analyze-'* , ce qui vous rappelle de réactiver l’analyse du code ultérieurement.

## <a name="enable-the-c-core-guidelines-checker-on-specific-project-files"></a><a name="corecheck_per_file"></a> Activer le vérificateur de C++ Core Guidelines sur des fichiers de projet spécifiques

Il est parfois utile d’effectuer une analyse du code ciblé tout en continuant à utiliser l’IDE de Visual Studio. Essayez l’exemple de scénario suivant pour les grands projets. Il peut économiser du temps de génération et faciliter le filtrage des résultats :

1. Dans l’interface de commande, définissez `esp.extension` les `esp.annotationbuildlevel` variables d’environnement et.

1. Pour hériter de ces variables, ouvrez Visual Studio à partir de l’interface de commande.

1. Chargez votre projet et ouvrez ses propriétés.

1. Activez l’analyse du code, choisissez les ensembles de règles appropriés, mais n’activez pas les extensions d’analyse du code.

1. Accédez au fichier que vous souhaitez analyser à l’aide de l’outil de vérification des C++ Core Guidelines et ouvrez ses propriétés.

1. Choisir les **Propriétés de configuration**  >  ligne de commande **C/C++**  >  **Command Line**  >  **options supplémentaires** et ajouter *`/analyze:plugin EspXEngine.dll`*

1. Désactivez l’utilisation de l’en-tête précompilé ( **Propriétés de configuration**  >  **C/C++**  >  **en-têtes précompilés** C/C++). C’est nécessaire, car le moteur d’extensions peut tenter de lire ses informations internes à partir de l’en-tête précompilé (PCH). Si le PCH a été compilé avec les options de projet par défaut, il ne sera pas compatible.

1. Regénérez le projet. Les vérifications prérapides courantes doivent s’exécuter sur tous les fichiers. Étant donné que l’outil de vérification de C++ Core Guidelines n’est pas activé par défaut, il ne doit s’exécuter que sur le fichier configuré pour l’utiliser.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Comment utiliser l’outil de vérification de C++ Core Guidelines en dehors de Visual Studio

Vous pouvez utiliser les contrôles de C++ Core Guidelines dans les builds automatisées.

### <a name="msbuild"></a>MSBuild

L’outil d’analyse du code natif (PREfast) est intégré à l’environnement MSBuild par les fichiers de cibles personnalisés. Vous pouvez utiliser les propriétés du projet pour l’activer et ajouter le vérificateur d’C++ Core Guidelines (qui est basé sur PREfast) :

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Veillez à ajouter ces propriétés avant l’importation du *`Microsoft.Cpp.targets`* fichier. Vous pouvez choisir des ensembles de règles spécifiques ou créer un ensemble de règles personnalisé. Ou utilisez l’ensemble de règles par défaut qui comprend d’autres vérifications PREfast.

Vous pouvez exécuter l’outil de vérification du noyau C++ uniquement sur les fichiers spécifiés. Utilisez la même approche que celle [décrite précédemment](#corecheck_per_file), mais utilisez des fichiers MSBuild. Les variables d’environnement peuvent être définies à l’aide de l' `BuildMacro` élément :

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Si vous ne souhaitez pas modifier le fichier projet, vous pouvez passer des propriétés sur la ligne de commande :

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projets non-MSBuild

Si vous utilisez un système de génération qui ne repose pas sur MSBuild, vous pouvez toujours exécuter l’outil de vérification. Pour l’utiliser, vous devez vous familiariser avec certains éléments internes de la configuration du moteur d’analyse du code. Nous ne garantissons pas la prise en charge de ces éléments internes dans les futures versions de Visual Studio.

L’analyse du code requiert quelques variables d’environnement et des options de ligne de commande du compilateur. Nous vous recommandons d’utiliser l’environnement d' **invite de commandes des outils natifs** pour ne pas avoir à rechercher des chemins spécifiques pour le compilateur, les répertoires Include, etc.

- **Variables d’environnement**
  - `set esp.extensions=cppcorecheck.dll` Cela indique au moteur de charger le module C++ Core Guidelines.
  - `set esp.annotationbuildlevel=ignore` Cela désactive la logique qui traite les annotations SAL. Les annotations n’affectent pas l’analyse du code dans le vérificateur de C++ Core Guidelines, mais leur traitement prend du temps (parfois à long terme). Ce paramètre est facultatif, mais fortement recommandé.
  - `set caexcludepath=%include%` Nous vous recommandons vivement de désactiver les avertissements qui se déclenchent sur les en-têtes standard. Vous pouvez ajouter d’autres chemins ici, par exemple, le chemin d’accès aux en-têtes courants dans votre projet.

- **Options de ligne de commande**
  - **`/analyze`**  Active l’analyse du code (envisagez également d’utiliser **`/analyze:only`** et **`/analyze:quiet`** ).
  - **`/analyze:plugin EspXEngine.dll`** Cette option charge le moteur des extensions d’analyse du code dans le prérapide. Ce moteur charge, à son tour, le vérificateur de C++ Core Guidelines.

## <a name="use-the-guideline-support-library"></a>Utiliser la bibliothèque de prise en charge des instructions

La bibliothèque de prise en charge des instructions (GSL) est conçue pour vous aider à suivre les instructions principales. Le portail GSL comprend des définitions qui vous permettent de remplacer des constructions sujettes aux erreurs par des alternatives plus sûres. Par exemple, vous pouvez remplacer une `T*, length` paire de paramètres par le `span<T>` type. Le portail GSL est disponible à l’adresse [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . La bibliothèque étant Open source, vous pouvez afficher les sources, créer des commentaires ou contribuer. Le projet se trouve à l’adresse [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .

::: moniker range="msvc-140"

## <a name="use-the-c-core-check-guidelines-in-visual-studio-2015-projects"></a><a name="vs2015_corecheck"></a> Utiliser les instructions de C++ Core Check dans les projets Visual Studio 2015

Si vous utilisez Visual Studio 2015, les ensembles de règles d’analyse du code C++ Core Check ne sont pas installés par défaut. Des étapes supplémentaires sont nécessaires avant de pouvoir activer les outils d’analyse du code C++ Core Check dans Visual Studio 2015. Microsoft fournit une prise en charge pour les projets Visual Studio 2015 à l’aide d’un package NuGet. Le package est nommé Microsoft. CppCoreCheck et il est disponible à l’adresse [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . Pour ce package, vous devez avoir au moins Visual Studio 2015 avec la mise à jour 1 installée.

Le package installe également un autre package en tant que dépendance, la bibliothèque de prise en charge des instructions en en-tête uniquement (GSL). Le portail GSL est également disponible sur GitHub à l’adresse [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .

En raison de la façon dont les règles d’analyse du code sont chargées dans Visual Studio 2015, vous devez installer le `Microsoft.CppCoreCheck` package NuGet dans chaque projet C++ que vous souhaitez vérifier.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Pour ajouter le package Microsoft. CppCoreCheck à votre projet dans Visual Studio 2015

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit pour ouvrir le menu contextuel de votre projet dans la solution à laquelle vous souhaitez ajouter le package. Sélectionnez **gérer les packages NuGet** pour ouvrir le **Gestionnaire de package NuGet**.

1. Dans la fenêtre **Gestionnaire de package NuGet** , recherchez Microsoft. CppCoreCheck.

    ![La fenêtre du gestionnaire de package NuGet affiche le package CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

1. Sélectionnez le package Microsoft. CppCoreCheck, puis cliquez sur le bouton **installer** pour ajouter les règles à votre projet.

   Le package NuGet ajoute un fichier MSBuild supplémentaire *`.targets`* à votre projet qui est appelé lorsque vous activez l’analyse du code sur votre projet. Le *`.targets`* fichier ajoute les règles de C++ Core Check en tant qu’extension supplémentaire à l’outil d’analyse du code Visual Studio. Lorsque le package est installé, vous pouvez utiliser la boîte de dialogue pages de propriétés pour activer ou désactiver les règles de publication et expérimentale.

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Référence de C++ Core Check Visual Studio](code-analysis-for-cpp-corecheck.md)
