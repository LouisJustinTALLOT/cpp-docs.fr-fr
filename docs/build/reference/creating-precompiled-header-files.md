---
title: Création de fichiers d’en-tête précompilé
ms.date: 11/19/2018
f1_keywords:
- pch
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: b570b76328ee9824610aac495d97cede19189cf9
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176430"
---
# <a name="creating-precompiled-header-files"></a>Création de fichiers d’en-tête précompilé

Les compilateurs Microsoft C et C++ offrent des options pour la précompilation du code en C ou C++, y compris du code incorporé. Grâce à cela, vous pouvez compiler un corps de code stable, stocker l'état compilé du code dans un fichier et, lors des compilations suivantes, combiner le code précompilé avec du code qui est toujours en cours de développement. Les compilations ultérieures sont plus rapides, car le code stable n'a pas besoin d'être recompilé.

Cette rubrique couvre les sujets d’en-tête précompilé suivants :

- [Quand précompiler le code source](#when-to-precompile-source-code)

- [Deux méthodes au choix pour la précompilation du code](#two-choices-for-precompiling-code)

- [Règles de cohérence s’appliquant aux en-têtes précompilés](#precompiled-header-consistency-rules)

- [Règles de cohérence pour l’utilisation d’en-têtes précompilés par fichier](#consistency-rules-for-per-file-use-of-precompiled-headers)

- [Règles de cohérence pour /Yc et /Yu](#consistency-rules-for-yc-and-yu)

- [Utilisation d’en-têtes précompilés dans un projet](#using-precompiled-headers-in-a-project)

- [Fichiers PCH utilisés dans le processus de génération](#pch-files-in-the-build-process)

- [Exemple de makefile pour PCH](#sample-makefile-for-pch)

- [Exemple de code pour PCH](#example-code-for-pch)

Pour plus d’informations de référence sur les options du compilateur relatives aux en-têtes précompilés, consultez [/Y (en-têtes précompilés)](../../build/reference/y-precompiled-headers.md).

## <a name="when-to-precompile-source-code"></a>Quand précompiler le code source

Code précompilé est utile au cours du cycle de développement pour réduire le temps de compilation, en particulier si :

- Vous utilisez toujours un large corps de code qui sont rarement modifiées.

- Votre programme comprend plusieurs modules, qui utilisent tous un ensemble standard de fichiers include et les mêmes options de compilation. Dans ce cas, tous les fichiers include peuvent être précompilés en un seul en-tête précompilé.

La première compilation — celle qui crée le fichier d’en-tête précompilé (PCH) — prend un peu plus de temps que les compilations suivantes. Les compilations ultérieures plus rapidement en incluant le code précompilé.

Vous pouvez précompiler des programmes C et C++. Dans la programmation C++, il est courant pour séparer les informations d’interface de classe dans les fichiers d’en-tête. Ces fichiers d’en-tête peuvent être inclus dans les programmes qui utilisent la classe ultérieurement. En recompilant ces en-têtes, vous pouvez réduire le temps pour compiler un programme.

> [!NOTE]
> Bien que vous pouvez utiliser qu’un seul fichier d’en-tête précompilé (.pch) par fichier source, vous pouvez utiliser plusieurs fichiers .pch dans un projet.

## <a name="two-choices-for-precompiling-code"></a>Deux méthodes au choix pour la précompilation du code

Avec Visual C++, vous pouvez précompiler n’importe quel code C ou C++ ; vous n’êtes pas limité à précompiler uniquement les fichiers d’en-tête.

La précompilation requiert une planification, mais il offre des compilations sensiblement plus rapides si vous précompilez un code source autre que des fichiers d’en-tête simples.

Précompiler le code lorsque vous savez que vos fichiers sources utilisent des jeux communs de fichiers d’en-tête mais ne les incluent pas dans le même ordre, ou lorsque vous souhaitez inclure du code source dans votre précompilation.

Les options d’en-tête précompilé sont [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) et [/Yu (utiliser un en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md). Utilisez **/Yc** pour créer un en-tête précompilé. Lorsqu’il est utilisé avec le paramètre facultatif [hdrstop](../../preprocessor/hdrstop.md) pragma, **/Yc** vous permet de précompiler les deux fichiers d’en-tête et de code source. Sélectionnez **/Yu** à utiliser un en-tête précompilé existant dans la compilation en cours. Vous pouvez également utiliser **/FP** avec la **/Yc** et **/Yu** options afin de fournir un autre nom pour l’en-tête précompilé.

Les rubriques de référence d’option du compilateur pour **/Yu** et **/Yc** expliquent comment accéder à cette fonctionnalité dans l’environnement de développement.

## <a name="precompiled-header-consistency-rules"></a>Règles de cohérence s’appliquant aux en-têtes précompilés

Étant donné que les fichiers PCH contiennent des informations sur l’environnement de machine, ainsi que des informations d’adresse de mémoire sur le programme, vous devez uniquement utiliser un fichier PCH sur l’ordinateur où il a été créé.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Règles de cohérence pour l’utilisation d’en-têtes précompilés par fichier

Le [/Yu](../../build/reference/yu-use-precompiled-header-file.md) option du compilateur vous permet de spécifier le fichier d’en-tête Précompilé à utiliser.

Lorsque vous utilisez un fichier PCH, le compilateur suppose que le même environnement de compilation, qui utilise les options du compilateur cohérente, des pragmas, etc., qui était en vigueur lorsque vous avez créé le fichier PCH, sauf indication contraire. Si le compilateur détecte une incohérence, il émet un avertissement et identifie l’incohérence lorsque cela est possible. Ces avertissements n’indiquent pas nécessairement un problème avec le fichier PCH ; ils simplement vous Avertissement des éventuels conflits. Exigences de cohérence pour les fichiers PCH sont décrits dans les sections suivantes.

### <a name="compiler-option-consistency"></a>Cohérence des options du compilateur

Les options du compilateur suivantes peuvent déclencher un avertissement d’incohérence lors de l’utilisation d’un fichier PCH :

- Macros créés à l’aide du préprocesseur (/ D) option doit être le même entre la compilation qui a créé le fichier PCH et la compilation en cours. L’état des constantes définies n’est pas activée, mais des résultats imprévisibles peuvent se produire si ces modifient.

- Fichiers PCH ne fonctionnent pas avec les options /E et /EP.

- Fichiers PCH doivent être créés à l’aide soit le générer recherche d’informations (/ FR) option ou exclure les Variables locales (/ Fr) option avant que les compilations ultérieures qui utilisent le fichier PCH peuvent utiliser ces options.

### <a name="c-70-compatible-z7"></a>Compatible C 7.0 (/ Z7)

Si cette option est activée lorsque le fichier PCH est créé, les compilations ultérieures qui utilisent le fichier PCH peuvent utiliser les informations de débogage.

Si le Compatible C 7.0 (/ Z7) option n’est pas en vigueur lorsque le fichier PCH est créé, les compilations ultérieures qui utilisent le fichier PCH et/Z7 déclenchent un avertissement. Les informations de débogage sont placées dans le fichier .obj en cours, et les symboles locaux définis dans le fichier PCH ne sont pas disponibles pour le débogueur.

### <a name="include-path-consistency"></a>Inclure la cohérence du chemin d’accès

Un fichier d’en-tête Précompilé ne contient pas d’informations sur le chemin d’accès include qui était en vigueur lors de sa création. Lorsque vous utilisez un fichier PCH, le compilateur utilise toujours le chemin d’accès include spécifié dans la compilation actuelle.

### <a name="source-file-consistency"></a>Cohérence du fichier source

Lorsque vous spécifiez l’option d’utiliser un fichier d’en-tête précompilé (/Yu), le compilateur ignore toutes les directives de préprocesseur (y compris les pragmas) qui s’affichent dans le code source qui sera précompilé. La compilation spécifiée par ces directives de préprocesseur doit être identique à celle utilisée pour l’option créer un en-tête précompilé (/Yc).

### <a name="pragma-consistency"></a>Cohérence des pragmas

Pragmas traités lors de la création d’un fichier PCH affectent généralement le fichier avec lequel le fichier PCH est utilisé par la suite. Le `comment` et `message` pragmas n’affectent pas le reste de la compilation.

Ces pragmas affectent uniquement le code dans le fichier PCH ; elles n’affectent pas le code qui utilise ensuite le fichier PCH :

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Ces pragmas sont conservés dans le cadre d’un en-tête précompilé et affecter le reste d’une compilation qui utilise l’en-tête précompilé :

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Règles de cohérence pour /Yc et /Yu

Lorsque vous utilisez un en-tête précompilé créé à l’aide de /Yc ou/Yu, le compilateur compare l’environnement de compilation actuel à celui qui existait lorsque vous avez créé le fichier PCH. Veillez à spécifier un environnement cohérent avec la précédente (à l’aide des options du compilateur cohérente, des pragmas, etc.) pour la compilation en cours. Si le compilateur détecte une incohérence, il émet un avertissement et identifie l’incohérence lorsque cela est possible. Ces avertissements n’indiquent pas nécessairement un problème avec le fichier PCH ; ils simplement vous Avertissement des éventuels conflits. Les sections suivantes décrivent les exigences de cohérence pour les en-têtes précompilés.

### <a name="compiler-option-consistency"></a>Cohérence des options du compilateur

Ce tableau répertorie les options du compilateur pouvant déclencher un avertissement d’incohérence lors de l’utilisation d’un en-tête précompilé :

|Option|Name|Règle|
|------------|----------|----------|
|/D|Définir des constantes et macros|Doit être le même entre la compilation qui a créé l’en-tête précompilé et la compilation en cours. L’état des constantes définies n’est pas activée, mais des résultats imprévisibles peuvent se produire si vos fichiers dépendent des valeurs des constantes modifiées.|
|/E ou /EP|Copie la sortie du préprocesseur vers la sortie standard|En-têtes précompilés ne fonctionnent pas avec l’option /E ou /EP.|
|/Fr ou /FR|Générer des informations de l’Explorateur de Source de Microsoft|Pour les options /Fr et /FR soit valide avec l’option/Yu, elles doivent également avoir été en vigueur lors de la création de l’en-tête précompilé. Compilations ultérieures utilisant l’en-tête précompilé génèrent également des informations du navigateur Source. Informations du navigateur sont placées dans un seul fichier .sbr et sont référencées par d’autres fichiers de la même manière que les informations CodeView. Vous ne pouvez pas remplacer le positionnement des informations du navigateur Source.|
|/ GA, /GD, /GE, /Gw ou /GW|Options de protocole Windows|Doit être le même entre la compilation qui a créé l’en-tête précompilé et la compilation en cours. Si ces options diffèrent, un message d’avertissement se produit.|
|/ZI|Générer des informations de débogage complètes|Si cette option est en vigueur lors de la création de l’en-tête précompilé, les compilations ultérieures utilisant la précompilation peuvent utiliser ces informations de débogage. Si/Zi n’est pas en vigueur lors de la création de l’en-tête précompilé, les compilations ultérieures utilisant la précompilation et l’option/Zi déclenchent un avertissement. Les informations de débogage sont placées dans le fichier objet en cours, et les symboles locaux définis dans l’en-tête précompilé ne sont pas disponibles pour le débogueur.|

> [!NOTE]
>  La fonctionnalité en-têtes précompilés est destinée uniquement dans les fichiers sources C et C++.

## <a name="using-precompiled-headers-in-a-project"></a>Utilisation d’en-têtes précompilés dans un projet

Les sections précédentes donnent une vue d’ensemble d’en-têtes précompilés : /Yc et/Yu, l’option/Fp et le [hdrstop](../../preprocessor/hdrstop.md) pragma. Cette section décrit une méthode d’utilisation manuelle des options d’en-tête précompilé dans un projet ; Il se termine par un exemple de makefile et le code qu’il gère.

Pour une autre approche pour utilisation manuelle des options d’en-têtes précompilés dans un projet, étudiez l’un des makefiles situés dans le répertoire MFC\SRC créé lors de l’installation par défaut de Visual C++. Ces fichiers Make adopter une approche similaire à celle présentée dans cette section mais tirer le meilleur parti des macros de NMAKE Microsoft Program Maintenance Utility () et offre un meilleur contrôle du processus de génération.

## <a name="pch-files-in-the-build-process"></a>Fichiers PCH utilisés dans le processus de génération

La base de code d’un projet de logiciel est généralement contenue dans plusieurs fichiers sources, fichiers objets, bibliothèques et fichiers d’en-tête C ou C++. En règle générale, un makefile coordonne la combinaison de ces éléments dans un fichier exécutable. La figure suivante montre la structure d’un makefile qui utilise un fichier d’en-tête précompilé. Les noms des macros NMAKE et les noms de fichiers dans ce diagramme sont cohérents avec ceux de l’exemple de code trouvé dans [exemple de Makefile pour PCH](#sample-makefile-for-pch) et [exemple de Code pour PCH](#example-code-for-pch).

La figure utilise trois appareils schématique pour montrer le flux du processus de génération. Les rectangles nommés représentent chaque fichier ou une macro ; les trois macros représentent un ou plusieurs fichiers. Les zones ombrées représentent chaque action de compilation ou de liaison. Les flèches indiquent les fichiers et les macros sont combinées au cours de la compilation ou d’un processus de liaison.

![Structure d’un makefile qui utilise un fichier d’en-tête précompilé](../../build/reference/media/vc30ow1.gif "Structure d’un makefile qui utilise un fichier d’en-tête précompilé") <br/>
Structure d’un Makefile qui utilise un fichier d’en-tête précompilé

En haut du diagramme, STABLEHDRS et limite sont des macros NMAKE dans lequel vous ne listez pas susceptible d’avoir besoin de recompilation des fichiers. Ces fichiers sont compilés par la chaîne de commande

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

uniquement si le fichier d’en-tête précompilé (STABLE.pch) n’existe pas ou si vous apportez des modifications aux fichiers répertoriées dans les deux macros. Dans les deux cas, le fichier d’en-tête précompilé contiendra le code uniquement à partir des fichiers répertoriés dans la macro STABLEHDRS. Répertorie le dernier fichier que vous souhaitez dans la macro de limite.

Les fichiers que vous spécifiez dans ces macros peuvent être soit des fichiers d’en-tête ou des fichiers source C ou C++. (Un seul fichier PCH ne peut pas être utilisé avec des modules C et C++.) Notez que vous pouvez utiliser la **hdrstop** macro pour arrêter la précompilation à un moment donné dans le fichier de la frontière. Consultez [hdrstop](../../preprocessor/hdrstop.md) pour plus d’informations.

Continuer vers le bas le diagramme, APPLIB.obj représente le code de prise en charge utilisé dans votre application finale. Il est créé à partir de APPLIB.cpp, les fichiers répertoriés dans la macro UNSTABLEHDRS et code précompilé à partir de l’en-tête précompilé.

MYAPP.obj représente votre application finale. Il est créé à partir de MYAPP.cpp, les fichiers répertoriés dans la macro UNSTABLEHDRS et code précompilé à partir de l’en-tête précompilé.

Enfin, le fichier exécutable (MYAPP. (EXE) est créé en liant les fichiers répertoriés dans la macro obj (APPLIB.obj et MYAPP.obj).

## <a name="sample-makefile-for-pch"></a>Exemple de makefile pour PCH

Le makefile suivant utilise des macros et un ! IF ! AUTRE ! Structure de commande de flux de contrôle ENDIF pour simplifier son adaptation à votre projet.

```NMAKE
# Makefile : Illustrates the effective use of precompiled
#            headers in a project
# Usage:     NMAKE option
# option:    DEBUG=[0|1]
#            (DEBUG not defined is equivalent to DEBUG=0)
#
OBJS = myapp.obj applib.obj
# List all stable header files in the STABLEHDRS macro.
STABLEHDRS = stable.h another.h
# List the final header file to be precompiled here:
BOUNDRY = stable.h
# List header files under development here:
UNSTABLEHDRS = unstable.h
# List all compiler options common to both debug and final
# versions of your code here:
CLFLAGS = /c /W3
# List all linker options common to both debug and final
# versions of your code here:
LINKFLAGS = /NOD /ONERROR:NOEXE
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi /f
LINKFLAGS = $(LINKFLAGS) /COD
LIBS      = slibce
!ELSE
CLFLAGS   = $(CLFLAGS) /Oselg /Gs
LINKFLAGS = $(LINKFLAGS)
LIBS      = slibce
!ENDIF
myapp.exe: $(OBJS)
    link $(LINKFLAGS) @<<
$(OBJS), myapp, NUL, $(LIBS), NUL;
<<
# Compile myapp
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp
# Compile applib
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp
# Compile headers
stable.pch : $(STABLEHDRS)
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp
```

Des macros STABLEHDRS, limite et UNSTABLEHDRS illustrée dans la figure « Structure d’un Makefile qu’utilise un fichier d’en-tête précompilé » [fichiers PCH utilisés dans le processus de génération](#pch-files-in-the-build-process), ce makefile fournit une macro CLFLAGS et une LINKFLAGS macro. Vous devez utiliser ces macros pour répertorier les options du compilateur et éditeur de liens qui s’appliquent si vous générez un débogage ou la version finale du fichier exécutable de l’application. Il existe également une macro LIBS où vous répertoriez les bibliothèques de votre projet a besoin.

Le makefile utilise également ! IF ! AUTRE ! ENDIF afin de déterminer si vous définissez un symbole de débogage sur la ligne de commande NMAKE :

```NMAKE
NMAKE DEBUG=[1|0]
```

Cette fonctionnalité rend possible que vous pouvez utiliser le même makefile pendant le développement et pour les versions finales de votre programme, utilisez le débogage = 0 pour les versions finales. Les lignes de commande suivantes sont équivalentes :

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Pour plus d’informations sur les makefiles, consultez [Référence NMAKE](../../build/nmake-reference.md). Consultez également [Options du compilateur](../../build/reference/compiler-options.md) et [les Options de l’éditeur de liens](../../build/reference/linker-options.md).

## <a name="example-code-for-pch"></a>Exemple de code pour PCH

Les fichiers sources suivants sont utilisés dans le makefile décrit dans [fichiers PCH utilisés dans le processus de génération](#pch-files-in-the-build-process) et [exemple de Makefile pour PCH](#sample-makefile-for-pch). Notez que les commentaires contiennent des informations importantes.

```cpp
// ANOTHER.H : Contains the interface to code that is not
//             likely to change.
//
#ifndef __ANOTHER_H
#define __ANOTHER_H
#include<iostream>
void savemoretime( void );
#endif // __ANOTHER_H
```

```cpp
// STABLE.H : Contains the interface to code that is not likely
//            to change. List code that is likely to change
//            in the makefile's STABLEHDRS macro.
//
#ifndef __STABLE_H
#define __STABLE_H
#include<iostream>
void savetime( void );
#endif // __STABLE_H
```

```cpp
// UNSTABLE.H : Contains the interface to code that is
//              likely to change. As the code in a header
//              file becomes stable, remove the header file
//              from the makefile's UNSTABLEHDR macro and list
//              it in the STABLEHDRS macro.
//
#ifndef __UNSTABLE_H
#define __UNSTABLE_H
#include<iostream.h>
void notstable( void );
#endif // __UNSTABLE_H
```

```cpp
// APPLIB.CPP : This file contains the code that implements
//              the interface code declared in the header
//              files STABLE.H, ANOTHER.H, and UNSTABLE.H.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
// The following code represents code that is deemed stable and
// not likely to change. The associated interface code is
// precompiled. In this example, the header files STABLE.H and
// ANOTHER.H are precompiled.
void savetime( void )
    { cout << "Why recompile stable code?\n"; }
void savemoretime( void )
    { cout << "Why, indeed?\n\n"; }
// The following code represents code that is still under
// development. The associated header file is not precompiled.
void notstable( void )
    { cout << "Unstable code requires"
            << " frequent recompilation.\n";
    }
```

```cpp
// MYAPP.CPP : Sample application
//             All precompiled code other than the file listed
//             in the makefile's BOUNDRY macro (stable.h in
//             this example) must be included before the file
//             listed in the BOUNDRY macro. Unstable code must
//             be included after the precompiled code.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
int main( void )
{
    savetime();
    savemoretime();
    notstable();
}
```

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)