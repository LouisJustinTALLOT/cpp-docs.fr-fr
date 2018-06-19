---
title: ExitInstance, fonction membre | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords: []
dev_langs:
- C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 954d2248061ec571d9d2ba8804c1f7c97275cbfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343497"
---
# <a name="exitinstance-member-function"></a>ExitInstance, fonction membre
Le [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) fonction membre de classe [CWinApp](../mfc/reference/cwinapp-class.md) est appelée chaque fois qu’une copie de votre application se termine, généralement suite à l’utilisateur de quitter l’application.  
  
 Substituer `ExitInstance` si vous devez le traitement de nettoyage spécial, comme la libération des ressources de graphics device interface GDI (interface) ou de désallocation de mémoire utilisée pendant l’exécution du programme. Nettoyage des éléments standards tels que des documents et des vues, toutefois, est fourni par le framework, avec les autres fonctions substituables effectuant un nettoyage spécial spécifique à ces objets.  
  
## <a name="see-also"></a>Voir aussi  
 [CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)
