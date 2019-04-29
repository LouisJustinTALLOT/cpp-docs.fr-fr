---
title: Fonctions membres CWinApp remplaçables
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 35db009f86a0cb984f70a349a3ecdd93bfefb0f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297078"
---
# <a name="overridable-cwinapp-member-functions"></a>Fonctions membres CWinApp remplaçables

[CWinApp](../mfc/reference/cwinapp-class.md) fournit plusieurs fonctions membres clés substituables (`CWinApp` substitue ces membres à partir de la classe [CWinThread](../mfc/reference/cwinthread-class.md), à partir de laquelle `CWinApp` dérive) :

- [InitInstance](../mfc/initinstance-member-function.md)

- [Exécuter](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

La seule `CWinApp` que vous devez substituer la fonction membre est `InitInstance`.

## <a name="see-also"></a>Voir aussi

[CWinApp : Classe d’application](../mfc/cwinapp-the-application-class.md)
