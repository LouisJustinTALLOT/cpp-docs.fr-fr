---
description: En savoir plus sur:/NOENTRY (aucun point d’entrée)
title: /NOENTRY (Aucun point d'entrée)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
ms.openlocfilehash: c3d1f725a4e185a052d443010894ff2dc2261675
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196683"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (Aucun point d'entrée)

```
/NOENTRY
```

## <a name="remarks"></a>Notes

L'option /NOENTRY est nécessaire pour créer une DLL de ressources uniquement ne contenant aucun code exécutable. Pour plus d’informations, consultez [création d’un Resource-Only dll](../creating-a-resource-only-dll.md).

Utilisez cette option pour empêcher LINK de lier une référence à `_main` dans la DLL.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l' **éditeur de liens** .

1. Sélectionnez la page de propriétés **Avancé**.

1. Modifiez la propriété **aucun point d’entrée** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>.

## <a name="see-also"></a>Voir aussi

[Création d’une DLL Resource-Only](../creating-a-resource-only-dll.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
