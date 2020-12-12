---
description: En savoir plus sur les éléments suivants:/MACHINE (spécifier la plateforme cible)
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
ms.openlocfilehash: a1bf87142fb99577672391356a43a2771ea0b09f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190807"
---
# <a name="machine-specify-target-platform"></a>/MACHINE (Spécifier la plate-forme cible)

```
/MACHINE:{ARM|EBC|X64|X86}
```

## <a name="remarks"></a>Notes

L’option/MACHINE spécifie la plateforme cible pour le programme.

En règle générale, vous n’avez pas besoin de spécifier l’option/MACHINE. Le lien déduit le type d’ordinateur à partir des fichiers. obj. Toutefois, dans certains cas, LINK ne peut pas déterminer le type d’ordinateur et émet une [erreur des outils Éditeur de liens LNK1113](../../error-messages/tool-errors/linker-tools-error-lnk1113.md). Si une telle erreur se produit, spécifiez/MACHINE.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **avancé** .

1. Modifiez la propriété **ordinateur cible** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
