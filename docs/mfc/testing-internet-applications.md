---
title: Test des applications Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
ms.openlocfilehash: 934d336f8c7544bafa412a7b52404a657e8dc9ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439362"
---
# <a name="testing-internet-applications"></a>Test des applications Internet

Il existe des défis uniques de tests sur Internet, en particulier pour les applications qui s’exécutent sur un serveur Web. Le test initial sera probablement effectué à l’aide d’un client d’utilisateur unique qui se connecte à un serveur de test. Cela sera utile pour déboguer votre code.

Vous souhaitez également tester dans les conditions réelles : avec plusieurs clients connectés via des connexions haut débit, ainsi que des lignes de série de faible vitesse, y compris les connexions de modem. Il peut être difficile de simuler des conditions réelles, mais il vaut sans aucun doute les dépenses heure concevoir des scénarios possibles et les exécuter. Si possible, vous devez également utiliser des outils pour la capacité de faire et le test de contrainte. Certaines classes de bogues, tels que les bogues de temporisation, sont difficiles à trouver et à reproduire.

Un des défis de la programmation Internet est sa visibilité. Nombre d’accès à votre site peuvent ralentir votre serveur. Vous voulez que votre serveur pour une dégradation normale. Vous souhaitez empêcher tout code qui peut être à l’ordinateur d’un utilisateur si votre application échoue (par exemple, une altération des données lors de l’écriture dans le Registre ou lors de l’écriture des cookies sur le client).

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)

