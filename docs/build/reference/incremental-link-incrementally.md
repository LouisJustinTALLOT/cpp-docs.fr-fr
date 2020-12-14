---
description: En savoir plus sur:/INCREMENTAL (lier par incrément)
title: /INCREMENTAL (Lier par incrément)
ms.date: 11/04/2016
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
ms.openlocfilehash: 4b115bd88bed5b012c29c3d0e61d471aa869b78a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191288"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (Lier par incrément)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>Notes

Contrôle la façon dont l'éditeur gère l'édition des liens incrémentielle.

Par défaut, l'éditeur de liens s'exécute en mode incrémentiel. Pour substituer un lien incrémentiel par défaut, spécifiez /INCREMENTAL:NO.

Un programme lié de façon incrémentielle est fonctionnellement équivalent à un programme qui n’est pas lié de manière incrémentielle. Toutefois, étant donné qu’il est préparé pour les liens incrémentiels suivants, un exécutable lié de façon incrémentielle, une bibliothèque statique ou un fichier de bibliothèque de liens dynamiques :

- Est supérieur à un programme lié de façon non incrémentielle en raison de la marge intérieure du code et des données. Le remplissage permet à l’éditeur de liens d’augmenter la taille des fonctions et des données sans recréer le fichier.

- Il peut contenir des conversions de code de renvoi pour gérer le réadressage des fonctions vers de nouvelles adresses.

   > [!NOTE]
   > Pour vous assurer que votre version Release finale ne contient pas de remplissage ou de thunks, liez votre programme de façon non incrémentielle.

Pour lier de façon incrémentielle, indépendamment de la valeur par défaut, spécifiez /INCREMENTAL. Quand cette option est sélectionnée, l’éditeur de liens émet un avertissement s’il ne peut pas lier de façon incrémentielle, puis lie le programme de façon non incrémentielle. Certaines options et situations substituent l'option /INCREMENTAL.

La plupart des programmes peuvent être liés de façon incrémentielle. Toutefois, certaines modifications sont trop importantes et certaines options sont incompatibles avec l'édition des liens incrémentielle. LINK effectue un lien complet si l'une des options suivantes est spécifiée :

- L'édition des liens incrémentielle n'est pas sélectionnée (/INCREMENTAL:NO)

- /OPT:REF est sélectionné

- /OPT:ICF est sélectionné

- /OPT:LBR est sélectionné

- /ORDER est sélectionné

/INCREMENTAL est implicite lorsque [/Debug](debug-generate-debug-info.md) est spécifié.

De plus, LINK effectue un lien complet si l'une des situations suivantes se produit :

- Le fichier d'état incrémentiel (.ilk) est manquant. (LINK crée un fichier .ilk en prévision de l'édition des liens incrémentielle à venir).

- Le fichier .ilk ne possède pas d'autorisation d'accès en écriture. (LINK ignore le fichier. ilk et les liens de façon non incrémentielle.)

- Le fichier de sortie .exe ou .dll est manquant.

- L'horodatage du fichier .ilk, .exe ou .dll est modifié.

- Une option LINK est modifiée. La plupart des options LINK, lorsqu'elles sont modifiées entre les builds, provoquent un lien complet.

- Un fichier objet (.obj) est ajouté ou omis.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l' **éditeur de liens** .

1. Sélectionnez la page de propriétés **Général** .

1. Modifiez la propriété **activer les liens incrémentiels** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
