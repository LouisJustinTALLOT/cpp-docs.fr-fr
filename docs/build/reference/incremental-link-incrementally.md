---
title: -INCREMENTAL (lier par incrément) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
dev_langs:
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02ba96a810703f653b101839d4c9b965da735588
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725047"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (Lier par incrément)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>Notes

Contrôle la façon dont l'éditeur gère l'édition des liens incrémentielle.

Par défaut, l'éditeur de liens s'exécute en mode incrémentiel. Pour substituer un lien incrémentiel par défaut, spécifiez /INCREMENTAL:NO.

Un programme lié de façon incrémentielle est fonctionnellement équivalent à un programme lié de façon non incrémentielle. Toutefois, comme il est préparé pour les liens incrémentiels à venir, lié de façon incrémentielle bibliothèque statique, exécutable ou fichier de bibliothèque de liens dynamiques :

- Est supérieur à un programme lié de façon non incrémentielle fait du remplissage du code et les données. Le remplissage permet à l’éditeur de liens augmenter la taille des fonctions et des données sans avoir à recréer le fichier.

- Il peut contenir des conversions de code de renvoi pour gérer le réadressage des fonctions vers de nouvelles adresses.

   > [!NOTE]
   > Pour vous assurer que votre version release finale ne contient pas de marge intérieure, ou thunks, liez votre programme de façon non incrémentielle.

Pour lier de façon incrémentielle, indépendamment de la valeur par défaut, spécifiez /INCREMENTAL. Lorsque cette option est sélectionnée, l’éditeur de liens émet un avertissement s’il ne peut pas lier par incrément et lie le programme de façon non incrémentielle. Certaines options et situations substituent l'option /INCREMENTAL.

La plupart des programmes peuvent être liés de façon incrémentielle. Toutefois, certaines modifications sont trop importantes et certaines options sont incompatibles avec l'édition des liens incrémentielle. LINK effectue un lien complet si l'une des options suivantes est spécifiée :

- L'édition des liens incrémentielle n'est pas sélectionnée (/INCREMENTAL:NO)

- /OPT:REF est sélectionné

- /OPT:ICF est sélectionné

- /OPT:LBR est sélectionné

- /ORDER est sélectionné

/INCREMENTAL est implicite lorsque [/DEBUG](../../build/reference/debug-generate-debug-info.md) est spécifié.

De plus, LINK effectue un lien complet si l'une des situations suivantes se produit :

- Le fichier d'état incrémentiel (.ilk) est manquant. (LINK crée un fichier .ilk en prévision de l'édition des liens incrémentielle à venir).

- Le fichier .ilk ne possède pas d'autorisation d'accès en écriture. (LINK ignore le fichier .ilk et des liens non incrémentielle.)

- Le fichier de sortie .exe ou .dll est manquant.

- L'horodatage du fichier .ilk, .exe ou .dll est modifié.

- Une option LINK est modifiée. La plupart des options LINK, lorsqu'elles sont modifiées entre les builds, provoquent un lien complet.

- Un fichier objet (.obj) est ajouté ou omis.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez la page de propriétés **Général** .

1. Modifier le **activation des liens incrémentiels** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)