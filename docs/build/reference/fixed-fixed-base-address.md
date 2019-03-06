---
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
ms.openlocfilehash: ccb89b7dfed78ddebf73aaf6e2a1a8529b065042
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423038"
---
# <a name="fixed-fixed-base-address"></a>/FIXED (Adresse de base fixe)

```
/FIXED[:NO]
```

## <a name="remarks"></a>Notes

Indique au système d’exploitation pour charger le programme uniquement à son adresse de base préférée. Si l’adresse de base préférée n’est pas disponible, le système d’exploitation ne charge pas le fichier. Pour plus d’informations, consultez l’article [/BASE (Adresse de base)](../../build/reference/base-base-address.md).

/ Fixed : no est le paramètre par défaut pour une DLL et /FIXED est le paramètre par défaut pour n’importe quel autre type de projet.

Lorsque /FIXED est spécifié, LINK ne génère pas d’une section de réadressage dans le programme. Au moment de l’exécution, si le système d’exploitation ne peut pas charger le programme à l’adresse spécifiée, il émet un message d’erreur et ne charge pas le programme.

Spécifiez/FIXED : no pour générer une section de réadressage dans le programme.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Tapez le nom de l’option et en définissant dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
