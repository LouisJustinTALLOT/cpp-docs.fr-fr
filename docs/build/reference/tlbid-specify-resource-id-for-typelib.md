---
description: En savoir plus sur:/TLBID (spécifier l’ID de ressource pour TypeLib)
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
ms.openlocfilehash: 4958229cbebe988867c5419d7953b6ffd968e45f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230014"
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID (Spécifier l'ID de ressource de TypeLib)

```
/TLBID:id
```

## <a name="arguments"></a>Arguments

*id*<br/>
Valeur spécifiée par l’utilisateur pour une bibliothèque de types créée par l’éditeur de liens. Il remplace l’ID de ressource par défaut 1.

## <a name="remarks"></a>Notes

Lors de la compilation d’un programme qui utilise des attributs, l’éditeur de liens crée une bibliothèque de types. L’éditeur de liens assignera un ID de ressource de 1 à la bibliothèque de types.

Si cet ID de ressource est en conflit avec l’une de vos ressources existantes, vous pouvez spécifier un autre ID avec/TLBID. La plage de valeurs que vous pouvez passer à est comprise entre `id` 1 et 65535.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **IDL incorporé** .

1. Modifiez la propriété de l' **ID de ressource TypeLib** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
