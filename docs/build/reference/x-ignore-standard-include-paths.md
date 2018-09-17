---
title: X-(ignorer Standard chemins d’accès Include) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
dev_langs:
- C++
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 994568d74c63e612b55d1101ce957e646c555e4a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707432"
---
# <a name="x-ignore-standard-include-paths"></a>/X (Ignorer les chemins d’accès Include standard)

Empêche le compilateur de rechercher des fichiers include dans les répertoires spécifiés dans les variables d’environnement PATH et INCLUDE.

## <a name="syntax"></a>Syntaxe

```
/X
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser cette option avec la [/I (autres répertoires Include)](../../build/reference/i-additional-include-directories.md) (**/I**`directory`) option.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **préprocesseur** page de propriétés.

1. Modifier le **chemin d’accès Include Standard ignorer** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Exemple

Dans la commande suivante, `/X` indique au compilateur d’ignorer les emplacements spécifiés par les variables d’environnement PATH et INCLUDE, et `/I` Spécifie le répertoire dans lesquels rechercher des fichiers include :

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)