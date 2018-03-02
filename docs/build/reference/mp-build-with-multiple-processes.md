---
title: "/MP (générer avec plusieurs processus) | Documents Microsoft"
ms.custom: 
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.MultiProcessorCompilation
dev_langs:
- C++
helpviewer_keywords:
- -MP compiler option (C++)
- /MP compiler option (C++)
- MP compiler option (C++)
- cl.exe compiler, multi-process build
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5aa190d2cb2d1e0b0d13979d5e0044291d7cd8a7
ms.sourcegitcommit: d24de38f9da844f824acb9d200a3f263077145fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="mp-build-with-multiple-processes"></a>/MP (Générer avec plusieurs processus)

L’option **/MP** option peut réduire la durée totale de compilation des fichiers source sur la ligne de commande. L’option **/MP** indique au compilateur de créer une ou plusieurs copies de lui-même, chacune dans un processus distinct. Ces copies compilent alors les fichiers sources simultanément. En conséquence, la durée totale de génération des fichiers sources peut être considérablement réduite.

## <a name="syntax"></a>Syntaxe

> **/MP**[*processMax*]

## <a name="arguments"></a>Arguments

*processMax*<br/>
(Facultatif) Le nombre maximal de processus que le compilateur peut créer.

Le *processMax* argument doit être comprise entre 1 et 65536. Sinon, le compilateur émet le message d’avertissement **D9014**, ignore les *processMax* argument et suppose que le nombre maximal de processus est 1.

Si vous omettez le *processMax* argument, le compilateur récupère le nombre de [processeurs effectifs](#effective_processors) sur votre ordinateur à partir du système d’exploitation et crée un processus pour chaque processeur.

## <a name="remarks"></a>Notes

L’option **/MP** du compilateur peut réduire considérablement le temps de génération quand vous compilez de nombreux fichiers. Pour améliorer les temps de génération, le compilateur crée jusqu'à *processMax* copie de lui-même, puis utilise ces copies pour compiler vos fichiers sources en même temps. L’option **/MP** s’applique aux compilations, mais pas à la liaison ni à la génération de code au moment de la liaison. L’option **/MP** est désactivée par défaut.

L’amélioration de la durée de la génération dépend du nombre de processeurs sur un ordinateur, du nombre de fichiers à compiler et de la disponibilité des ressources système, comme la capacité d’E/S. Faites des essais avec l’option **/MP** pour déterminer la meilleure configuration pour générer un projet particulier. Pour des conseils pour vous aider à décider, consultez [Guidelines](#guidelines).

## <a name="incompatible-options-and-language-features"></a>Options et fonctionnalités du langage incompatibles

L’option **/MP** est incompatible avec certaines options du compilateur et certaines fonctionnalités du langage. Si vous utilisez une option du compilateur incompatible avec le **/MP** option, le compilateur émet un avertissement **D9030** et ignore le **/MP** option. Si vous utilisez une fonctionnalité de langage incompatible, le compilateur émet erreur [l’erreur C2813](../../error-messages/compiler-errors-2/compiler-error-c2813.md) puis s’arrête ou continue selon le compilateur actuel, option de niveau d’avertissement.

> [!NOTE]
> La plupart des options sont incompatibles car si elles étaient autorisées, les compilateurs s’exécutant simultanément écriraient leur sortie en même temps sur la console ou dans un fichier particulier. Par conséquent, la sortie serait un mélange incompréhensible. Dans certains cas, la combinaison des options diminuerait les performances.

Le tableau suivant répertorie les options du compilateur et les fonctionnalités du langage qui sont incompatibles avec l’option **/MP** :

|Option ou fonctionnalité du langage|Description|
|--------------------------------|-----------------|
|Directive du préprocesseur[#import](../../preprocessor/hash-import-directive-cpp.md) |Convertit les types d’une bibliothèque de types en classes C++, puis écrit ces classes dans un fichier d’en-tête.|
|[/E](../../build/reference/e-preprocess-to-stdout.md), [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|Copie la sortie du préprocesseur vers la sortie standard (**stdout**).|
|[/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|Active une régénération incrémentielle.|
|[/showIncludes](../../build/reference/showincludes-list-include-files.md)|Écrit une liste des fichiers include dans l’erreur standard (**stderr**).|
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|Écrit un fichier d’en-tête précompilé.|

## <a name="diagnostic-messages"></a>Messages de diagnostic

Si vous spécifiez une option ou une fonctionnalité du langage qui est incompatible avec l’option **/MP** , vous recevez un message de diagnostic. Le tableau suivant répertorie les messages et le comportement du compilateur :

|Message de diagnostic|Description|Comportement du compilateur|
|------------------------|-----------------|-----------------------|
|**C2813**|La directive **#import** n’est pas compatible avec l’option **/MP** .|La compilation se termine, sauf si une option de [niveau d’avertissement du compilateur](../../build/reference/compiler-option-warning-level.md) spécifie le contraire.|
|**D9014**|Une valeur non valide est spécifiée pour le *processMax* argument.|Le compilateur ignore la valeur non valide et suppose une valeur de 1.|
|**D9030**|L’option spécifiée est incompatible avec **/MP**.|Le compilateur ignore l’option **/MP** .|

## <a name="guidelines"></a> Guidelines

### <a name="measure-performance"></a>Mesurer les performances

Utilisez le temps total de la génération pour mesurer les performances. Vous pouvez mesurer le temps de la génération avec une horloge physique, ou vous pouvez utiliser le logiciel qui calcule la différence entre le moment où la génération démarre et celui où elle s’arrête. Si votre ordinateur a plusieurs processeurs, une horloge physique peut générer des résultats plus précis qu’un logiciel de mesure du temps.

### <a name="effective_processors"></a> Effective Processors

Un ordinateur peut avoir un ou plusieurs processeurs virtuels, qui sont également appelés *processeurs effectifs*, pour chacun de ses processeurs physiques. Chaque processeur physique peut avoir un ou plusieurs cœurs et, si le système d’exploitation permet d’hyperthreading pour un cœur, chaque cœur apparaît comme deux processeurs virtuels.

Par exemple, un ordinateur a un processeur effectif s’il a un processeur physique avec un seul cœur et que l’hyperthreading est désactivé. En revanche, un ordinateur a huit processeurs effectifs s’il a deux processeurs physiques, que chacun d’eux a deux cœurs et que l’hyperthreading est activé sur tous les cœurs. Autrement dit, (8 processeurs effectifs) = (2 processeurs physiques) x (2 cœurs par processeur physique) x (2 processeurs effectifs par cœur en raison de l’hyperthreading).

Si vous omettez le *processMax* argument dans le **/MP** option, le compilateur obtient le nombre de processeurs effectifs à partir du système d’exploitation, puis crée un processus par processeur effectif. Cependant, le compilateur ne peut pas garantir quel processus s’exécute sur un processeur particulier ; c’est le système d’exploitation qui prend cette décision.

### <a name="number-of-processes"></a>Nombre de processus

Le compilateur calcule le nombre de processus qu’il utilisera pour compiler les fichiers sources. Cette valeur est la plus petite entre le nombre de fichiers sources que vous spécifiez sur la ligne de commande et le nombre de processus que vous spécifiez explicitement ou implicitement avec l’option **/MP** . Vous pouvez définir explicitement le nombre maximal de processus si vous fournissez la *processMax* argument de la **/MP** option. Ou vous pouvez utiliser la valeur par défaut, qui est égal au nombre de processeurs effectifs dans un ordinateur, si vous omettez le *processMax* argument.

Par exemple, supposons que vous spécifiez la ligne de commande suivante :

`cl /MP7 a.cpp b.cpp c.cpp d.cpp e.cpp`

Dans ce cas, le compilateur utilise cinq processus car cinq est la valeur la plus petite entre les cinq fichiers sources et un maximum de sept processus. Supposons maintenant que votre ordinateur a deux processeurs effectifs et que vous spécifiez la ligne de commande suivante :

`cl /MP a.cpp b.cpp c.cpp`

Dans ce cas, le système d’exploitation indique deux processeurs et le compilateur utilise donc deux processus dans son calcul. Ainsi, le compilateur exécute la génération avec deux processus car c’est la valeur la plus petite entre les deux processus et les trois fichiers sources.

### <a name="source-files-and-build-order"></a>Fichiers sources et ordre de génération

Les fichiers sources peuvent ne pas être compilés dans le même ordre que celui où ils apparaissent sur la ligne de commande. Bien que le compilateur crée un ensemble de processus contenant des copies du compilateur, le système d’exploitation planifie le moment d’exécution de chaque processus. En conséquence, vous ne pouvez pas garantir que les fichiers sources seront compilés dans un ordre particulier.

Un fichier source est compilé quand un processus est disponible pour le compiler. S’il y a plus de fichiers que de processus, le premier ensemble de fichiers est compilé par les processus disponibles. Les fichiers restants sont traités quand un processus termine le traitement d’un fichier précédent et qu’il est disponible pour travailler sur un des fichiers restants.

Ne spécifiez pas le même fichier source plusieurs fois sur une ligne de commande. Cela peut se produire par exemple si un outil crée automatiquement un [makefile](../../build/contents-of-a-makefile.md) qui est basé sur les informations de dépendance dans un projet. Si vous ne spécifiez pas l’option **/MP** , le compilateur traite la liste des fichiers séquentiellement et recompile chaque occurrence du fichier. Cependant, si vous spécifiez l’option **/MP** , différents compilateurs peuvent compiler le même fichier en même temps. Par conséquent, les différents compilateurs essayent d’écrire dans le même fichier de sortie en même temps. Un compilateur acquiert l’accès en écriture exclusif au fichier de sortie et réussit, alors que les autres compilateurs échouent avec une erreur d’accès au fichier.

### <a name="using-type-libraries-import"></a>Utilisation de bibliothèques de types (#import)

Le compilateur ne prend pas en charge l’utilisation de la directive [#import](../../preprocessor/hash-import-directive-cpp.md) avec le commutateur **/MP** . Si possible, procédez comme suit pour contourner ce problème :

- Déplacez tous les directives `#import` de vos différents fichiers sources vers un ou plusieurs fichiers, puis compilez ces fichiers sans l’option **/MP** . Le résultat est un ensemble de fichiers d’en-tête générés.

- Dans vos fichiers sources restants, insérez des directives [#include](../../preprocessor/hash-include-directive-c-cpp.md) qui spécifient les en-têtes générés, puis compilez vos fichiers sources restants en utilisant l’option **/MP** .

### <a name="visual-studio-project-settings"></a>Paramètres des projets Visual Studio

#### <a name="the-msbuildexe-tool"></a>L’outil MSBUILD.exe

[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] utilise le [MSBuild.exe](/visualstudio/msbuild/msbuild-reference) outil pour générer des solutions et projets. Le **/maxcpucount :**_nombre_ (ou **/m:**_nombre_) une option de ligne de commande de l’outil MSBuild.exe peut générer plusieurs projets à la à la fois. L’option de compilateur **/MP** peut aussi générer plusieurs unités de compilation en même temps. Si c’est approprié pour votre application, améliorez le temps de génération de votre solution en utilisant **/MP** ou **/maxcpucount**, ou les deux.

Le temps de génération de votre solution dépend en partie du nombre de processus qui effectuent la génération. Le *nombre* argument de la [/maxcpucount](/visualstudio/msbuild/msbuild-command-line-reference) MSBuild option spécifie le nombre maximal de projets à générer en même temps. De même, la *processMax* argument de la **/MP** option du compilateur spécifie le nombre maximal d’unités de compilation à générer en même temps. Si le **/maxcpucount** option spécifie *P* projets et **/MP** option spécifie *C* traite, un maximum de *P*  x *C* processus s’exécutent en même temps.

 L’indication pour décider s’il faut utiliser MSBuild ou **/MP** technologie est comme suit :

- S’il existe de nombreux projets avec peu de fichiers dans chaque projet, utilisez l’outil MSBuild.

- S’il existe peu de projets avec de nombreux fichiers dans chaque projet, utilisez l’option **/MP** .

- Si le nombre de projets et des fichiers par projet est équilibré, utilisez à la fois MSBuild et **/MP**. Définissez d’abord l’option **/maxcpucount** sur le nombre de projets à générer et l’option **/MP** sur le nombre de processeurs de votre ordinateur. Mesurez les performances, puis ajustez les paramètres pour obtenir les meilleurs résultats. Répétez ce cycle jusqu’à ce que le temps total de la génération soit satisfaisant.

#### <a name="the-gm-compiler-option"></a>L’option de compilateur /Gm

Par défaut, la génération d’un projet active l’option de compilateur **/Gm** (générations incrémentielles) pour les versions debug, et la désactive les versions Release. Par conséquent, l’option de compilateur **/MP** est automatiquement désactivée dans les versions debug, car elle est en conflit avec la valeur par défaut de l’option de compilateur **/Gm** .

## <a name="see-also"></a>Voir aussi

[#import (directive)](../../preprocessor/hash-import-directive-cpp.md)<br/>
[Informations de référence sur la ligne de commande](/visualstudio/msbuild/msbuild-command-line-reference)<br/>
[/ZF (génération PDB plus rapide)](zf.md)<br/>
