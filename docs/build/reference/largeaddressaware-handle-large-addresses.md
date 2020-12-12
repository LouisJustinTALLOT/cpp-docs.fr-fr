---
description: En savoir plus sur:/LARGEADDRESSAWARE (gérer les adresses volumineuses)
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
ms.openlocfilehash: 72b2ba20b2ea2b91ecd234497c433bcdd9e9ee42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199569"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (Gérer les longues adresses)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>Notes

L’option/LARGEADDRESSAWARE indique à l’éditeur de liens que l’application peut gérer des adresses supérieures à 2 gigaoctets. Dans les compilateurs 64 bits, cette option est activée par défaut. Dans les compilateurs 32 bits,/LARGEADDRESSAWARE : NO est activé si/LARGEADDRESSAWARE n’est pas spécifié sur la ligne de l’éditeur de liens.

Si une application a été liée avec/LARGEADDRESSAWARE, DUMPBIN [/headers](headers.md) affiche des informations à cet effet.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **système** .

1. Modifiez la propriété **activer les adresses volumineuses** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
