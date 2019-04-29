---
title: /D (Définitions de préprocesseur)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
ms.openlocfilehash: 18bbdb980c63b3c04b432602afb2402c5e2c42e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293964"
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

**CL /D__far=  TEST.C**

Le **CL** variable d’environnement ne peut pas être définie sur une chaîne qui contient le signe égal. Pour utiliser **/D** conjointement avec la **CL** environnement variable, vous devez spécifier le signe dièse au lieu du signe égal :

```
SET CL=/DTEST#0
```

Lorsque vous définissez un symbole de prétraitement à l'invite de commandes, tenez compte des règles d'analyse du compilateur et des règles d'analyse du shell. Par exemple, pour définir un symbole de prétraitement sur le signe de pourcentage (%) dans votre programme, spécifiez les caractères de signe de deux pour cent (%) à l’invite de commandes : Si vous ne spécifiez qu’un seul, une erreur d’analyse est émise.

```
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

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

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/U, /u (Annuler la définition de symboles)](u-u-undefine-symbols.md)<br/>
[#undef, directive (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br/>
[#define, directive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
