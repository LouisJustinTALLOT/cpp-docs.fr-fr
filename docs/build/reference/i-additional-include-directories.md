---
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
ms.openlocfilehash: b922a4472246bb13bfed4022f2f85061c5d1217b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563863"
---
# <a name="i-additional-include-directories"></a>/I (Autres répertoires Include)

Ajoute un répertoire à la liste des répertoires de recherche des fichiers include.

## <a name="syntax"></a>Syntaxe

```
/I[ ]directory
```

## <a name="arguments"></a>Arguments

*Répertoire*<br/>
Le répertoire à ajouter à la liste des répertoires de recherche des fichiers include.

## <a name="remarks"></a>Notes

Pour ajouter plusieurs répertoires, utilisez cette option plusieurs fois. Répertoires sont recherchés uniquement jusqu'à ce que le fichier include spécifié est trouvé.

Vous pouvez utiliser cette option avec l’ignorer Standard chemins d’accès Include ([/X (ignorer Standard chemins d’accès Include)](../../build/reference/x-ignore-standard-include-paths.md)) option.

Le compilateur recherche les répertoires dans l’ordre suivant :

1. Répertoires contenant le fichier source.

1. Répertoires spécifiés avec le **/I** option, dans l’ordre où CL les trouve.

1. Répertoires spécifiés dans le **INCLUDE** variable d’environnement.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **général** page de propriétés.

1. Modifier le **autres répertoires Include** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.

## <a name="example"></a>Exemple

La commande suivante recherche les fichiers include demandés par MAIN.c dans l’ordre suivant : premier dans le répertoire contenant MAIN.c, puis le répertoire \INCLUDE, puis, dans le répertoire \MY\INCLUDE et enfin, dans les répertoires affectés à l’INCLUDE variable d’environnement.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)