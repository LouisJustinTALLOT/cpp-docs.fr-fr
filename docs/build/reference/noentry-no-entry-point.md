---
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
ms.openlocfilehash: c750fd94e21eec39a25acf216a452faaa277bf7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320407"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (Aucun point d'entrée)

```
/NOENTRY
```

## <a name="remarks"></a>Notes

L'option /NOENTRY est nécessaire pour créer une DLL de ressources uniquement ne contenant aucun code exécutable. Pour plus d’informations, consultez [création d’une DLL Resource-Only](../creating-a-resource-only-dll.md).

Utilisez cette option pour empêcher LINK de lier une référence à `_main` dans la DLL.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **avancé** page de propriétés.

1. Modifier le **aucun Point d’entrée** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>.

## <a name="see-also"></a>Voir aussi

[Création d’une DLL de ressource uniquement](../creating-a-resource-only-dll.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
