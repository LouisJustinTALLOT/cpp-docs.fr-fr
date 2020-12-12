---
description: En savoir plus sur:/NATVIS (Ajouter Natvis à PDB)
title: /NATVIS (Ajouter Natvis à PDB)
ms.date: 08/10/2017
f1_keywords:
- /natvis
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: 7703915591a59a558c8580dd64b9be22d281d784
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190521"
---
# <a name="natvis-add-natvis-to-pdb"></a>/NATVIS (Ajouter Natvis à PDB)

> /NATVIS :*nom de fichier*

## <a name="parameters"></a>Paramètres

*filename*<br/>
Fichier Natvis à ajouter au fichier PDB. Elle incorpore les visualisations du débogueur dans le fichier Natvis dans le fichier PDB.

## <a name="remarks"></a>Notes

L’option/NATVIS incorpore les visualisations du débogueur définies dans le *nom* de fichier de NATVIS dans le fichier PDB généré par Link. Cela permet au débogueur d’afficher les visualisations indépendamment du fichier. natvis. Vous pouvez utiliser plusieurs options/NATVIS pour incorporer plusieurs fichiers Natvis dans le fichier PDB généré.

LINK ignore/NATVIS lorsqu’un fichier PDB n’est pas créé à l’aide d’une option [/Debug](debug-generate-debug-info.md) . Pour plus d’informations sur la création et l’utilisation des fichiers. natvis, consultez [créer des vues personnalisées d’objets natifs dans le débogueur Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **ligne de commande** dans le dossier **éditeur de liens** .

1. Ajoutez l’option/NATVIS à la zone de texte **options supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Cette option n’a pas d’équivalent programmatique.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
