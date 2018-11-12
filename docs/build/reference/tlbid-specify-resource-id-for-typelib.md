---
title: /TLBID (Spécifier l'ID de ressource de TypeLib)
ms.date: 11/04/2016
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
ms.openlocfilehash: 1a86c753aa94302e7f4d26c53fee2f63175d33c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519286"
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID (Spécifier l'ID de ressource de TypeLib)

```
/TLBID:id
```

## <a name="arguments"></a>Arguments

*ID*<br/>
Une valeur spécifiée par l’utilisateur pour une bibliothèque de type créés par l’éditeur de liens. Ce paramètre remplace l’ID de ressource par défaut de 1.

## <a name="remarks"></a>Notes

Quand vous compilez un programme qui utilise des attributs, l’éditeur de liens crée une bibliothèque de types. L’éditeur de liens affecte un ID de ressource de 1 à la bibliothèque de types.

Si cet ID de ressource est en conflit avec l’un de vos ressources existantes, vous pouvez spécifier un autre ID avec /TLBID. La plage de valeurs que vous pouvez transmettre à `id` est comprise entre 1 et 65535.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **IDL incorporé** page de propriétés.

1. Modifier le **ID de ressource de TypeLib** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)