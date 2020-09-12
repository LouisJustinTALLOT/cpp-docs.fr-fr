---
title: /D (Définitions de préprocesseur)
ms.date: 09/18/2019
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
ms.openlocfilehash: 7c8a500820c8cc4655c409f4628d72a69acafa5a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040936"
---
# <a name="d-preprocessor-definitions"></a>/D (Définitions de préprocesseur)

Définit un symbole de prétraitement pour un fichier source.

## <a name="syntax"></a>Syntaxe

> **/D** \[ ]_Name_ \[ `=` \| `#` \[ { *chaîne* \| *Number* }]] \
> **/D** \[ ] `"` _Name_ \[ `=` \| `#` \[ { *chaîne* \| *Number* }]]`"`

## <a name="remarks"></a>Remarques

Vous pouvez utiliser ce symbole avec `#if` ou `#ifdef` pour effectuer une compilation conditionnelle du code source. La définition du symbole reste en vigueur jusqu’à ce qu’elle soit redéfinie dans le code ou qu’elle ne soit pas définie dans le code par une `#undef` directive.

**/D** a le même effet qu’une `#define` directive au début d’un fichier de code source. La différence est que **/d** supprime les guillemets sur la ligne de commande et qu’une `#define` directive les conserve. Vous pouvez avoir un espace entre le **/d** et le symbole. Il ne peut pas y avoir d’espace entre le symbole et le signe égal, ni entre le signe égal et toute valeur assignée.

Par défaut, la valeur associée à un symbole est 1. Par exemple, `/D name` équivaut à `/D name=1`. Dans l’exemple à la fin de cet article, la définition de `TEST` est affichée pour impression `1` .

La compilation à l’aide de `/D name=` entraîne l’absence de valeur associée dans le *nom* du symbole. Bien que le symbole puisse toujours être utilisé pour effectuer une compilation de code conditionnelle, il ne retourne rien. Dans l’exemple, si vous compilez à l’aide de `/DTEST=` , une erreur se produit. Ce comportement ressemble à l'utilisation de `#define` avec ou sans valeur.

L’option **/d** ne prend pas en charge les définitions de macros de type fonction. Pour insérer des définitions qui ne peuvent pas être définies sur la ligne de commande, utilisez l’option de compilateur [/fi (nom forcé include file)](fi-name-forced-include-file.md) .

Vous pouvez utiliser **/d** plusieurs fois sur la ligne de commande pour définir des symboles supplémentaires. Si le même symbole est défini plusieurs fois, la dernière définition est utilisée.

Cette commande définit le symbole DEBUG dans TEST.c:

```cmd
CL /DDEBUG TEST.C
```

Cette commande supprime toutes les occurrences du mot clé `__far` dans TEST.c :

```cmd
CL /D __far= TEST.C
```

La variable d’environnement **CL** ne peut pas être définie sur une chaîne qui contient le signe égal. Pour utiliser **/d** avec la variable d’environnement **CL** , vous devez spécifier le signe dièse ( `#` ) à la place du signe égal :

```cmd
SET CL=/DTEST#0
```

Lorsque vous définissez un symbole de prétraitement à l'invite de commandes, tenez compte des règles d'analyse du compilateur et des règles d'analyse du shell. Par exemple, pour définir un symbole de prétraitement de signe de pourcentage ( `%` ) dans votre programme, spécifiez deux caractères de pourcentage ( `%%` ) à l’invite de commandes. Si vous en spécifiez une seule, une erreur d’analyse est émise.

```cmd
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans le volet gauche, sélectionnez **Propriétés de configuration**, **C/C++**, **préprocesseur**.

1. Dans le volet droit, dans la colonne de droite de la propriété **définitions de préprocesseur** , ouvrez le menu déroulant et choisissez **modifier**.

1. Dans la boîte de dialogue **définitions de préprocesseur** , ajoutez (une par ligne), modifiez ou supprimez une ou plusieurs définitions. Choisissez **OK** pour enregistrer vos modifications.

   Vous n’avez pas besoin d’inclure le préfixe d’option « /D » dans les définitions que vous spécifiez ici. Dans la page de propriétés, les définitions sont séparées par des points-virgules ( `;` ).

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Exemple

```cpp
// cpp_D_compiler_option.cpp
// compile with: cl /EHsc /DTEST cpp_D_compiler_option.cpp
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

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)\
[/FI (nom du fichier include imposé)](fi-name-forced-include-file.md)\
[/U,/u (annuler la définition des symboles)](u-u-undefine-symbols.md)\
[#undef, directive (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)\
[#define, directive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
