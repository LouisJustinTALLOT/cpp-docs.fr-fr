---
title: Nettoyage des Documents et vues | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dfe54c13db6f44bc70289380ae5f50d99c3722b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341324"
---
# <a name="cleaning-up-documents-and-views"></a>Nettoyage des documents et vues
Lors de la fermeture d’un document, le framework appelle d’abord son [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) fonction membre. Si vous avez alloué de la mémoire dans le segment de mémoire au cours de l’utilisation du document, `DeleteContents` est le meilleur endroit pour la libérer.  
  
> [!NOTE]
>  Vous ne devez pas libérer les données de document dans le destructeur du document. Dans le cas d’une application SDI, l’objet de document peut être réutilisé.  
  
 Vous pouvez remplacer le destructeur d’une vue pour libérer toute mémoire allouée dans le tas.  
  
## <a name="see-also"></a>Voir aussi  
 [Initialisation et nettoyage des documents et vues](../mfc/initializing-and-cleaning-up-documents-and-views.md)

