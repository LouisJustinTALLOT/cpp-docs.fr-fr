---
title: -MACHINE (spécifier la plateforme cible) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e159fe15b0aed441b1a96047a3ffb035077d6266
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708615"
---
# <a name="machine-specify-target-platform"></a>/MACHINE (Spécifier la plate-forme cible)

```
/MACHINE:{ARM|EBC|X64|X86}
```

## <a name="remarks"></a>Notes

L’option /MACHINE spécifie la plateforme cible pour le programme.

En règle générale, vous n’êtes pas obligé de spécifier l’option /MACHINE. LIEN déduit le type d’ordinateur à partir des fichiers .obj. Toutefois, dans certaines circonstances, la liaison ne peut pas déterminer le type d’ordinateur et les problèmes un [LNK1113 d’erreur des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-error-lnk1113.md). Si une telle erreur se produit, spécifiez/machine.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **avancé** page de propriétés.

1. Modifier le **Machine cible** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)