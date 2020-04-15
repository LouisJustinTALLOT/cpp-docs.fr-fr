---
title: Fichiers d'en-tête précompilés
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 158301ec3caacced1663892071b17ef2b8f8e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328669"
---
# <a name="precompiled-header-files"></a>Fichiers d'en-tête précompilés

Lorsque vous créez un nouveau projet dans Visual Studio, un *fichier d’en-tête précompilé* nommé *pch.h* est ajouté au projet. (Dans Visual Studio 2017 et plus tôt, le fichier a été appelé *stdafx.h*.) Le but du fichier est d’accélérer le processus de construction. Tous les fichiers d’en-tête stables, par exemple les en-têtes Standard Library tels que `<vector>`, doivent être inclus ici. L’en-tête précalculé n’est compilé que lorsqu’il, ou tous les fichiers qu’il inclut, sont modifiés. Si vous n’effectuez que des modifications dans votre code source de projet, la version sautera la compilation pour l’en-tête précompilé.

Les options de compilateur pour les en-têtes précompilés sont [/Y](reference/y-precompiled-headers.md). Dans les pages de propriété du projet, les options sont situées sous **Configuration Properties > C/Cmd > en-tête précompilés**. Vous pouvez choisir de ne pas utiliser les en-têtes précompilés, et vous pouvez spécifier le nom du fichier d’en-tête et le nom et le chemin du fichier de sortie.

## <a name="custom-precompiled-code"></a>Code précalté personnalisé

Pour les grands projets qui prennent beaucoup de temps à construire, vous pouvez envisager de créer des fichiers précompilés personnalisés. Les compilateurs Microsoft C et C++ offrent des options pour la précompilation du code en C ou C++, y compris du code incorporé. Grâce à cela, vous pouvez compiler un corps de code stable, stocker l'état compilé du code dans un fichier et, lors des compilations suivantes, combiner le code précompilé avec du code qui est toujours en cours de développement. Les compilations ultérieures sont plus rapides, car le code stable n'a pas besoin d'être recompilé.

## <a name="when-to-precompile-source-code"></a>Quand précompiler le code source

Le code précompilé est utile pendant le cycle de développement pour réduire le temps de compilation, surtout si :

- Vous utilisez toujours un grand corps de code qui change rarement.

- Votre programme comprend plusieurs modules, qui utilisent tous un ensemble standard de fichiers inclus et les mêmes options de compilation. Dans ce cas, tous les fichiers comprennent peuvent être précompilés en un en-tête précompilé.

La première compilation — celle qui crée le fichier d’en-tête précompilé (PCH) — prend un peu plus de temps que les compilations ultérieures. Les compilations ultérieures peuvent se dérouler plus rapidement en incluant le code prédécalé.

Vous pouvez pré-compiler les programmes C et CMD. Dans la programmation CD, il est courant de séparer les informations d’interface de classe en fichiers d’en-tête. Ces fichiers d’en-tête peuvent plus tard être inclus dans les programmes qui utilisent la classe. En précomplant ces en-têtes, vous pouvez réduire le temps qu’un programme prend pour compiler.

> [!NOTE]
> Bien que vous ne puissiez utiliser qu’un seul fichier d’en-tête précompilé (.pch) par fichier source, vous pouvez utiliser plusieurs fichiers .pch dans un projet.

## <a name="two-choices-for-precompiling-code"></a>Deux méthodes au choix pour la précompilation du code

Vous pouvez précalculer n’importe quel code C ou CMD ; vous ne vous limitez pas à précompiler uniquement les fichiers d’en-tête.

La précomplation nécessite une planification, mais elle offre des compilations beaucoup plus rapides si vous précomplisez le code source autre que les fichiers d’en-tête simples.

Précompile code lorsque vous savez que vos fichiers sources utilisent des ensembles communs de fichiers d’en-tête, mais ne les incluent pas dans le même ordre, ou lorsque vous souhaitez inclure du code source dans votre précomplération.

Les options d’en-tête précompilées sont [/Yc (Créer le fichier d’en-tête précompilé)](reference/yc-create-precompiled-header-file.md) et [/Yu (Utiliser le fichier d’en-tête précompilé)](reference/yu-use-precompiled-header-file.md). Utilisez **/Yc** pour créer un en-tête précalté. Lorsqu’il est utilisé avec le [pragma hdrstop](../preprocessor/hdrstop.md) en option, **/Yc** vous permet de pré-compiler à la fois les fichiers d’en-tête et le code source. Sélectionnez **/Yu** pour utiliser un en-tête précompilé existant dans la compilation existante. Vous pouvez également utiliser **/Fp** avec les options **/Yc** et **/Yu** pour fournir un nom alternatif pour l’en-tête précompilé.

Les sujets de référence d’option de compilateur pour **/Yu** et **/Yc** discutent de la façon d’accéder à cette fonctionnalité dans l’environnement de développement.

## <a name="precompiled-header-consistency-rules"></a>Règles de cohérence s’appliquant aux en-têtes précompilés

Étant donné que les fichiers PCH contiennent des informations sur l’environnement de la machine ainsi que des informations d’adresse mémoire sur le programme, vous ne devez utiliser un fichier PCH sur la machine où il a été créé.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Règles de cohérence pour l'utilisation d'en-têtes précompilés par fichier

[L’option compilateur /Yu](reference/yu-use-precompiled-header-file.md) vous permet de spécifier le fichier PCH à utiliser.

Lorsque vous utilisez un fichier PCH, le compilateur suppose le même environnement de compilation - celui qui utilise des options de compilateur cohérente, pragmas, et ainsi de suite - qui était en vigueur lorsque vous avez créé le fichier PCH, sauf si vous spécifiez le contraire. Si le compilateur détecte une incohérence, il émet un avertissement et identifie l’incohérence dans la mesure du possible. De tels avertissements n’indiquent pas nécessairement un problème avec le fichier PCH; ils vous avertissent simplement d’éventuels conflits. Les exigences de cohérence pour les fichiers PCH sont décrites dans les sections suivantes.

### <a name="compiler-option-consistency"></a>Cohérence de l’option Compilateur

Les options de compilateur suivantes peuvent déclencher un avertissement d’incohérence lors de l’utilisation d’un fichier PCH :

- Les macros créées à l’aide de l’option Preprocessor (/D) doivent être les mêmes entre la compilation qui a créé le fichier PCH et la compilation actuelle. L’état des constantes définies n’est pas vérifié, mais des résultats imprévisibles peuvent se produire si ces changements.

- Les fichiers PCH ne fonctionnent pas avec les options /E et/EP.

- Les fichiers PCH doivent être créés en utilisant l’option Generate Browse Info (/FR) ou l’option Exclure les variables locales (/Fr) avant que les compilations ultérieures qui utilisent le fichier PCH puissent utiliser ces options.

### <a name="c-70-compatible-z7"></a>C 7.0-Compatible (/Z7)

Si cette option est en vigueur lors de la création du fichier PCH, les compilations ultérieures qui utilisent le fichier PCH peuvent utiliser les informations de débogage.

Si l’option C 7.0-Compatible (/Z7) n’est pas en vigueur lors de la création du fichier PCH, les compilations ultérieures qui utilisent le fichier PCH et /Z7 déclenchent un avertissement. Les informations de débogage sont placées dans le fichier actuel .obj, et les symboles locaux définis dans le fichier PCH ne sont pas disponibles pour le débogage.

### <a name="include-path-consistency"></a>Inclure la cohérence du chemin

Un fichier PCH ne contient pas d’informations sur le chemin inclus qui était en vigueur lors de sa création. Lorsque vous utilisez un fichier PCH, le compilateur utilise toujours le chemin inclus spécifié dans la compilation actuelle.

### <a name="source-file-consistency"></a>Cohérence du fichier source

Lorsque vous spécifiez l’option Fichier d’en-tête précompilé d’utilisation (/Yu), le compilateur ignore toutes les directives de préprocesseur (y compris les pragmas) qui apparaissent dans le code source qui sera précompilé. La compilation spécifiée par ces directives de préprocesseur doit être la même que la compilation utilisée pour l’option Fichier d’en-tête précompilé Create (/Yc).

### <a name="pragma-consistency"></a>Cohérence Pragma

Les pragmas traités lors de la création d’un fichier PCH affectent habituellement le fichier avec lequel le fichier PCH est ensuite utilisé. Les `comment` `message` pragmas et les pragmas n’affectent pas le reste de la compilation.

Ces pragmas n’affectent que le code dans le fichier PCH; ils n’affectent pas le code qui utilise par la suite le fichier PCH :

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Ces pragmas sont conservés dans le cadre d’un en-tête précompilé, et affectent le reste d’une compilation qui utilise l’en-tête précompilé:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Règles de cohérence pour /Yc et /Yu

Lorsque vous utilisez un en-tête précompilé créé à l’aide de /Yc ou /Yu, le compilateur compare l’environnement de compilation actuel à celui qui existait lorsque vous avez créé le fichier PCH. Assurez-vous de spécifier un environnement compatible avec le précédent (à l’aide d’options de compilateur cohérentes, de pragmas, etc.) pour la compilation en cours. Si le compilateur détecte une incohérence, il émet un avertissement et identifie l’incohérence dans la mesure du possible. De tels avertissements n’indiquent pas nécessairement un problème avec le fichier PCH; ils vous avertissent simplement d’éventuels conflits. Les sections suivantes expliquent les exigences de cohérence pour les en-têtes précompilés.

### <a name="compiler-option-consistency"></a>Cohérence de l’option Compilateur

Ce tableau répertorie les options de compilateur qui pourraient déclencher un avertissement d’incohérence lors de l’utilisation d’un en-tête précompilé :

|Option|Nom|Règle|
|------------|----------|----------|
|/D|Décrivez les constantes et les macros|Doit être le même entre la compilation qui a créé l’en-tête précompilé et la compilation actuelle. L’état des constantes définies n’est pas vérifié, mais des résultats imprévisibles peuvent se produire si vos fichiers dépendent des valeurs des constantes modifiées.|
|/E ou /EP|Copier la sortie du préprocesseur à la sortie standard|Les en-têtes précompilés ne fonctionnent pas avec l’option /E ou/EP.|
|/Fr ou /FR|Générer des informations sur microsoft Source Browser|Pour que les options /Fr et/FR soient valables avec l’option /Yu, elles doivent également avoir été en vigueur lors de la création de l’en-tête précompilé. Les compilations ultérieures qui utilisent l’en-tête précompilé génèrent également des informations source de navigateur. Les informations du navigateur sont placées dans un seul fichier .sbr et sont référencées par d’autres fichiers de la même manière que les informations CodeView. Vous ne pouvez pas remplacer le placement des informations Source Browser.|
|/GA, /GD, /GE, /Gw, ou /GW|Options de protocole Windows|Doit être le même entre la compilation qui a créé l’en-tête précompilé et la compilation actuelle. Si ces options diffèrent, un message d’avertissement en résulte.|
|/Zi|Générer des informations complètes de débogage|Si cette option est en vigueur lorsque l’en-tête précompilé est créé, les compilations ultérieures qui utilisent la précomplation peuvent utiliser cette information de débogage. Si /Zi n’est pas en vigueur lorsque l’en-tête précompilé est créé, les compilations ultérieures qui utilisent la précomplération et l’option /Zi déclenchent un avertissement. Les informations de débogage sont placées dans le fichier d’objet actuel, et les symboles locaux définis dans l’en-tête précompilé ne sont pas disponibles pour le débogage.|

> [!NOTE]
> L’installation d’en-tête précomposée n’est destinée qu’aux fichiers source C et CMD.

## <a name="using-precompiled-headers-in-a-project"></a>Utilisation d'en-têtes précompilés dans un projet

Les sections précédentes présentent un aperçu des en-têtes précompilés : /Yc et /Yu, l’option /Fp, et le [pragma hdrstop.](../preprocessor/hdrstop.md) Cette section décrit une méthode d’utilisation des options manuelles en tête précalculée dans un projet; il se termine par un exemple makefile et le code qu’il gère.

Pour une autre approche à l’utilisation des options manuelles précompilées-en-tête dans un projet, étudiez l’un des makefiles situés dans l’annuaire MFC-SRC qui est créé lors de la configuration par défaut de Visual Studio. Ces makefiles adoptent une approche similaire à celle présentée dans cette section, mais font un meilleur usage des macros Microsoft Program Maintenance Utility (NMAKE), et offrent un meilleur contrôle du processus de construction.

## <a name="pch-files-in-the-build-process"></a>Fichiers PCH utilisés dans le processus de génération

La base de code d’un projet logiciel est généralement contenue dans plusieurs fichiers de source C ou C, fichiers d’objets, bibliothèques et fichiers d’en-tête. En règle générale, un makefile coordonne la combinaison de ces éléments dans un fichier exécutable. La figure suivante montre la structure d’un makefile qui utilise un fichier d’en-tête précompilé. Les noms macro NMAKE et les noms de fichiers dans ce diagramme sont compatibles avec ceux du code d’exemple trouvé dans [Sample Makefile pour PCH](#sample-makefile-for-pch) et [Code d’exemple pour PCH](#example-code-for-pch).

La figure utilise trois dispositifs schématiques pour afficher le flux du processus de construction. Les rectangles nommés représentent chaque fichier ou macro; les trois macros représentent un ou plusieurs fichiers. Les zones ombragées représentent chaque action compilée ou lier. Les flèches montrent quels fichiers et macros sont combinés au cours de la compilation ou du processus de liaison.

![Structure d’un makefile qui utilise un fichier d’en-tête précalté](media/vc30ow1.gif "Structure d’un makefile qui utilise un fichier d’en-tête précalté") <br/>
Structure d’un Makefile qui utilise un fichier d’en-tête précompilé

En commençant par le haut du diagramme, STABLEHDRS et BOUNDRY sont des macros NMAKE dans lesquels vous énumérez les fichiers qui n’ont probablement pas besoin d’être compilés. Ces fichiers sont compilés par la chaîne de commande

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

seulement si le fichier d’en-tête précompilé (STABLE.pch) n’existe pas ou si vous modifiez les fichiers énumérés dans les deux macros. Dans les deux cas, le fichier d’en-tête précompilé ne contiendra du code que des fichiers énumérés dans la macro STABLEHDRS. Énumérez le dernier fichier que vous souhaitez précompiler dans la macro BOUNDRY.

Les fichiers que vous inscrivez dans ces macros peuvent être des fichiers d’en-tête ou des fichiers source C ou C. (Un seul fichier PCH ne peut pas être utilisé avec les modules C et C.) Notez que vous pouvez utiliser la macro **hdrstop** pour arrêter la précomplation à un moment donné dans le fichier BOUNDRY. Voir [hdrstop](../preprocessor/hdrstop.md) pour plus d’informations.

Poursuivant le diagramme, APPLIB.obj représente le code de support utilisé dans votre application finale. Il est créé à partir d’APPLIB.cpp, les fichiers répertoriés dans la macro UNSTABLEHDRS, et le code précompilé à partir de l’en-tête précompilé.

MYAPP.obj représente votre application finale. Il est créé à partir de MYAPP.cpp, les fichiers énumérés dans la macro UNSTABLEHDRS, et le code précompilé à partir de l’en-tête précompilé.

Enfin, le fichier exécutable (MYAPP. EXE) est créé en reliant les fichiers répertoriés dans la macro OBJS (APPLIB.obj et MYAPP.obj).

## <a name="sample-makefile-for-pch"></a>Exemple de makefile pour PCH

Le makefile suivant utilise des macros et un ! Si! Autre! Structure de commande de flux de contrôle ENDIF pour simplifier son adaptation à votre projet.

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
LINKFLAGS = /nologo
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi
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

Mis à part les macros STABLEHDRS, BOUNDRY et UNSTABLEHDRS indiqués dans la figure « Structure d’un Makefile qui utilise un fichier d’en-tête précompilé » dans [les fichiers PCH dans le processus de construction,](#pch-files-in-the-build-process)ce makefile fournit une macro CLFLAGS et une macro LINKFLAGS. Vous devez utiliser ces macros pour répertorier les options de compilateur et de liaison qui s’appliquent si vous construisez un débbug ou une version finale du fichier exécutable de l’application. Il y a également une macro LIBS où vous dressez la liste des bibliothèques dont votre projet a besoin.

Le makefile utilise également ! Si! Autre! ENDIF pour détecter si vous définissez un symbole DEBUG sur la ligne de commande NMAKE :

```NMAKE
NMAKE DEBUG=[1|0]
```

Cette fonctionnalité vous permet d’utiliser le même makefile pendant le développement et pour les versions finales de votre programme — utilisez DEBUG-0 pour les versions finales. Les lignes de commande suivantes sont équivalentes :

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Pour plus d’informations sur les makefiles, voir [NMAKE Reference](reference/nmake-reference.md). Voir également [MSVC Compiler Options](reference/compiler-options.md) et les [options MSVC Linker](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Exemple de code pour PCH

Les fichiers sources suivants sont utilisés dans le makefile décrit dans [les fichiers PCH dans le processus de construction](#pch-files-in-the-build-process) et le [makefile d’échantillon pour PCH](#sample-makefile-for-pch). Notez que les commentaires contiennent des informations importantes.

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
#include<iostream>
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
using namespace std;
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

[Référence à la génération C/C++](reference/c-cpp-building-reference.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
