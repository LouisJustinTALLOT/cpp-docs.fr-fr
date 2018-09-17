---
title: -D (définitions de préprocesseur) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
dev_langs:
- C++
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19da0c8e29a27734b23a01a1b2d3ffaa64a7fe05
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713791"
---
# <a name="d-preprocessor-definitions"></a>/D (Définitions de préprocesseur)

Définit un symbole de prétraitement pour un fichier source.

## <a name="syntax"></a>Syntaxe

```
/Dname[= | # [{string | number}] ]
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser ce symbole avec `#if` ou `#ifdef` pour effectuer une compilation conditionnelle du code source. La définition du symbole reste en vigueur jusqu'à ce qu'elle soit redéfinie ou annulée dans le code par la directive `#undef`.

**/D** a le même effet que la `#define` directive au début d’un fichier de code source, à ceci près que **/D** supprime les guillemets sur la ligne de commande et `#define` les conserve.

Par défaut, la valeur associée à un symbole est 1. Par exemple, **/D** `name` équivaut à **/D**`name`**= 1**. Dans l’exemple à la fin de cet article, la définition de **TEST** affiche `1`.

Compilation à l’aide **/D** `name` **=** , n’ont aucune valeur associée au symbole. Bien que le symbole puisse toujours être utilisé pour effectuer une compilation de code conditionnelle, il ne retourne rien. Dans l’exemple, si vous compilez à l’aide de **DTEST =**, une erreur se produit. Ce comportement ressemble à l'utilisation de `#define` avec ou sans valeur.

Cette commande définit le symbole DEBUG dans TEST.c:

**CL /DDEBUG TEST. C**

Cette commande supprime toutes les occurrences du mot clé `__far` dans TEST.c :

**CL /D__far = TEST. C**

Le **CL** variable d’environnement ne peut pas être définie sur une chaîne qui contient le signe égal. Pour utiliser **/D** conjointement avec la **CL** environnement variable, vous devez spécifier le signe dièse au lieu du signe égal :

```
SET CL=/DTEST#0
```

Lorsque vous définissez un symbole de prétraitement à l'invite de commandes, tenez compte des règles d'analyse du compilateur et des règles d'analyse du shell. Par exemple, pour définir le symbole de prétraitement pourcentage (%) dans votre programme, spécifiez deux caractères pourcentage (%%) à l'invite de commandes : si vous n'en spécifiez qu'un seul, une erreur d'analyse est émise.

```
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Dans le volet gauche, sélectionnez **propriétés de Configuration**, **C/C++**, **préprocesseur**.

1. Dans le volet droit, dans la colonne de droite de la **définitions de préprocesseur** propriété, ouvrez le menu déroulant et choisissez **modifier**.

1. Dans le **définitions de préprocesseur** boîte de dialogue, ajouter (un par ligne), modifier ou supprimer une ou plusieurs définitions. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Exemple

```
// cpp_D_compiler_option.cpp
// compile with: /DTEST
#include <stdio.h>

int main( )
{
    #ifdef TEST
        printf_s("TEST defined %d\n", TEST);
    #else
        printf_s("TEST not defined\n");
    #endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[/ U, /u (annuler la définition des symboles)](../../build/reference/u-u-undefine-symbols.md)
[#undef Directive (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)
[#define, Directive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)