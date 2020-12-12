---
description: 'En savoir plus sur : fermeture des fichiers'
title: Fermeture des fichiers
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: e8d2f0792aeb889c40cb516af259fc2a40890a1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338386"
---
# <a name="closing-files"></a>Fermeture des fichiers

Comme d’habitude dans les opérations d’e/s, une fois que vous avez terminé avec un fichier, vous devez le fermer.

#### <a name="to-close-a-file"></a>Pour fermer un fichier

1. Utilisez la fonction membre **Close** . Cette fonction ferme le fichier du système de fichiers et vide les mémoires tampons, si nécessaire.

Si vous avez alloué l’objet [CFile](reference/cfile-class.md) sur le frame (comme dans l’exemple indiqué dans [ouverture de fichiers](opening-files.md)), l’objet est automatiquement fermé puis détruit lorsqu’il est hors de portée. Notez que la suppression de l' `CFile` objet ne supprime pas le fichier physique dans le système de fichiers.

## <a name="see-also"></a>Voir aussi

[Fichiers](files-in-mfc.md)
