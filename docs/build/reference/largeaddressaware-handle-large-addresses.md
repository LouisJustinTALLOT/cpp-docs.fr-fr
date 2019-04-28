---
title: /LARGEADDRESSAWARE (Gérer les longues adresses)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
ms.openlocfilehash: 81a560ebf083e2f93d9bb514fc401186291d7f41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269548"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (Gérer les longues adresses)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>Notes

L’option /LARGEADDRESSAWARE indique à l’éditeur de liens que l’application peut gérer des adresses supérieures à 2 gigaoctets. Dans les compilateurs 64 bits, cette option est activée par défaut. Dans les compilateurs 32 bits, / LARGEADDRESSAWARE : no est activée si /LARGEADDRESSAWARE n’est pas spécifiée autrement sur la ligne de l’éditeur de liens.

Si une application a été liée avec cette option, DUMPBIN [/HEADERS](headers.md) affiche des informations à cet effet.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **système** page de propriétés.

1. Modifier le **activer les longues adresses** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
