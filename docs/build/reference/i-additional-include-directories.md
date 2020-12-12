---
description: En savoir plus sur:/I (autres répertoires Include)
title: /I (Autres répertoires Include)
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
ms.openlocfilehash: ad44abec28bbb87f91f449765a9ea2f30f2bffa8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191340"
---
# <a name="i-additional-include-directories"></a>/I (Autres répertoires Include)

Ajoute un répertoire à la liste des répertoires dans lesquels sont recherchés les fichiers include.

## <a name="syntax"></a>Syntaxe

> **/I**[]*répertoire*

### <a name="arguments"></a>Arguments

*Directory*<br/>
Répertoire à ajouter à la liste des répertoires dans lesquels sont recherchés les fichiers include.

## <a name="remarks"></a>Notes

Pour ajouter plusieurs répertoires, utilisez cette option plusieurs fois. Les répertoires sont recherchés uniquement jusqu’à ce que le fichier include spécifié soit trouvé.

Vous pouvez utiliser cette option avec l’option ([/x (ignorer les chemins d’accès Include standard)](x-ignore-standard-include-paths.md)).

Le compilateur recherche des répertoires dans l’ordre suivant :

1. S’il est spécifié à l’aide d’une [directive #include](../../preprocessor/hash-include-directive-c-cpp.md) sous forme de guillemet double, il recherche d’abord dans les répertoires locaux. La recherche commence dans le même répertoire que le fichier qui contient l’instruction **#include** . Si le fichier n’est pas trouvé, il effectue une recherche dans les répertoires des fichiers include actuellement ouverts, dans l’ordre inverse dans lequel ils ont été ouverts. La recherche commence dans le répertoire du fichier Include parent et continue vers le haut, dans les répertoires de tous les fichiers Include grands-parents.

1. Si elle est spécifiée à l’aide d’une **#include** directive dans le cadre d’un chevron, ou si la recherche de répertoire locale a échoué, elle recherche des répertoires spécifiés à l’aide de l’option **/i** , dans l’ordre dans lequel CL les rencontre sur la ligne de commande.

1. Répertoires spécifiés dans la variable d’environnement **include** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés général des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **autres répertoires Include** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.

## <a name="example"></a>Exemple

La commande suivante recherche les fichiers include demandés par MAIN. c dans l’ordre suivant : tout d’abord, s’il est spécifié à l’aide de guillemets doubles, la recherche s’effectue dans les fichiers locaux. Ensuite, la recherche se poursuit dans le répertoire \INCLUDE, puis dans le répertoire \MY\INCLUDE et enfin dans les répertoires affectés à la variable d’environnement INCLUDe.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
