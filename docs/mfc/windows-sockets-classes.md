---
description: En savoir plus sur les classes Windows Sockets
title: Windows Sockets, classes (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 03d8ddae0bb511e52b0ea7ed2b3754184ed6ebc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118639"
---
# <a name="windows-sockets-classes"></a>Windows Sockets, classes (C++)

Les sockets Windows offrent une méthode indépendante du protocole réseau pour la communication entre deux ordinateurs. Ces Sockets peuvent être synchrones (votre programme attend jusqu’à ce que la communication soit effectuée) ou asynchrone (votre programme continue de s’exécuter pendant que la communication est en cours).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Encapsule l’API Windows Sockets dans un wrapper léger.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Abstraction de niveau supérieur dérivée de `CAsyncSocket` . Elle fonctionne de façon synchrone.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Fournit une `CFile` interface à un socket Windows.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../mfc/class-library-overview.md)
