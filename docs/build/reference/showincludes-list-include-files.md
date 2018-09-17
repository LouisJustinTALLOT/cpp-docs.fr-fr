---
title: -showIncludes (liste les fichiers Include) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
dev_langs:
- C++
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51305212f97482c6963ee2ba0d272c5c4692416e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709385"
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