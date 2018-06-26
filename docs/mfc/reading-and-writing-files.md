---
title: Lors de la lecture et écriture de fichiers | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e30ee5b326833b45365c422238ecfcd4f82c556d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930909"
---
# <a name="reading-and-writing-files"></a>Lecture et écriture de fichiers
Si vous avez utilisé les fonctions de gestion de fichiers de bibliothèque Runtime C, MFC, la lecture et l’écriture des opérations apparaîtra familier. Cet article décrit directement lire et écrire directement à un `CFile` objet. Vous pouvez également en mémoire tampon d’e/s de fichier avec le [CArchive](../mfc/reference/carchive-class.md) classe.  
  
#### <a name="to-read-from-and-write-to-the-file"></a>Pour lire et écrire dans le fichier  
  
1.  Utilisez le `Read` et `Write` des fonctions membres pour lire et écrire des données dans le fichier.  
  
     - ou -  
  
2.  Le `Seek` fonction membre est également disponible pour atteindre un certain décalage dans le fichier.  
  
 `Read` prend un pointeur vers une mémoire tampon et le nombre d’octets à lire et retourne le nombre réel d’octets qui ont été lus. Si le nombre d’octets requis ne parvient pas, car fin de fichier (EOF) est atteint, le nombre réel d’octets lus est retourné. Si une erreur de lecture se produit, une exception est levée. `Write` est semblable à `Read`, mais le nombre d’octets écrits n’est pas retourné. Si une erreur d’écriture se produit, y compris n’écrit ne pas tous les octets spécifiés, une exception est levée. Si vous avez valide `CFile` de l’objet, vous pouvez lire ou écrire comme indiqué dans l’exemple suivant :  
  
 [!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]  
  
> [!NOTE]
>  Vous devez normalement effectuer les opérations d’entrée/sortie dans un **essayez**/**catch** bloc gestion des exceptions. Pour plus d’informations, consultez [la gestion des exceptions (MFC)](../mfc/exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers](../mfc/files-in-mfc.md)

