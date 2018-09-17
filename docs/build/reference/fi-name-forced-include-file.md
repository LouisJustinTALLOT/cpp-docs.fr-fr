---
title: -FI (nom du fichier Include) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCNMakeTool.ForcedIncludes
- VC.Project.VCCLCompilerTool.ForcedIncludeFiles
- VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles
- /fi
dev_langs:
- C++
helpviewer_keywords:
- FI compiler option [C++]
- -FI compiler option [C++]
- /FI compiler option [C++]
- preprocess header file compiler option [C++]
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa06eaf8f16a80b849ce911468fc0001366b9e29
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725463"
---
# <a name="fi-name-forced-include-file"></a>/FI (Nom du fichier Include imposé)

Indique au préprocesseur de traiter le fichier d’en-tête spécifié.

## <a name="syntax"></a>Syntaxe

```
/FI[ ]pathname
```

## <a name="remarks"></a>Notes

Cette option a le même effet que si vous définissiez le fichier avec des guillemets doubles dans une `#include` directive sur la première ligne de chaque fichier source spécifié sur la ligne de commande dans la variable d’environnement CL, ou dans un fichier de commandes. Si vous utilisez plusieurs **/FI** options, les fichiers sont incluses dans l’ordre, ils sont traités par CL.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **avancé** page de propriétés.

1. Modifier le **Force inclut** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.

## <a name="see-also"></a>Voir aussi

[Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)