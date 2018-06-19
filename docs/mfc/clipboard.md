---
title: Presse-papiers | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2ad21bcbff31335f6ec79a4527ef7d99e07e547
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341102"
---
# <a name="clipboard"></a>Presse-papiers
Cette famille d’articles explique comment implémenter la prise en charge du Presse-papiers Windows dans les applications MFC. Le Presse-papiers Windows est utilisé de deux manières :  
  
-   Implémentation de commandes du menu Edition standards, telles que couper, copier et coller.  
  
-   Mise en œuvre de données uniforme transférer par glisser-déplacer (OLE).  
  
 Le Presse-papiers est la méthode Windows standard de transfert de données entre une source et une destination. Il peut également être très utile pour les opérations OLE. Avec l’arrivée de OLE, il existe deux mécanismes de Presse-papiers dans Windows. L’API de Presse-papiers standard de Windows est toujours disponible, mais il a été complétée par le mécanisme de transfert de données OLE. Transfert de données uniforme OLE (UDT) prend en charge les opérations couper, copier et coller avec le Presse-papiers et glisser -déplacer.  
  
 Le Presse-papiers est un service système partagé par la session entière de Windows, afin qu’il n’a pas d’un handle ou une classe qui lui sont propres. Vous gérez le Presse-papiers via les fonctions membres de classe [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Quand utiliser chaque mécanisme de Presse-papiers](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)  
  
-   [À l’aide de l’API du Presse-papiers Windows traditionnel](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [À l’aide du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [Copier et coller des données](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Ajout d’autres formats](../mfc/clipboard-adding-other-formats.md)  
  
-   [Le Presse-papiers Windows](https://msdn.microsoft.com/library/ms648709)  
  
-   [Implémentation de glisser -déplacer (OLE)](../mfc/drag-and-drop-ole.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)
