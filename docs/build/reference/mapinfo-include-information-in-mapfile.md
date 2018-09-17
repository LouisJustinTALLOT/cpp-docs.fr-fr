---
title: -MAPINFO (inclure des informations dans le fichier de mappage) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.MapLines
- VC.Project.VCLinkerTool.MapInfoFixups
- VC.Project.VCLinkerTool.MapExports
- /mapinfo
dev_langs:
- C++
helpviewer_keywords:
- /MAPINFO linker option
- MAPINFO linker option
- -MAPINFO linker option
ms.assetid: 533d2bce-f9b7-4fea-ae1c-0b4864c9d10b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f52e044962007c4a820bf234d45b5cb9ffd584f6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723084"
---
# <a name="mapinfo-include-information-in-mapfile"></a>/MAPINFO (Inclure des informations dans le fichier de mappage)

```
/MAPINFO:EXPORTS
```

## <a name="remarks"></a>Notes

L’option /MAPINFO indique à l’éditeur de liens à inclure les informations spécifiées dans un fichier de mappage, qui est créé si vous spécifiez le [/mapper](../../build/reference/map-generate-mapfile.md) option.  EXPORTS indique à l’éditeur de liens d’inclure des fonctions exportées.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **déboguer** page de propriétés.

1. Modification de la **mappage des exportations** propriétés :

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapExports%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)