---
title: Windows Sockets, classes (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 3f1b7b2b6674b4a5f8c8f7bff6c5fa239715f459
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445981"
---
# <a name="windows-sockets-classes"></a>Windows Sockets, classes (C++)

Les sockets Windows offrent une méthode indépendante du protocole réseau pour la communication entre deux ordinateurs. Ces Sockets peuvent être synchrones (votre programme attend jusqu’à ce que la communication soit effectuée) ou asynchrone (votre programme continue de s’exécuter pendant que la communication est en cours).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Encapsule l’API Windows Sockets dans un wrapper léger.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Abstraction de niveau supérieur dérivée de `CAsyncSocket`. Elle fonctionne de façon synchrone.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Fournit une interface de `CFile` à un socket Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
