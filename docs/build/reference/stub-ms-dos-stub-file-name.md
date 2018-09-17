---
title: -STUB (nom du fichier Stub MS-DOS) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c279d6f33befb4c308afe0c92b7dcca3d45ba66
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707718"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (Nom du fichier stub MS-DOS)

```
/STUB:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Une application MS-DOS.

## <a name="remarks"></a>Notes

L’option /STUB attache un programme stub MS-DOS à un programme de Win32.

Un programme stub est appelé si le fichier est exécuté dans MS-DOS. Il affiche généralement un message approprié ; Toutefois, n’importe quelle application MS-DOS valide peut être un programme stub.

Spécifiez un *filename* pour le programme stub après le signe deux-points ( :)) sur la ligne de commande. Les vérifications de l’éditeur de liens *filename* et émet un message d’erreur si le fichier n’est pas un fichier exécutable. Le programme doit être un fichier .exe ; un fichier .com n’est pas valide pour un programme stub.

Si cette option n’est pas utilisée, l’éditeur de liens attache un programme stub par défaut qui émet le message suivant :

```
This program cannot be run in MS-DOS mode.
```

Lors de la création d’un pilote de périphérique virtuel, *filename* permet à l’utilisateur de spécifier un nom de fichier qui contient une structure IMAGE_DOS_HEADER (définie dans WINNT. (H) à utiliser dans le VXD, plutôt que dans l’en-tête par défaut.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)