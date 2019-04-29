---
title: /showIncludes (Liste des fichiers Include)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
ms.openlocfilehash: d454054c132976a899fcc4a56a63be427e79beec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318158"
---
# <a name="showincludes-list-include-files"></a>/showIncludes (Liste des fichiers Include)

Indique au compilateur de générer une liste des fichiers include. Imbriquées incluent les fichiers sont également affichés (les fichiers qui sont inclus dans les fichiers que vous incluez).

## <a name="syntax"></a>Syntaxe

```
/showIncludes
```

## <a name="remarks"></a>Notes

Lorsqu’un fichier include est rencontré pendant la compilation, un message est sortie, par exemple :

```
Note: including file: d:\MyDir\include\stdio.h
```

Imbriquées incluent les fichiers sont indiqués par une mise en retrait, un espace pour chaque niveau d’imbrication, par exemple :

```
Note: including file: d:\temp\1.h
Note: including file:  d:\temp\2.h
```

Dans ce cas, `2.h` a été inclus à partir de `1.h`, par conséquent, la mise en retrait.

Le **/showIncludes** option émet à `stderr`, et non `stdout`.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **avancé** page de propriétés.

1. Modifier le **affichage des fichiers** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
