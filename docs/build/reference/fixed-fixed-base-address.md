---
description: En savoir plus sur:/FIXED (adresse de base fixe)
title: /FIXED (Adresse de base fixe)
ms.date: 11/04/2016
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
ms.openlocfilehash: 08b781b7fbeaf43d6c7e0e82da7bf8319cf77953
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192055"
---
# <a name="fixed-fixed-base-address"></a>/FIXED (Adresse de base fixe)

```
/FIXED[:NO]
```

## <a name="remarks"></a>Notes

Indique au système d’exploitation de charger le programme uniquement à son adresse de base préférée. Si l'adresse de base préférée est introuvable, le système d'exploitation ne charge pas le fichier. Pour plus d’informations, consultez l’article [/BASE (Adresse de base)](base-base-address.md).

/FIXED : NO est le paramètre par défaut pour une DLL et/FIXED est le paramètre par défaut pour tout autre type de projet.

Lorsque /FIXED est spécifié, LINK ne génère pas de section de réadressage dans le programme. Au moment de l’exécution, si le système d’exploitation ne parvient pas à charger le programme à l’adresse spécifiée, il émet un message d’erreur et ne charge pas le programme.

Spécifiez/FIXED : NO pour générer une section de réadressage dans le programme.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l' **éditeur de liens** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Tapez le nom et le paramètre de l’option dans la zone **options supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
