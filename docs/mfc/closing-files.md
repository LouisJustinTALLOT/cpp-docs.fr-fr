---
title: Fermeture de fichiers | Documents Microsoft
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
ms.openlocfilehash: 97bd910ae4cb514cda07dd319f37a05a32712909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341024"
---
# <a name="closing-files"></a>Fermeture des fichiers
Comme d’habitude dans les opérations d’e/s, une fois que vous avez terminé avec un fichier, vous devez le fermer.  
  
#### <a name="to-close-a-file"></a>Pour fermer un fichier  
  
1.  Utilisez le **fermer** fonction membre. Cette fonction ferme le fichier de système de fichiers et vide les mémoires tampons si nécessaire.  
  
 Si vous avez alloué la [CFile](../mfc/reference/cfile-class.md) objet sur le frame (comme dans l’exemple illustré [ouverture de fichiers](../mfc/opening-files.md)), l’objet sera automatiquement être fermé et puis détruits lorsqu’il devient hors de portée. Notez que la suppression du `CFile` objet ne supprime pas le fichier physique du système de fichiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers](../mfc/files-in-mfc.md)

