---
description: En savoir plus sur:/SWAPRUN (charger la sortie de l’éditeur de liens dans le fichier d’échange)
title: /SWAPRUN (Charger la sortie de l'Éditeur de liens dans le fichier d'échange)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
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
ms.openlocfilehash: f62d5e32432a2c738b7782c0fbf0cd4fd76a7f9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230209"
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN (Charger la sortie de l'Éditeur de liens dans le fichier d'échange)

```
/SWAPRUN:{NET|CD}
```

## <a name="remarks"></a>Notes

L’option/SWAPRUN indique au système d’exploitation de copier la sortie de l’éditeur de liens dans un fichier d’échange, puis d’exécuter l’image à partir de là. Il s’agit d’une fonctionnalité de Windows NT 4,0 (et versions ultérieures).

Si NET est spécifié, le système d’exploitation copie tout d’abord l’image binaire du réseau dans un fichier d’échange et la charge à partir de là. Cette option est utile pour exécuter des applications sur le réseau. Si vous spécifiez CD, le système d’exploitation copie l’image sur un disque amovible dans un fichier d’échange, puis la charge.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **système** .

1. Modifiez l’une des propriétés suivantes :

   - **Échange d’exécution à partir du CD**

   - **Échange d’exécution à partir du réseau**

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
