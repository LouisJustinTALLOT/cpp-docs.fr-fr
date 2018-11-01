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
ms.openlocfilehash: 9f1098e305606df9463e308466b7864b019d5a00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459278"
---
# <a name="overridable-cwinapp-member-functions"></a>Fonctions membres CWinApp remplaçables

[CWinApp](../mfc/reference/cwinapp-class.md) fournit plusieurs fonctions membres clés substituables (`CWinApp` substitue ces membres à partir de la classe [CWinThread](../mfc/reference/cwinthread-class.md), à partir de laquelle `CWinApp` dérive) :

- [InitInstance](../mfc/initinstance-member-function.md)

- [Exécuter](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

La seule `CWinApp` que vous devez substituer la fonction membre est `InitInstance`.

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)
