---
title: Windows Sockets, classes (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 18537c0de09185c8cd219e3d17ef8bb297e1d711
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433603"
---
# <a name="windows-sockets-classes"></a>Windows Sockets, classes (C++)

Windows Sockets fournissent un moyen indépendant du protocole de réseau pour la communication entre deux ordinateurs. Ces sockets peuvent être synchrones (votre programme attend jusqu'à ce que la communication s’effectue) ou asynchrone (votre programme poursuit pendant la communication est en cours d’exécution).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Encapsule l’API de Sockets Windows dans un wrapper mince.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Niveau d’abstraction plus élevé est dérivée de `CAsyncSocket`. Il fonctionne de manière synchrone.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Fournit un `CFile` interface à un Socket Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

