---
title: /MACHINE (Spécifier la plate-forme cible)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
ms.openlocfilehash: 872370269e9ab8acaaa8cafe7fb47b1121bcbb97
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546433"
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