---
title: /X (Ignorer les chemins d'accès Include standard)
ms.date: 07/18/2019
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 16f903b98d69472fe1a33b084fe6393ecf9ec001
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341041"
---
# <a name="x-ignore-standard-include-paths"></a>/X (Ignorer les chemins d'accès Include standard)

Empêche le compilateur de rechercher des fichiers include dans les répertoires spécifiés dans les variables d’environnement PATH et INCLUDe.

## <a name="syntax"></a>Syntaxe

```
/X
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser cette option avec l’option [/i (autres répertoires Include)](i-additional-include-directories.md) ( **/i**`directory`).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur  la page de propriétés du préprocesseur.

1. Modifiez la propriété **ignorer le chemin d’accès Include standard** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Exemple

Dans la commande suivante, `/X` indique au compilateur d’ignorer les emplacements spécifiés par les variables d’environnement PATH et `/I` include, et spécifie le répertoire dans lequel rechercher les fichiers include:

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
