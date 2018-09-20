---
title: Windows Sockets, Classes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.net
dev_langs:
- C++
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 893fa525b04376cde0e96f280c95e6bfd1243946
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439976"
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

