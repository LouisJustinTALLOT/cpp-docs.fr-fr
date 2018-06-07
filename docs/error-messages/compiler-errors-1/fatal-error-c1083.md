---
title: Erreur irrécupérable C1083 | Documents Microsoft
ms.custom: ''
ms.date: 09/01/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1083
dev_langs:
- C++
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b014ccc46434fd0c3f13689e579ed4798ebcdb2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569808"
---
# <a name="fatal-error-c1083"></a>Erreur irrécupérable C1083

> Impossible d’ouvrir *filetype* fichier : '*fichier*' : *message*

Le compilateur génère une erreur C1083 lorsqu’il ne peut pas trouver un fichier, qu'il requiert. Il existe de nombreuses causes possibles de cette erreur. Une recherche include incorrect chemin d’accès ou les fichiers d’en-tête manquant ou incorrectement sont les causes les plus courantes, mais les autres types de fichiers et les problèmes peuvent également provoquer C1083. Voici quelques-unes des raisons courantes pour lesquelles le compilateur génère cette erreur.

## <a name="the-specified-file-name-is-wrong"></a>Le nom de fichier spécifié est erroné

Le nom d'un fichier est peut-être tapé de façon incorrecte. Par exemple :

`#include <algorithm.h>`

ne trouve peut-être pas le fichier souhaité. La plupart des fichiers d’en-tête de bibliothèque C++ Standard n’ont pas une extension de nom de fichier .h. Le \<algorithme > en-tête ne seront pas trouvé par cette `#include` la directive. Pour résoudre ce problème, vérifiez que le nom de fichier, comme dans cet exemple :

`#include <algorithm>`

Certains en-têtes de la bibliothèque runtime C sont situés dans un sous-répertoire du répertoire Include standard. Par exemple, pour inclure sys/types.h, vous devez inclure le nom du sous-répertoire sys dans la `#include` directive :

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>Le fichier n’est pas inclus dans le chemin de recherche include

Le compilateur ne parvient pas à trouver le fichier à l'aide des règles de recherche indiquées par une directive `#include` ou `#import`. Par exemple, lorsqu’un nom de fichier d’en-tête est entre guillemets,

`#include "myincludefile.h"`

Cela indique au compilateur de rechercher le fichier dans le même répertoire que celui qui contient le fichier source tout d’abord et recherchez dans les autres emplacements spécifiés par l’environnement de génération. Si les guillemets contiennent un chemin d’accès absolu, le compilateur recherche uniquement le fichier à cet emplacement. Si les guillemets contiennent un chemin d’accès relatif, le compilateur recherche le fichier dans le répertoire relatif au répertoire source.

Si le nom est placé entre crochets,

`#include <stdio.h>`

le compilateur suit un chemin de recherche défini par l’environnement de génération, le **/I** option du compilateur, le **/X** option du compilateur et le **INCLUDE** variable d’environnement. Pour plus d’informations, y compris des détails spécifiques sur l’ordre de recherche utilisé pour rechercher un fichier, consultez [#include, Directive (C/C++)](../../preprocessor/hash-include-directive-c-cpp.md) et [Directive #import](../../preprocessor/hash-import-directive-cpp.md).

Si vos fichiers include sont dans un autre répertoire relatif au répertoire de votre code source, et que vous utilisez un chemin d’accès relatif dans votre #include, vous devez utiliser des guillemets doubles au lieu des crochets pointus. Par exemple, si votre myheader.h de fichier d’en-tête se trouve dans un sous-répertoire de vos sources de projet nommé en-têtes, cet exemple ne parvient pas à trouver le fichier et provoque C1083 :

`#include <headers\myheader.h>`

Toutefois, cet exemple fonctionne :

`#include "headers\myheader.h"`

Les chemins d’accès relatifs peuvent également servir avec des répertoires sur le chemin de recherche include. Si vous ajoutez un répertoire pour le **INCLUDE** variable d’environnement ou votre **répertoires Include** chemin d’accès dans Visual Studio, n’ajoutez pas également dans le chemin d’accès aux directives include. Par exemple, si votre en-tête se trouve dans \path\example\headers\myheader.h, et que vous ajoutez \path\example\headers\ à votre **répertoires Include** chemin d’accès dans Visual Studio, mais votre `#include` directive fait référence au fichier en tant que

`#include <headers\myheader.h>`

puis le fichier est introuvable. Utilisez le chemin d’accès correct par rapport au répertoire spécifié dans le chemin de recherche include. Dans cet exemple, vous pouvez modifier le chemin de recherche include et \path\example\, ou supprimer le segment de chemin d’accès headers\ à partir de la `#include` la directive.

## <a name="third-party-library-issues-and-vcpkg"></a>Problèmes de bibliothèque tierce et Vcpkg

Si vous recevez cette erreur lorsque vous essayez de configurer une bibliothèque tierce dans le cadre de votre build, envisagez d’utiliser [Vcpkg](../../vcpkg.md), le Gestionnaire de Package Visual C++, pour installer et de générer la bibliothèque. Prend en charge Vcpkg important et croissant [la liste des bibliothèques tierces](https://github.com/Microsoft/vcpkg/tree/master/ports)et définit toutes les propriétés de configuration et les dépendances requises pour les générations réussies dans le cadre de votre projet. Pour plus d’informations, consultez le [Blog Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) valider.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>Le fichier se trouve dans votre projet, mais pas le chemin de recherche include

Même lorsque les fichiers d’en-tête sont listés dans **l’Explorateur de solutions** dans le cadre d’un projet, les fichiers sont trouvés uniquement par le compilateur lorsqu’ils sont référencés par une `#include` ou `#import` directive dans une source de fichier et se trouvent dans un chemin de recherche Include. Différents genres de builds peuvent utiliser différents chemins d’accès de recherche. Le **/X** option du compilateur peut être utilisée pour exclure des répertoires à partir du chemin de recherche include. Cela permet à des builds distinctes d'utiliser des fichiers Include distincts qui portent le même nom, mais qui sont conservés dans des dossiers différents. Il s'agit d'une alternative à la compilation conditionnelle à l'aide de commandes de préprocesseur. Pour plus d’informations sur la **/X** option du compilateur, consultez [/X (ignorer Standard chemins d’accès Include)](../../build/reference/x-ignore-standard-include-paths.md).

Pour résoudre ce problème, corrigez le chemin d’accès utilisé par le compilateur pour rechercher le fichier inclus ou importé. Une nouvelle valeur par défaut de projet utilise les chemins de recherche include. Vous devrez peut-être modifier le chemin de recherche include pour ajouter un répertoire pour votre projet. Si vous compilez sur la ligne de commande, ajoutez le chemin d’accès à la **INCLUDE** variable d’environnement ou le **/I** option du compilateur pour spécifier le chemin d’accès au fichier.

Pour définir le chemin d’accès du répertoire include dans Visual Studio, ouvrez le projet **Pages de propriétés** boîte de dialogue. Sélectionnez **répertoires VC ++** sous **propriétés de Configuration** dans le volet gauche, puis modifiez le **répertoires Include** propriété. Pour plus d’informations sur les répertoires par utilisateur et par projet recherché par le compilateur dans Visual Studio, consultez [Page de propriétés répertoires VC ++](../../ide/vcpp-directories-property-page.md). Pour plus d’informations sur la **/I** option du compilateur, consultez [/I (autres répertoires Include)](../../build/reference/i-additional-include-directories.md).

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>La ligne de commande INCLUDE ou d’un environnement de LIB n’est pas définie.

Lorsque le compilateur est appelé sur la ligne de commande, les variables d’environnement sont souvent utilisées pour spécifier des chemins de recherche. Si le chemin de recherche décrit par le **INCLUDE** ou **LIB** variable d’environnement n’est pas définie correctement, une erreur C1083 peut être générée. Nous vous recommandons vivement de les builds à l’aide d’un raccourci d’invite de commandes développeur pour définir l’environnement de base pour la ligne de commande. Pour plus d’informations, consultez [génération C/C++ sur la ligne de commande](../../build/building-on-the-command-line.md). Pour plus d’informations sur l’utilisation des variables d’environnement, consultez [Comment : utiliser les Variables d’environnement dans une Build](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).

## <a name="the-file-may-be-locked-or-in-use"></a>Le fichier est peut-être verrouillé ou en cours d’utilisation

Si vous utilisez un autre programme pour modifier ou d’accéder au fichier, il est peut-être verrouillé le fichier. Essayez de fermer le fichier dans l’autre programme. L’autre programme peut parfois être Visual Studio, si vous utilisez les options de compilation parallèle. Si la désactivation de l’option de génération parallèle rend l’erreur disparaître, puis c’est le problème. Autres systèmes de génération en parallèle peuvent également avoir ce problème. Veillez à définir des dépendances de fichier et de projet afin de l’ordre de génération est correct. Dans certains cas, envisagez de créer un projet intermédiaire pour forcer l’ordre de dépendance de génération d’un fichier courantes qui peut-être être généré par plusieurs projets. Les programmes antivirus parfois verrouiller temporairement les fichiers récemment modifiés pour l’analyse. Si possible, envisagez excluant les répertoires de génération de projet à partir de l’antivirus.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>La version incorrecte d'un nom de fichier est incluse

Une erreur C1083 peut également indiquer que la version incorrecte d'un fichier a été incluse. Par exemple, une build peut inclure la mauvaise version d'un fichier qui possède une directive `#include` pour un fichier d'en-tête non destiné à cette build. Par exemple, certains fichiers peuvent s’appliquer uniquement à x86 génère, ou pour les versions Debug. Lorsque le fichier d'en-tête est introuvable, le compilateur génère une erreur C1083. Pour résoudre ce problème, utilisez le fichier approprié. N'ajoutez pas le fichier d'en-tête ou le répertoire à la build.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Les en-têtes précompilés ne sont pas encore précompilés

Lorsqu’un projet est configuré pour utiliser des en-têtes précompilés, les fichiers .pch appropriés doivent être créés de manière à ce que les fichiers qui utilisent le contenu d’en-tête puissent être compilés. Par exemple, le fichier stdafx.cpp est automatiquement créé dans le répertoire du projet pour les nouveaux projets. Compilez d’abord ce fichier pour créer les fichiers d’en-tête précompilés. Dans la conception de processus de génération classique, cela s’effectue automatiquement. Pour plus d’informations, consultez [création de fichiers d’en-tête précompilés](../../build/reference/creating-precompiled-header-files.md).

## <a name="additional-causes"></a>Causes supplémentaires

- Vous avez installé un kit de développement logiciel ou d’une bibliothèque tierce, mais vous n’avez pas ouvert une nouvelle fenêtre d’invite de commandes développeur après le Kit de développement ou la bibliothèque est installée. Si le Kit de développement logiciel ou la bibliothèque ajoute des fichiers à la **INCLUDE** chemin d’accès, vous devrez peut-être ouvrir une nouvelle fenêtre d’invite de commandes développeur pour relever ces modifications de variable d’environnement.

- Le fichier utilise du code managé, mais l’option de compilateur **/CLR** n’est pas spécifié. Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

- Le fichier est compilé à l’aide d’un autre **/ analyze** paramètre de l’option du compilateur que celui utilisé pour la précompilation des en-têtes. Lorsque les en-têtes d’un projet sont précompilés, tous doivent utiliser le même **/ analyze** paramètres. Pour plus d’informations, consultez l’article [/analyze (analyse de code)](../../build/reference/analyze-code-analysis.md).

- Le fichier ou répertoire a été créé par le sous-système Windows pour Linux, par répertoire de respect de la casse est activé, et le cas spécifié d’un fichier ou un chemin d’accès ne correspond pas à la casse du chemin d’accès ou du fichier sur le disque.

- Le fichier, le répertoire ou le disque est en lecture seule.

- Visual Studio ou les outils de ligne de commande n’ont pas d’autorisations suffisantes pour lire le fichier ou le répertoire. Par exemple, cela peut se produire lorsque les fichiers projet ont différentes propriétés que le processus en cours d’exécution Visual Studio ou les outils de ligne de commande. Parfois, ce problème peut être résolu en exécutant Visual Studio ou l’invite de commandes développeur en tant qu’administrateur.

- Il n'y a pas assez de handles de fichiers. Fermez certaines applications, puis recompilez. Cette situation est inhabituelle dans des circonstances normales. Toutefois, elle peut se produire lorsque des projets de grande taille sont générés sur un ordinateur dont la mémoire physique est limitée.

## <a name="example"></a>Exemple

L’exemple suivant génère une erreur C1083 lorsque le fichier d’en-tête `"test.h"` n’existe pas dans le répertoire source ou sur le chemin de recherche include.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

Pour plus d’informations sur la génération de projets C/C++ dans l’IDE ou sur la ligne de commande et les informations sur la définition des variables d’environnement, consultez [génération de programmes C/C++](../../build/building-c-cpp-programs.md).

## <a name="see-also"></a>Voir aussi

- [Propriétés MSBuild](/visualstudio/msbuild/msbuild-properties)
