---
title: C++Avertissements des instructions de base
ms.date: 10/16/2019
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
ms.openlocfilehash: 544c737470a6578e65e82bb3c8cf1824ec93895f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079966"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Utilisation des vérificateurs C++ Core Guidelines

Les C++ directives principales sont un ensemble portable d’instructions, de règles et de meilleures pratiques concernant le C++ codage créé C++ par des experts et des concepteurs. Visual Studio prend actuellement en charge un sous-ensemble de ces règles dans le cadre de C++ses outils d’analyse du code pour. Les contrôleurs d’instructions de base sont installés par défaut dans Visual Studio 2017 et Visual Studio 2019, et sont [disponibles en tant que package NuGet pour Visual studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Le C++ projet de recommandations principales

Créé par Bjarne Stroustrup et d’autres, C++ les recommandations de base sont un guide d' C++ utilisation de la sécurité moderne et efficace. Les directives insistent sur la sécurité des types statiques et la sécurité des ressources. Ils identifient les moyens d’éliminer ou de réduire les parties les plus sujettes aux erreurs du langage, et de vous suggérer comment rendre votre code plus simple et plus performant de manière fiable. Ces recommandations sont gérées par la C++ base standard. Pour en savoir plus, consultez la documentation, C++ [ C++ les instructions principales](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)et accédez aux fichiers de projet de base de documentation sur [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Activer les C++ instructions de contrôle de base dans l’analyse du code

Vous pouvez activer l’analyse du code sur votre projet en activant la case à cocher **activer l’analyse du code sur la build** dans la section **analyse du code** de la boîte de dialogue **pages de propriétés** de votre projet.

![Page de propriétés pour les paramètres généraux de l’analyse du code](../code-quality/media/cppcorecheck_codeanalysis_general.png)

Les C++ règles de contrôle de base sont des extensions aux ensembles de règles par défaut qui s’exécutent lorsque l’analyse du code est activée. Étant donné C++ que les règles de contrôle de base sont en cours de développement, certaines règles sont bien établies et certaines peuvent ne pas être prêtes à être utilisées sur tout le code, mais peuvent toujours être informatives. Les règles sont divisées en deux groupes : Released et expérimental. Vous pouvez choisir d’exécuter ou non les règles publiées ou expérimentales dans les propriétés de votre projet.

![Page de propriétés pour les paramètres des extensions d’analyse du code](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

Pour activer ou désactiver les C++ ensembles de règles de vérification de base, ouvrez la boîte de dialogue **pages de propriétés** de votre projet. Sous **Propriétés de configuration**, développez **analyse du code**, **Extensions**. Dans le contrôle de liste déroulante en regard de **activer C++ la vérification principale (publiée)** ou **activer C++ la vérification principale (expérimental)** , choisissez **Oui** ou **non**. Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="examples"></a>Exemples

Voici un exemple de certains des problèmes que les C++ règles de contrôle de base peuvent trouver :

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

Cet exemple illustre quelques-uns des avertissements que les C++ règles de contrôle de base peuvent trouver :

- C26494 est de type règle. 5 : Initialise toujours un objet.

- C26485 est une limite de règle. 3 : aucune atténuation de tableau à pointeur.

- C26481 est une limite de règle. 1 : n’utilisez pas l’arithmétique de pointeur. Utilisez `span` à la place.

Si les C++ ensembles de règles d’analyse du code de contrôle de base sont installés et activés lorsque vous compilez ce code, les deux premiers avertissements sont générés, mais le troisième est supprimé. Voici la sortie de la génération de l’exemple de code :

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Les C++ recommandations de base sont là pour vous aider à écrire du code plus sécurisé. Toutefois, si vous avez une instance dans laquelle une règle ou un profil ne doit pas être appliqué, il est facile de la supprimer directement dans le code. Vous pouvez utiliser l’attribut `gsl::suppress` pour garder C++ le contrôle principal de la détection et du signalement d’une violation d’une règle dans le bloc de code suivant. Vous pouvez marquer des instructions individuelles pour supprimer des règles spécifiques. Vous pouvez même supprimer le profil de limites entier en écrivant `[[gsl::suppress(bounds)]]` sans inclure un numéro de règle spécifique.

## <a name="supported-rule-sets"></a>Ensembles de règles pris en charge

À mesure que de nouvelles règles sont C++ ajoutées à l’outil de vérification des instructions de base, le nombre d’avertissements générés pour le code préexistant peut augmenter. Vous pouvez utiliser des ensembles de règles prédéfinis pour filtrer les genres de règles à activer. À compter de Visual Studio 2017 version 15,3, les ensembles de règles pris en charge sont les suivants :

- Les **règles de pointeur propriétaire** appliquent [ C++ les vérifications de gestion des ressources liées au propriétaire\<t > à partir des instructions de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Les **règles const** appliquent [ C++ les vérifications liées à const à partir des instructions de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- Les **règles de pointeur brut** appliquent [ C++ les vérifications de gestion des ressources liées aux pointeurs bruts à partir des recommandations principales](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Les **règles de pointeur uniques** appliquent [les C++ vérifications de gestion des ressources liées aux types avec une sémantique de pointeur unique à partir des instructions de base](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Les **règles de limites** appliquent le [profil de limites C++ des recommandations principales](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- Les **règles de type** appliquent le [profil C++ de type des recommandations principales](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

Vous pouvez choisir de limiter les avertissements à un seul ou à quelques groupes. Les ensembles de règles natifs **minimum** et **natif recommandés** incluent C++ des règles de contrôle de base en plus d’autres vérifications prérapides. Pour afficher les ensembles de règles disponibles, ouvrez la boîte de dialogue Propriétés du projet, sélectionnez **code Analysis\General**, ouvrez la zone de liste déroulante **ensembles de règles** , puis **Choisissez plusieurs ensembles de règles**. Pour plus d’informations sur l’utilisation d’ensembles de règles dans Visual Studio, consultez [utiliser des C++ ensembles de règles pour spécifier les règles à exécuter](using-rule-sets-to-specify-the-cpp-rules-to-run.md) et [utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules).

## <a name="macros"></a>Macros

Le C++ vérificateur des instructions de base est fourni avec un fichier d’en-tête qui définit des macros qui facilitent la suppression des catégories entières d’avertissements dans le code :

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Ces macros correspondent aux ensembles de règles et se développent en listes séparées par des espaces de numéros d’avertissement. À l’aide des constructions pragma appropriées, vous pouvez configurer l’ensemble de règles effectif qui est intéressant pour un projet ou une section de code. Dans l’exemple suivant, l’analyse du code ne signale que les modificateurs de constante manquants :

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attributs

Le compilateur C++ Microsoft a une prise en charge limitée de l’attribut de suppression GSL. Il peut être utilisé pour supprimer des avertissements sur les instructions d’expression et de bloc dans une fonction.

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

## <a name="suppressing-analysis-by-using-command-line-options"></a>Suppression de l’analyse à l’aide des options de ligne de commande

Au lieu de #pragmas, vous pouvez utiliser les options de ligne de commande dans la page de propriétés du fichier pour supprimer les avertissements d’un projet ou d’un fichier unique. Par exemple, pour désactiver l’avertissement C26400 pour un fichier :

1. Cliquez avec le bouton droit sur le fichier dans **Explorateur de solutions**

1. Choisir les **Propriétés | C/C++| Ligne de commande**

1. Dans la fenêtre **options supplémentaires** , ajoutez `/wd26400`.

Vous pouvez utiliser l’option de ligne de commande pour désactiver temporairement l’ensemble de l’analyse du code d’un fichier en spécifiant `/analyze-`. Cela génère un avertissement *D9025 remplaçant'/Analyze’par'/Analyze-'* , ce qui vous rappelle de réactiver l’analyse du code ultérieurement.

## <a name="enabling-the-c-core-guidelines-checker-on-specific-project-files"></a><a name="corecheck_per_file"></a>Activation du C++ vérificateur des instructions de base sur des fichiers de projet spécifiques

Parfois, il peut être utile d’effectuer une analyse du code ciblé tout en tirant parti de l’IDE de Visual Studio. Voici un exemple de scénario qui peut être utilisé pour des projets volumineux afin d’économiser du temps de génération et de faciliter le filtrage des résultats.

1. Dans l’interface de commande, définissez les variables d’environnement `esp.extension` et `esp.annotationbuildlevel`.
1. Ouvrez Visual Studio à partir de l’interface de commande pour hériter de ces variables.
1. Chargez votre projet et ouvrez ses propriétés.
1. Activez l’analyse du code, choisissez les ensembles de règles appropriés, mais n’activez pas les extensions d’analyse du code.
1. Accédez au fichier que vous souhaitez analyser à l’aide C++ de l’outil de vérification des instructions de base et ouvrez ses propriétés.
1. Choisissez les **optionsC++de ligne C/\Command** et ajoutez `/analyze:plugin EspXEngine.dll`
1. Désactivez l’utilisation de l’en-tête précompilé (**en-têtes CC++/\Precompiled**). Cela est nécessaire, car le moteur d’extensions peut tenter de lire ses informations internes à partir de l’en-tête précompilé et, si ce dernier a été compilé avec les options de projet par défaut, il ne sera pas compatible.
1. Regénérez le projet. Les vérifications prérapides courantes doivent s’exécuter sur tous les fichiers. Étant donné C++ que le vérificateur des instructions de base n’est pas activé par défaut, il ne doit s’exécuter que sur le fichier configuré pour l’utiliser.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Comment utiliser le C++ vérificateur des instructions de base en dehors de Visual Studio

Vous pouvez utiliser les C++ contrôles des instructions principales dans les builds automatisées.

### <a name="msbuild"></a>MSBuild

L’outil d’analyse du code natif (PREfast) est intégré à l’environnement MSBuild par les fichiers de cibles personnalisés. Vous pouvez utiliser les propriétés du projet pour l’activer et ajouter C++ le vérificateur des instructions de base (qui est basé sur PREfast) :

```xml
<PropertyGroup>
  <EnableCppCoreCheck>true</EnableCppCoreCheck>
  <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>
  <RunCodeAnalysis>true</RunCodeAnalysis>
</PropertyGroup>
```

Veillez à ajouter ces propriétés avant d’importer le fichier Microsoft. cpp. targets. Vous pouvez choisir des ensembles de règles spécifiques ou créer un ensemble de règles personnalisé ou utiliser l’ensemble de règles par défaut qui comprend d’autres vérifications PREfast.

Vous pouvez exécuter l' C++ outil de vérification de base uniquement sur les fichiers spécifiés à l’aide de la même approche que celle [décrite précédemment](#corecheck_per_file), mais en utilisant des fichiers MSBuild. Les variables d’environnement peuvent être définies à l’aide de l’élément `BuildMacro` :

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Si vous ne souhaitez pas modifier le fichier projet, vous pouvez passer des propriétés sur la ligne de commande :

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projets non-MSBuild

Si vous utilisez un système de génération qui ne repose pas sur MSBuild, vous pouvez toujours exécuter l’outil de vérification, mais vous devez vous familiariser avec certains éléments internes de la configuration du moteur d’analyse du code (qui n’est pas forcément pris en charge à l’avenir).

Vous devrez définir quelques variables d’environnement et utiliser les options de ligne de commande appropriées pour le compilateur. Il est préférable de travailler dans l’environnement « invite de commandes des outils natifs » afin de ne pas avoir à rechercher des chemins spécifiques pour le compilateur, les répertoires Include, etc.

1. **Variables d’environnement**
   - `set esp.extensions=cppcorecheck.dll` cela indique au moteur de charger le C++ module instructions principales.
   - `set esp.annotationbuildlevel=ignore` cela désactive la logique qui traite les annotations SAL. Les annotations n’affectent pas l' C++ analyse du code dans le vérificateur des instructions de base, mais leur traitement prend du temps (parfois beaucoup de temps). Ce paramètre est facultatif, mais fortement recommandé.
   - `set caexcludepath=%include%` nous vous recommandons vivement de désactiver les avertissements qui se déclenchent sur les en-têtes standard. Vous pouvez ajouter d’autres chemins ici, par exemple, le chemin d’accès aux en-têtes courants dans votre projet.
1. **Options de ligne de commande**
   - `/analyze` active l’analyse du code (envisagez également d’utiliser/Analyze : uniquement et/Analyze : quiet).
   - `/analyze:plugin EspXEngine.dll` cette option permet de charger le moteur des extensions d’analyse du code dans le préfast. Ce moteur charge, à son tour, C++ le vérificateur des instructions de base.

## <a name="use-the-guideline-support-library"></a>Utiliser la bibliothèque de prise en charge des instructions

La bibliothèque de prise en charge des instructions est conçue pour vous aider à suivre les instructions principales. Le portail GSL comprend des définitions qui vous permettent de remplacer des constructions sujettes aux erreurs par des alternatives plus sûres. Par exemple, vous pouvez remplacer une paire `T*, length` de paramètres par le type `span<T>`. Le portail GSL est disponible sur [https://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). La bibliothèque étant Open source, vous pouvez afficher les sources, créer des commentaires ou contribuer. Le projet se trouve sur [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

## <a name="use-the-c-core-check-guidelines-in-visual-studio-2015-projects"></a><a name="vs2015_corecheck"></a>Utiliser les C++ instructions de contrôle de base dans les projets Visual Studio 2015

Si vous utilisez Visual Studio 2015, les C++ ensembles de règles d’analyse du code de contrôle de base ne sont pas installés par défaut. Vous devez effectuer quelques étapes supplémentaires avant de pouvoir activer les C++ outils d’analyse du code de vérification de base dans Visual Studio 2015. Microsoft fournit une prise en charge pour les projets Visual Studio 2015 à l’aide d’un package NuGet. Le package est nommé Microsoft. CppCoreCheck et est disponible sur [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Pour ce package, vous devez avoir au moins Visual Studio 2015 avec la mise à jour 1 installée.

Le package installe également un autre package en tant que dépendance, une bibliothèque de prise en charge des instructions en en-tête uniquement (GSL). Le portail GSL est également disponible sur GitHub à l’adresse [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

En raison du mode de chargement des règles d’analyse du code, vous devez installer le package NuGet Microsoft. CppCoreCheck C++ dans chaque projet que vous souhaitez vérifier dans Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Pour ajouter le package Microsoft. CppCoreCheck à votre projet dans Visual Studio 2015

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit pour ouvrir le menu contextuel de votre projet dans la solution à laquelle vous souhaitez ajouter le package. Sélectionnez **gérer les packages NuGet** pour ouvrir le **Gestionnaire de package NuGet**.

1. Dans la fenêtre **Gestionnaire de package NuGet** , recherchez Microsoft. CppCoreCheck.

    ![La fenêtre du gestionnaire de package NuGet affiche le package CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

1. Sélectionnez le package Microsoft. CppCoreCheck, puis cliquez sur le bouton **installer** pour ajouter les règles à votre projet.

   Le package NuGet ajoute un fichier MSBuild. targets supplémentaire à votre projet qui est appelé lorsque vous activez l’analyse du code sur votre projet. Ce fichier. targets ajoute C++ les règles de contrôle de base en tant qu’extension supplémentaire à l’outil d’analyse du code Visual Studio. Lorsque le package est installé, vous pouvez utiliser la boîte de dialogue pages de propriétés pour activer ou désactiver les règles de publication et expérimentale.
