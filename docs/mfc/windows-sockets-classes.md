---
title: Windows Sockets, classes (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 4abdd8f8fbfc115b5014ffd0b3a37df357852b16
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303818"
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
