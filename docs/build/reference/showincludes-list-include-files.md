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
ms.openlocfilehash: 7be3d93f91133ad1a29e6b4d6d2c50157a3376b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523043"
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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **avancé** page de propriétés.

1. Modifier le **affichage des fichiers** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)