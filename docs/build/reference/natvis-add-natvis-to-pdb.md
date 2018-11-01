---
title: / NATVIS (ajouter Natvis à PDB)
ms.date: 08/10/2017
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: 475eb377fd55d6118c109f4e03ea1cf624a563f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446018"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (ajouter Natvis à PDB)

> / NATVIS :*nom de fichier*

## <a name="parameters"></a>Paramètres

*filename*<br/>
Un fichier Natvis à ajouter au fichier PDB. Il incorpore les visualisations du débogueur dans le fichier .natvis dans le fichier PDB.

## <a name="remarks"></a>Notes

L’option /NATVIS incorpore les visualisations du débogueur définies dans le fichier Natvis *nom de fichier* dans le fichier PDB généré par LINK. Cela permet au débogueur afficher les visualisations indépendamment le fichier .natvis. Vous pouvez utiliser plusieurs options /NATVIS à incorporer plusieurs fichiers Natvis dans le fichier PDB généré.

LIEN ignore /NATVIS quand un fichier PDB n’est pas créé à l’aide un [/DEBUG](../../build/reference/debug-generate-debug-info.md) option. Pour plus d’informations sur la création et l’utilisation de fichiers .natvis, consultez [créer des vues personnalisées d’objets natifs dans le débogueur Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Sélectionnez le **ligne de commande** page de propriétés dans le **l’éditeur de liens** dossier.

1. Ajoutez l’option /NATVIS à la **des Options supplémentaires** zone de texte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Cette option n’a pas un équivalent de programmation.

## <a name="see-also"></a>Voir aussi

[Créer des vues personnalisées d’objets natifs dans le débogueur Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects)<br/>
[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)