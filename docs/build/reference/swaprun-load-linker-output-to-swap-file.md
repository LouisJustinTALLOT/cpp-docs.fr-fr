---
title: -SWAPRUN (charger la sortie de l’éditeur de liens pour le fichier d’échange) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
dev_langs:
- C++
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1867eb55f9ebcaba2d29f7b9b4b2f44a68164390
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717494"
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN (Charger la sortie de l'Éditeur de liens dans le fichier d'échange)

```
/SWAPRUN:{NET|CD}
```

## <a name="remarks"></a>Notes

Cette option indique le système d’exploitation pour la première copie de l’éditeur de liens de sortie dans un fichier d’échange et puis exécuter l’image à partir de là. Il s’agit d’une fonctionnalité de Windows NT 4.0 (et versions ultérieure).

Si NET est spécifié, le système d’exploitation sera tout d’abord copier l’image binaire du réseau dans un fichier d’échange et chargez-le à partir de là. Cette option est utile pour exécuter des applications sur le réseau. Lorsque le CD est spécifié, le système d’exploitation copie l’image sur un disque amovible dans un fichier de page et puis de son chargement.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **système** page de propriétés.

1. Modifier l’une des propriétés suivantes :

   - **Exécuter l’échange à partir du CD**

   - **Exécuter l’échange à partir du réseau**

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)