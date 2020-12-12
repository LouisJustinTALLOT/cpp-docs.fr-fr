---
description: 'En savoir plus sur : erreur irrécupérable C1083'
title: Erreur irrécupérable C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: 5a2a0cb842b385963f4f4695a2289abc1c07a702
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189624"
---
# <a name="fatal-error-c1083"></a>Erreur irrécupérable C1083

> Impossible d’ouvrir le fichier *filetype* : '*file*' : *message*

Le compilateur génère une erreur C1083 lorsqu’il ne peut pas trouver un fichier dont il a besoin. Il existe de nombreuses causes possibles pour cette erreur. Un chemin de recherche include incorrect ou des fichiers d’en-tête manquants ou incorrectement spécifiés sont les causes les plus courantes, mais d’autres types de fichiers et problèmes peuvent également provoquer C1083. Voici quelques-unes des raisons les plus courantes pour lesquelles le compilateur génère cette erreur.

## <a name="the-specified-file-name-is-wrong"></a>Le nom de fichier spécifié est erroné

Le nom d'un fichier est peut-être tapé de façon incorrecte. Par exemple :

`#include <algorithm.h>`

ne trouve peut-être pas le fichier souhaité. La plupart des fichiers d’en-tête de bibliothèque standard C++ n’ont pas d’extension de nom de fichier. h. L' \<algorithm> en-tête ne sera pas trouvé par cette `#include` directive. Pour résoudre ce problème, vérifiez que le nom de fichier correct est entré, comme dans cet exemple :

`#include <algorithm>`

Certains en-têtes de la bibliothèque runtime C sont situés dans un sous-répertoire du répertoire Include standard. Par exemple, pour inclure *`sys/types.h`* , vous devez inclure le *`sys`* nom du sous-répertoire dans la `#include` directive :

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>Le fichier n’est pas inclus dans le chemin de recherche include

Le compilateur ne parvient pas à trouver le fichier à l'aide des règles de recherche indiquées par une directive `#include` ou `#import`. Par exemple, lorsqu’un nom de fichier d’en-tête est placé entre guillemets,

`#include "myincludefile.h"`

Cela indique au compilateur de rechercher d’abord le fichier dans le même répertoire qui contient le fichier source, puis de rechercher dans d’autres emplacements spécifiés par l’environnement de génération. Si les guillemets contiennent un chemin d’accès absolu, le compilateur recherche uniquement le fichier à cet emplacement. Si les guillemets contiennent un chemin d'accès relatif, le compilateur recherche le fichier dans le répertoire relatif au répertoire source.

Si le nom est placé entre crochets pointus,

`#include <stdio.h>`

le compilateur suit un chemin de recherche défini par l’environnement de génération, l' **`/I`** option de compilateur, l' **`/X`** option de compilateur et la variable d’environnement **include** . Pour plus d’informations, notamment des détails spécifiques sur l’ordre de recherche utilisé pour rechercher un fichier, consultez [#include directive (C/C++)](../../preprocessor/hash-include-directive-c-cpp.md) et [#import directive](../../preprocessor/hash-import-directive-cpp.md).

Si vos fichiers include se trouvent dans un autre répertoire relatif à votre répertoire source et que vous utilisez un chemin d’accès relatif dans vos directives include, vous devez utiliser des guillemets doubles à la place des crochets pointus. Par exemple, si votre fichier d’en-tête *`myheader.h`* se trouve dans un sous-répertoire de vos sources de projet nommées en-têtes, cet exemple ne parvient pas à trouver le fichier et provoque C1083 :

`#include <headers\myheader.h>`

mais cet exemple fonctionne :

`#include "headers\myheader.h"`

Les chemins d’accès relatifs peuvent également être utilisés avec des répertoires dans le chemin de recherche include. Si vous ajoutez un répertoire à la variable d’environnement **include** ou à votre chemin d’accès aux **répertoires Include** dans Visual Studio, n’ajoutez pas une partie du chemin d’accès aux directives include. Par exemple, si votre en-tête se trouve dans *`\path\example\headers\myheader.h`* et que vous ajoutez *`\path\example\headers\`* à votre chemin d’accès aux **répertoires Include** dans Visual Studio, mais que votre `#include` directive fait référence au fichier en tant que

`#include <headers\myheader.h>`

le fichier est introuvable. Utilisez le chemin d’accès correct relatif au répertoire spécifié dans le chemin de recherche include. Dans cet exemple, vous pouvez modifier le chemin de recherche include en *`\path\example\`* ou supprimer le *`headers\`* segment de chemin d’accès de la `#include` directive.

## <a name="third-party-library-issues-and-vcpkg"></a>Problèmes de bibliothèque tierce et vcpkg

Si vous voyez cette erreur lorsque vous essayez de configurer une bibliothèque tierce dans le cadre de votre Build, envisagez d’utiliser [`vcpkg`](../../build/vcpkg.md) , un gestionnaire de package C++, pour installer et générer la bibliothèque. vcpkg prend en charge une liste volumineuse et croissante [de bibliothèques tierces](https://github.com/Microsoft/vcpkg/tree/master/ports), et définit toutes les propriétés de configuration et les dépendances requises pour les builds réussies dans le cadre de votre projet.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>Le fichier se trouve dans votre projet, mais pas dans le chemin de recherche include

Même lorsque les fichiers d’en-tête sont répertoriés dans **Explorateur de solutions** dans le cadre d’un projet, les fichiers sont trouvés uniquement par le compilateur lorsqu’ils sont référencés par une `#include` `#import` directive ou dans un fichier source, et se trouvent dans un chemin de recherche include. Différents genres de builds peuvent utiliser différents chemins d’accès de recherche. L' **`/X`** option de compilateur peut être utilisée pour exclure des répertoires du chemin de recherche include. Cela permet à des builds distinctes d'utiliser des fichiers Include distincts qui portent le même nom, mais qui sont conservés dans des dossiers différents. Il s'agit d'une alternative à la compilation conditionnelle à l'aide de commandes de préprocesseur. Pour plus d’informations sur l' **`/X`** option du compilateur, consultez [ `/X` (ignorer les chemins d’accès Include standard)](../../build/reference/x-ignore-standard-include-paths.md).

Pour résoudre ce problème, corrigez le chemin d'accès utilisé par le compilateur pour rechercher le fichier inclus ou importé. Un nouveau projet utilise les chemins de recherche include par défaut. Vous devrez peut-être modifier le chemin de recherche include pour ajouter un répertoire pour votre projet. Si vous compilez sur la ligne de commande, ajoutez le chemin d’accès à la variable d’environnement **include** ou l' **`/I`** option du compilateur pour spécifier le chemin d’accès au fichier.

Pour définir le chemin d’accès du répertoire include dans Visual Studio, ouvrez la boîte de dialogue **pages de propriétés** du projet. Dans le volet gauche de la fenêtre **Propriétés de configuration** , sélectionnez **Répertoires VC + +** , puis modifiez la propriété **inclure les répertoires** . Pour plus d’informations sur les répertoires par utilisateur et par projet recherchés par le compilateur dans Visual Studio, consultez la [page de propriétés Répertoires VC + +](../../build/reference/vcpp-directories-property-page.md). Pour plus d’informations sur l' **`/I`** option du compilateur, consultez [ `/I` (autres répertoires Include)](../../build/reference/i-additional-include-directories.md).

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>L’environnement INCLUDe de la ligne de commande ou LIB n’est pas défini

Lorsque le compilateur est appelé sur la ligne de commande, les variables d'environnement sont souvent utilisées pour spécifier des chemins de recherche. Si le chemin de recherche décrit par la variable d’environnement **include** ou **lib** n’est pas défini correctement, une erreur C1083 peut être générée. Nous vous recommandons vivement d’utiliser un raccourci d’invite de commandes développeur pour définir l’environnement de base pour les générations à partir de la ligne de commande. Pour plus d’informations, consultez [Build C/C++ sur la ligne de commande](../../build/building-on-the-command-line.md). Pour plus d’informations sur l’utilisation des variables d’environnement, consultez [Comment : utiliser des variables d’environnement dans une build](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).

## <a name="the-file-may-be-locked-or-in-use"></a>Le fichier est peut-être verrouillé ou en cours d’utilisation

Si vous utilisez un autre programme pour modifier ou accéder au fichier, le fichier peut être verrouillé. Essayez de fermer le fichier dans l’autre programme. Parfois, l’autre programme peut être Visual Studio lui-même, si vous utilisez des options de compilation parallèle. Si la désactivation de l’option de génération parallèle fait disparaître l’erreur, il s’agit du problème. D’autres systèmes de génération parallèle peuvent également rencontrer ce problème. Veillez à définir les dépendances de fichier et de projet pour que l’ordre de génération soit correct. Dans certains cas, envisagez de créer un projet intermédiaire pour forcer l’ordre des dépendances de génération pour un fichier commun qui peut être généré par plusieurs projets. Parfois, les programmes antivirus verrouillent temporairement les fichiers récemment modifiés pour l’analyse. Si possible, envisagez d’exclure les répertoires de build de votre projet du scanneur antivirus.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>La version incorrecte d'un nom de fichier est incluse

Une erreur C1083 peut également indiquer que la version incorrecte d'un fichier a été incluse. Par exemple, une build peut inclure la mauvaise version d'un fichier qui possède une directive `#include` pour un fichier d'en-tête non destiné à cette build. Par exemple, certains fichiers peuvent s’appliquer uniquement aux builds x86, ou déboguer des builds. Lorsque le fichier d'en-tête est introuvable, le compilateur génère une erreur C1083. Pour résoudre ce problème, utilisez le fichier approprié. N'ajoutez pas le fichier d'en-tête ou le répertoire à la build.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Les en-têtes précompilés ne sont pas encore précompilés

Lorsqu’un projet est configuré pour utiliser des en-têtes précompilés, les *`.pch`* fichiers appropriés doivent être créés afin que les fichiers qui utilisent le contenu d’en-tête puissent être compilés. Par exemple, le *`pch.cpp`* fichier ( *`stdafx.cpp`* dans Visual Studio 2017 et versions antérieures) est automatiquement créé dans le répertoire du projet pour les nouveaux projets. Compilez d’abord ce fichier pour créer les fichiers d’en-tête précompilés. Dans la conception de processus de génération typique, cette opération est effectuée automatiquement. Pour plus d’informations, consultez [création de fichiers d’en-tête précompilés](../../build/creating-precompiled-header-files.md).

## <a name="additional-causes"></a>Causes supplémentaires

- Vous avez installé un kit de développement logiciel (SDK) ou une bibliothèque tierce, mais vous n’avez pas ouvert une nouvelle fenêtre d’invite de commandes développeur après l’installation du kit de développement logiciel (SDK) ou de la bibliothèque. Si le kit de développement logiciel (SDK) ou la bibliothèque ajoute des fichiers au chemin d’accès **include** , vous devrez peut-être ouvrir une nouvelle fenêtre d’invite de commandes développeur pour sélectionner ces modifications de variable d’environnement.

- Le fichier utilise du code managé, mais l’option de compilateur **`/clr`** n’est pas spécifiée. Pour plus d’informations, consultez [ `/clr` (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

- Le fichier est compilé à l’aide d’un autre **`/analyze`** paramètre d’option de compilateur que celui utilisé pour précompiler les en-têtes. Lorsque les en-têtes d’un projet sont précompilés, tous doivent utiliser les mêmes **`/analyze`** paramètres. Pour plus d’informations, consultez [ `/analyze` (analyse du code)](../../build/reference/analyze-code-analysis.md).

- Le fichier ou le répertoire a été créé par le sous-système Windows pour Linux, le respect de la casse par répertoire est activé, et la casse spécifiée d’un chemin d’accès ou d’un fichier ne correspond pas à la casse du chemin d’accès ou du fichier sur le disque.

- Le fichier, le répertoire ou le disque est en lecture seule.

- Visual Studio ou les outils en ligne de commande ne disposent pas des autorisations suffisantes pour lire le fichier ou le répertoire. Cela peut se produire, par exemple, lorsque les fichiers projet ont une propriété différente de celle du processus exécutant Visual Studio ou les outils en ligne de commande. Parfois, ce problème peut être résolu en exécutant Visual Studio ou l’invite de commandes développeur en tant qu’administrateur.

- Il n'y a pas assez de handles de fichiers. Fermez certaines applications, puis recompilez. Cette situation est inhabituelle dans des circonstances normales. Toutefois, elle peut se produire lorsque des projets de grande taille sont générés sur un ordinateur dont la mémoire physique est limitée.

## <a name="example"></a>Exemple

L’exemple suivant génère une erreur C1083 lorsque le fichier d’en-tête `"test.h"` n’existe pas dans le répertoire source ou dans le chemin de recherche include.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

Pour plus d’informations sur la génération de projets C/C++ dans l’IDE ou sur la ligne de commande, ainsi que sur la définition de variables d’environnement, consultez [projets et générer des systèmes](../../build/projects-and-build-systems-cpp.md).

## <a name="see-also"></a>Voir aussi

- [Propriétés MSBuild](/visualstudio/msbuild/msbuild-properties)
