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
ms.openlocfilehash: c52bfb9e4b6d0e94cecb77c766ac9e82b52f1e66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317794"
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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **IDL incorporé** page de propriétés.

1. Modifier le **ID de ressource de TypeLib** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
