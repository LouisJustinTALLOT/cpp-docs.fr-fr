---
description: 'En savoir plus sur : test d’applications Internet'
title: Test des applications Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
ms.openlocfilehash: ed3dd9819524e156af47da4070c517e3761380ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216260"
---
# <a name="testing-internet-applications"></a>Test des applications Internet

Il existe des défis de test uniques sur Internet, en particulier pour les applications qui s’exécutent sur un serveur Web. Vos tests initiaux seront probablement effectués à l’aide d’un client mono-utilisateur qui se connecte à un serveur de test. Cela sera utile pour déboguer votre code.

Vous devez également effectuer un test dans des conditions réelles : avec plusieurs clients connectés via des connexions haut débit et des lignes série à faible vitesse, y compris des connexions par modem. Il peut être difficile de simuler des conditions réelles, mais il est sans doute utile de consacrer du temps à concevoir des scénarios possibles et à les exécuter. Si possible, vous pouvez également utiliser des outils pour effectuer des tests de capacité et de stress. Certaines classes de bogues, telles que les bogues de minutage, sont difficiles à trouver et à reproduire.

L’un des défis de la programmation Internet est sa visibilité. De nombreux accès à votre site peuvent ralentir votre serveur. Vous souhaitez que votre serveur se dégrade normalement. Vous souhaitez empêcher tout ce qui peut être destructif sur l’ordinateur d’un utilisateur en cas d’échec de votre application (par exemple, l’altération des données lors de l’écriture dans le registre ou lors de l’écriture de cookies sur le client).

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Concepts de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)
