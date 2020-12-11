---
description: 'En savoir plus sur : fichiers d’en-tête précompilés'
title: Fichiers d'en-tête précompilés
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 9f3d6847043f988f4b0ef57df9b1558c1cd5655c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163130"
---
# <a name="precompiled-header-files"></a>Fichiers d'en-tête précompilés

Lorsque vous créez un projet dans Visual Studio, un *fichier d’en-tête précompilé* nommé *pch. h* est ajouté au projet. (Dans Visual Studio 2017 et versions antérieures, le fichier était appelé *stdafx. h*.) L’objectif du fichier est d’accélérer le processus de génération. Tous les fichiers d’en-tête stables, par exemple les en-têtes de bibliothèque standard tels que `<vector>` , doivent être inclus ici. L’en-tête précompilé est compilé uniquement quand celui-ci, ou les fichiers qu’il contient, sont modifiés. Si vous apportez uniquement des modifications dans le code source de votre projet, la génération ignorera la compilation pour l’en-tête précompilé.

Les options du compilateur pour les en-têtes précompilés sont [/y](reference/y-precompiled-headers.md). Dans les pages de propriétés du projet, les options se trouvent sous **Propriétés de Configuration > C/C++ > en-têtes précompilés**. Vous pouvez choisir de ne pas utiliser d’en-têtes précompilés, et vous pouvez spécifier le nom du fichier d’en-tête, ainsi que le nom et le chemin d’accès du fichier de sortie.

## <a name="custom-precompiled-code"></a>Code précompilé personnalisé

Pour les grands projets dont la génération prend beaucoup de temps, vous pouvez envisager de créer des fichiers précompilés personnalisés. Les compilateurs Microsoft C et C++ offrent des options pour la précompilation du code en C ou C++, y compris du code incorporé. Grâce à cela, vous pouvez compiler un corps de code stable, stocker l'état compilé du code dans un fichier et, lors des compilations suivantes, combiner le code précompilé avec du code qui est toujours en cours de développement. Les compilations ultérieures sont plus rapides, car le code stable n'a pas besoin d'être recompilé.

## <a name="when-to-precompile-source-code"></a>Quand précompiler le code source

Le code précompilé est utile pendant le cycle de développement afin de réduire le temps de compilation, en particulier dans les cas suivants :

- Vous utilisez toujours un grand corps de code qui change rarement.

- Votre programme comprend plusieurs modules, qui utilisent tous un ensemble standard de fichiers include et les mêmes options de compilation. Dans ce cas, tous les fichiers include peuvent être précompilés dans un en-tête précompilé.

La première compilation, celle qui crée le fichier d’en-tête précompilé (PCH), prend un peu plus de temps que les compilations suivantes. Les compilations ultérieures peuvent se poursuivre plus rapidement en incluant le code précompilé.

Vous pouvez précompiler les programmes C et C++. En programmation C++, il est courant de séparer les informations de l’interface de classe en fichiers d’en-tête. Ces fichiers d’en-tête peuvent être inclus ultérieurement dans les programmes qui utilisent la classe. En précompilant ces en-têtes, vous pouvez réduire le temps nécessaire à la compilation d’un programme.

> [!NOTE]
> Même si vous ne pouvez utiliser qu’un seul fichier d’en-tête précompilé (. pch) par fichier source, vous pouvez utiliser plusieurs fichiers. pch dans un projet.

## <a name="two-choices-for-precompiling-code"></a>Deux méthodes au choix pour la précompilation du code

Vous pouvez précompiler tout code C ou C++. vous n’êtes pas limité à la précompilation des fichiers d’en-tête uniquement.

La précompilation nécessite une planification, mais elle offre des compilations beaucoup plus rapides si vous précompilez du code source autre que des fichiers d’en-tête simples.

Précompilez le code lorsque vous savez que vos fichiers sources utilisent des ensembles communs de fichiers d’en-tête, mais que vous ne les incluez pas dans le même ordre ou lorsque vous souhaitez inclure du code source dans votre précompilation.

Les options d’en-tête précompilé sont [/Yc (créer un fichier d’en-tête précompilé)](reference/yc-create-precompiled-header-file.md) et [/Yu (utiliser un fichier d’en-tête précompilé)](reference/yu-use-precompiled-header-file.md). Utilisez **/Yc** pour créer un en-tête précompilé. Lorsqu’il est utilisé avec le pragma [hdrstop](../preprocessor/hdrstop.md) facultatif, **/Yc** vous permet de précompiler les fichiers d’en-tête et le code source. Sélectionnez **/Yu** pour utiliser un en-tête précompilé existant dans la compilation existante. Vous pouvez également utiliser **/FP** avec les options **/Yc** et **/Yu** pour fournir un autre nom pour l’en-tête précompilé.

Les rubriques de référence de l’option du compilateur pour **/Yu** et **/Yc** expliquent comment accéder à cette fonctionnalité dans l’environnement de développement.

## <a name="precompiled-header-consistency-rules"></a>Règles de cohérence s’appliquant aux en-têtes précompilés

Étant donné que les fichiers PCH contiennent des informations sur l’environnement de l’ordinateur ainsi que des informations d’adresse mémoire sur le programme, vous devez utiliser uniquement un fichier PCH sur l’ordinateur sur lequel il a été créé.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Règles de cohérence pour l'utilisation d'en-têtes précompilés par fichier

L’option du compilateur [/Yu](reference/yu-use-precompiled-header-file.md) vous permet de spécifier le fichier PCH à utiliser.

Quand vous utilisez un fichier PCH, le compilateur suppose qu’il s’agit du même environnement de compilation (un qui utilise des options de compilateur cohérentes, des pragmas, etc.) qui était en vigueur lors de la création du fichier PCH, sauf indication contraire. Si le compilateur détecte une incohérence, il émet un avertissement et identifie l’incohérence dans la mesure du possible. Ces avertissements n’indiquent pas nécessairement un problème avec le fichier PCH ; ils vous avertissent simplement des éventuels conflits. Les exigences de cohérence pour les fichiers PCH sont décrites dans les sections suivantes.

### <a name="compiler-option-consistency"></a>Cohérence des options du compilateur

Les options de compilateur suivantes peuvent déclencher un avertissement d’incohérence lors de l’utilisation d’un fichier PCH :

- Les macros créées à l’aide de l’option de préprocesseur (/D) doivent être identiques entre la compilation qui a créé le fichier PCH et la compilation en cours. L’état des constantes définies n’est pas vérifié, mais des résultats imprévisibles peuvent se produire en cas de modification.

- Les fichiers PCH ne fonctionnent pas avec les options/E et/EP.

- Les fichiers PCH doivent être créés à l’aide de l’option générer des informations de consultation (/FR) ou de l’option exclure les variables locales avant que les compilations ultérieures qui utilisent le fichier PCH puissent utiliser ces options.

### <a name="c-70-compatible-z7"></a>C 7,0-compatible (/Z7)

Si cette option est activée lors de la création du fichier PCH, les compilations ultérieures qui utilisent le fichier PCH peuvent utiliser les informations de débogage.

Si l’option C 7,0-compatible (/Z7) n’est pas activée lors de la création du fichier PCH, les compilations ultérieures qui utilisent le fichier PCH et/Z7 déclenchent un avertissement. Les informations de débogage sont placées dans le fichier. obj en cours et les symboles locaux définis dans le fichier PCH ne sont pas disponibles pour le débogueur.

### <a name="include-path-consistency"></a>Inclure la cohérence du chemin

Un fichier PCH ne contient pas d’informations sur le chemin d’accès include qui était en vigueur lors de sa création. Quand vous utilisez un fichier PCH, le compilateur utilise toujours le chemin d’accès include spécifié dans la compilation actuelle.

### <a name="source-file-consistency"></a>Cohérence des fichiers sources

Lorsque vous spécifiez l’option utiliser le fichier d’en-tête précompilé (/Yu), le compilateur ignore toutes les directives de préprocesseur (y compris les pragmas) qui s’affichent dans le code source qui sera précompilé. La compilation spécifiée par ces directives de préprocesseur doit être identique à la compilation utilisée pour l’option créer un fichier d’en-tête précompilé (/YC).

### <a name="pragma-consistency"></a>Cohérence des pragmas

Les pragmas traités lors de la création d’un fichier PCH affectent généralement le fichier avec lequel le fichier PCH est utilisé par la suite. Les `comment` `message` Pragmas et n’affectent pas le reste de la compilation.

Ces pragmas affectent uniquement le code dans le fichier PCH ; ils n’affectent pas le code qui utilise par la suite le fichier PCH :

:::row:::
   :::column span="":::
      `comment`\
      `linesize`
   :::column-end:::
   :::column span="":::
      `message`\
      `page`
   :::column-end:::
   :::column span="":::
      `pagesize`\
      `skip`
   :::column-end:::
   :::column span="":::
      `subtitle`\
      `title`
   :::column-end:::
:::row-end:::

Ces pragmas sont conservés dans le cadre d’un en-tête précompilé et affectent le reste d’une compilation qui utilise l’en-tête précompilé :

:::row:::
   :::column span="":::
      `alloc_text`\
      `auto_inline`\
      `check_stack`\
      `code_seg`\
      `data_seg`
   :::column-end:::
   :::column span="":::
      `function`\
      `include_alias`\
      `init_seg`\
      `inline_depth`
   :::column-end:::
   :::column span="":::
      `inline_recursion`\
      `intrinsic`\
      `optimize`\
      `pack`
   :::column-end:::
   :::column span="":::
      `pointers_to_members`\
      `setlocale`\
      `vtordisp`\
      `warning`
   :::column-end:::
:::row-end:::

## <a name="consistency-rules-for-yc-and-yu"></a>Règles de cohérence pour /Yc et /Yu

Quand vous utilisez un en-tête précompilé créé à l’aide de/YC ou/Yu, le compilateur compare l’environnement de compilation actuel à celui qui existait lors de la création du fichier PCH. Veillez à spécifier un environnement cohérent avec le précédent (à l’aide d’options de compilateur cohérentes, de pragmas, etc.) pour la compilation en cours. Si le compilateur détecte une incohérence, il émet un avertissement et identifie l’incohérence dans la mesure du possible. Ces avertissements n’indiquent pas nécessairement un problème avec le fichier PCH ; ils vous avertissent simplement des éventuels conflits. Les sections suivantes expliquent les exigences de cohérence pour les en-têtes précompilés.

### <a name="compiler-option-consistency"></a>Cohérence des options du compilateur

Ce tableau répertorie les options du compilateur qui peuvent déclencher un avertissement d’incohérence lors de l’utilisation d’un en-tête précompilé :

|Option|Nom|Règle|
|------------|----------|----------|
|/D|Définir des constantes et des macros|Doit être identique entre la compilation qui a créé l’en-tête précompilé et la compilation en cours. L’état des constantes définies n’est pas vérifié, mais des résultats imprévisibles peuvent se produire si vos fichiers dépendent des valeurs des constantes modifiées.|
|/E ou/EP|Copier la sortie du préprocesseur vers la sortie standard|Les en-têtes précompilés ne fonctionnent pas avec l’option/E ou/EP.|
|/Fr ou/FR|Générer les informations du navigateur source Microsoft|Pour que les options/fr et/FR soient valides avec l’option/Yu, elles doivent également être appliquées lors de la création de l’en-tête précompilé. Les compilations suivantes qui utilisent l’en-tête précompilé génèrent également des informations sur le navigateur source. Les informations du navigateur sont placées dans un seul fichier. SBR et sont référencées par d’autres fichiers de la même manière que les informations CodeView. Vous ne pouvez pas remplacer le placement des informations du navigateur source.|
|/GA,/GD,/GE,/GW ou/GW|Options de protocole Windows|Doit être identique entre la compilation qui a créé l’en-tête précompilé et la compilation en cours. Si ces options diffèrent, un message d’avertissement est obtenu.|
|/Zi|Générer des informations de débogage complètes|Si cette option est activée lors de la création de l’en-tête précompilé, les compilations ultérieures qui utilisent la précompilation peuvent utiliser ces informations de débogage. Si/ZI n’est pas activé lors de la création de l’en-tête précompilé, les compilations suivantes qui utilisent la précompilation et l’option/Zi déclenchent un avertissement. Les informations de débogage sont placées dans le fichier objet actuel, et les symboles locaux définis dans l’en-tête précompilé ne sont pas disponibles pour le débogueur.|

> [!NOTE]
> La fonctionnalité d’en-tête précompilé est destinée à être utilisée uniquement dans les fichiers sources C et C++.

## <a name="using-precompiled-headers-in-a-project"></a>Utilisation d'en-têtes précompilés dans un projet

Les sections précédentes présentent une vue d’ensemble des en-têtes précompilés:/Yc et/Yu, l’option/FP et le pragma [hdrstop](../preprocessor/hdrstop.md) . Cette section décrit une méthode permettant d’utiliser les options d’en-tête précompilé manuelles dans un projet. Il se termine par un exemple de Makefile et le code qu’il gère.

Pour une autre approche de l’utilisation des options d’en-tête précompilé manuelles dans un projet, étudiez l’un des makefiles situés dans le répertoire MFC\SRC créé lors de l’installation par défaut de Visual Studio. Ces makefiles adoptent une approche similaire à celle présentée dans cette section, mais utilisent davantage les macros de l’utilitaire de maintenance de programme Microsoft (NMAKE) et offrent un meilleur contrôle du processus de génération.

## <a name="pch-files-in-the-build-process"></a>Fichiers PCH utilisés dans le processus de génération

La base de code d’un projet de logiciel est généralement contenue dans plusieurs fichiers sources C ou C++, fichiers objets, bibliothèques et fichiers d’en-tête. En général, un Makefile coordonne la combinaison de ces éléments dans un fichier exécutable. L’illustration suivante montre la structure d’un Makefile qui utilise un fichier d’en-tête précompilé. Les noms de macros NMAKE et les noms de fichiers dans ce diagramme sont cohérents avec ceux de l’exemple de code trouvé dans exemple de [makefile pour PCH](#sample-makefile-for-pch) et [exemple de code pour PCH](#example-code-for-pch).

La figure utilise trois appareils schématique pour afficher le déroulement du processus de génération. Les rectangles nommés représentent chaque fichier ou macro. les trois macros représentent un ou plusieurs fichiers. Les zones ombrées représentent chaque action de compilation ou de liaison. Les flèches indiquent les fichiers et les macros combinés pendant le processus de compilation ou de liaison.

![Structure d’un Makefile qui utilise un fichier d’en-tête précompilé](media/vc30ow1.gif "Structure d’un Makefile qui utilise un fichier d’en-tête précompilé") <br/>
Structure d’un Makefile qui utilise un fichier d’en-tête précompilé

À partir de la partie supérieure du diagramme, les STABLEHDRS et les limites sont des macros NMAKE dans lesquelles vous répertoriez les fichiers qui n’ont probablement pas besoin d’être recompilés. Ces fichiers sont compilés par la chaîne de commande.

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

uniquement si le fichier d’en-tête précompilé (STABLE. pch) n’existe pas ou si vous apportez des modifications aux fichiers listés dans les deux macros. Dans les deux cas, le fichier d’en-tête précompilé ne contiendra du code qu’à partir des fichiers listés dans la macro STABLEHDRS. Répertoriez le dernier fichier que vous souhaitez précompiler dans la macro de LIMITEur.

Les fichiers que vous répertoriez dans ces macros peuvent être des fichiers d’en-tête ou des fichiers sources C ou C++. (Un seul fichier PCH ne peut pas être utilisé avec les modules C et C++.) Notez que vous pouvez utiliser la macro **hdrstop** pour arrêter la précompilation à un moment donné dans le fichier de limite. Pour plus d’informations, consultez [hdrstop](../preprocessor/hdrstop.md) .

En poursuivant le diagramme, APPLIB. obj représente le code de prise en charge utilisé dans votre application finale. Il est créé à partir de APPLIB. cpp, les fichiers listés dans la macro UNSTABLEHDRS et le code précompilé de l’en-tête précompilé.

MYAPP. obj représente votre application finale. Il est créé à partir de MYAPP. cpp, les fichiers listés dans la macro UNSTABLEHDRS et le code précompilé de l’en-tête précompilé.

Enfin, le fichier exécutable (MYAPP.EXE) est créé en liant les fichiers listés dans la macro ne comportaient (APPLIB. objet MYAPP. obj).

## <a name="sample-makefile-for-pch"></a>Exemple de makefile pour PCH

Le Makefile suivant utilise des macros et un ! Si, ! Sinon, ! ENDIF structure de commande Flow-of-Control pour simplifier son adaptation à votre projet.

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

À part les macros de STABLEHDRS, de limite et UNSTABLEHDRS présentées dans la figure « structure d’un Makefile qui utilise un fichier d’en-tête précompilé » dans les [fichiers PCH du processus de génération](#pch-files-in-the-build-process), ce makefile fournit une macro CLFLAGS et une macro LINKFLAGS. Vous devez utiliser ces macros pour répertorier les options du compilateur et de l’éditeur de liens qui s’appliquent si vous générez une version Debug ou une version finale du fichier exécutable de l’application. Il existe également une macro LIBS dans laquelle vous répertoriez les bibliothèques dont votre projet a besoin.

Le Makefile utilise également ! Si, ! Sinon, ! ENDIF pour détecter si vous définissez un symbole de débogage sur la ligne de commande NMAKE :

```NMAKE
NMAKE DEBUG=[1|0]
```

Grâce à cette fonctionnalité, vous pouvez utiliser le même Makefile pendant le développement et pour les versions finales de votre programme. Utilisez DEBUG = 0 pour les versions finales. Les lignes de commande suivantes sont équivalentes :

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Pour plus d’informations sur les Makefiles, consultez la [Référence NMAKE](reference/nmake-reference.md). Consultez également [Options du compilateur MSVC](reference/compiler-options.md) et [options de l’éditeur de liens MSVC](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Exemple de code pour PCH

Les fichiers sources suivants sont utilisés dans le Makefile décrit dans [fichiers PCH dans le processus de génération](#pch-files-in-the-build-process) et [exemple de makefile pour PCH](#sample-makefile-for-pch). Notez que les commentaires contiennent des informations importantes.

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
