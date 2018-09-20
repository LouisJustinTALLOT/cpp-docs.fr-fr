---
title: Fermeture des fichiers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c392ef728e1d796a02cfa32edc2c3e8c74d083b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426235"
---
# <a name="closing-files"></a>Fermeture des fichiers

Comme d’habitude dans les opérations d’e/s, une fois que vous avez terminé avec un fichier, vous devez le fermer.

#### <a name="to-close-a-file"></a>Pour fermer un fichier

1. Utilisez le **fermer** fonction membre. Cette fonction ferme le fichier de système de fichiers et vide les mémoires tampons si nécessaire.

Si vous avez alloué le [CFile](../mfc/reference/cfile-class.md) objet sur le frame (comme dans l’exemple présenté dans [ouverture de fichiers](../mfc/opening-files.md)), l’objet sera automatiquement être fermé et puis détruits lorsqu’il devient hors de portée. Notez que cette opération le `CFile` objet ne supprime pas le fichier physique dans le système de fichiers.

## <a name="see-also"></a>Voir aussi

[Fichiers](../mfc/files-in-mfc.md)

