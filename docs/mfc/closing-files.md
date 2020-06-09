---
title: Fermeture des fichiers
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 51e51c88260a51ec44f11ecb5c2a88e645194f4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617233"
---
# <a name="closing-files"></a>Fermeture des fichiers

Comme d’habitude dans les opérations d’e/s, une fois que vous avez terminé avec un fichier, vous devez le fermer.

#### <a name="to-close-a-file"></a>Pour fermer un fichier

1. Utilisez la fonction membre **Close** . Cette fonction ferme le fichier du système de fichiers et vide les mémoires tampons, si nécessaire.

Si vous avez alloué l’objet [CFile](reference/cfile-class.md) sur le frame (comme dans l’exemple indiqué dans [ouverture de fichiers](opening-files.md)), l’objet est automatiquement fermé puis détruit lorsqu’il est hors de portée. Notez que la suppression de l' `CFile` objet ne supprime pas le fichier physique dans le système de fichiers.

## <a name="see-also"></a>Voir aussi

[Fichiers](files-in-mfc.md)
