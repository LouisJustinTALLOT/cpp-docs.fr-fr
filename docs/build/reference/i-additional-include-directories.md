---
title: /I (autres répertoires include)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
ms.openlocfilehash: 6ec8b15e77fec5214013c484e617904ed29e8197
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270140"
---
# <a name="i-additional-include-directories"></a>/I (autres répertoires include)

Ajoute un répertoire à la liste des répertoires de recherche des fichiers include.

## <a name="syntax"></a>Syntaxe

> **/I**[ ]*directory*

### <a name="arguments"></a>Arguments

*directory*<br/>
Le répertoire à ajouter à la liste des répertoires de recherche des fichiers include.

## <a name="remarks"></a>Notes

Pour ajouter plusieurs répertoires, utilisez cette option plusieurs fois. Répertoires sont recherchés uniquement jusqu'à ce que le fichier include spécifié est trouvé.

Vous pouvez utiliser cette option avec le ([/X (ignorer Standard chemins d’accès Include)](x-ignore-standard-include-paths.md)) option.

Le compilateur recherche des répertoires dans l’ordre suivant :

1. Si spécifié à l’aide un [#include, directive](../../preprocessor/hash-include-directive-c-cpp.md) sous forme de guillemets doubles, il recherche tout d’abord les répertoires locaux. La recherche commence dans le même répertoire que le fichier qui contient le **#include** instruction. En cas d’échec rechercher le fichier, il recherche dans les répertoires d’actuellement ouverts fichiers incluent, dans l’ordre inverse dans lequel ils ont été ouverts. La recherche commence dans le répertoire du fichier Include parent et continue vers le haut, dans les répertoires de tous les fichiers Include grands-parents.

1. Si spécifié à l’aide un **#include** directive dans l’angle mettre entre parenthèses le formulaire, ou si la recherche dans l’annuaire local a échoué, il recherche des répertoires spécifiés à l’aide de la **/I** option, dans l’ordre où CL les trouve sur la ligne de commande.

1. Répertoires spécifiés dans le **INCLUDE** variable d’environnement.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **général** page de propriétés.

1. Modifier le **autres répertoires Include** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.

## <a name="example"></a>Exemple

La commande suivante recherche les fichiers include demandés par MAIN.c dans l’ordre suivant : Tout d’abord, s’il est spécifié à l’aide de guillemets doubles, les fichiers locaux sont recherchés. Ensuite, recherche continue dans le répertoire \INCLUDE, puis, dans le répertoire \MY\INCLUDE et enfin, dans les répertoires affecté à la variable d’environnement INCLUDE.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
