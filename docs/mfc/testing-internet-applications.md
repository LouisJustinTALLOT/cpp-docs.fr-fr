---
title: Test des Applications Internet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61ffc5b11783806555b210b8561cbe6cdd2878ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380067"
---
# <a name="testing-internet-applications"></a>Test des applications Internet
Il existe des défis de tests uniques sur Internet, en particulier pour les applications qui s’exécutent sur un serveur Web. Le test initial est probablement effectué à l’aide d’un client de mono-utilisateur se connectant à un serveur de test. Cela sera utile pour le débogage de votre code.  
  
 Vous devez également tester dans les conditions réelles : avec plusieurs clients connectés via des connexions haut débit, ainsi que des lignes de série de faible débit, y compris les connexions de modem. Il peut être difficile de simuler des conditions réelles, mais il est certainement à temps concevoir des scénarios possibles de dépense et de les exécuter. Si possible, vous devez également utiliser les outils à la capacité d’et le test de stress. Certaines classes de bogues, tels que les bogues de temporisation, sont difficiles à détecter et à reproduire.  
  
 Un des défis de la programmation Internet est sa visibilité. Nombre d’accès à votre site peuvent ralentir votre serveur. Vous souhaitez que votre serveur dégradation normale. Vous souhaitez éviter tout ce qui peut être dans l’ordinateur d’un utilisateur si votre application échoue (par exemple, une altération des données lors de l’écriture dans le Registre ou lors de l’écriture des cookies sur le client).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)

