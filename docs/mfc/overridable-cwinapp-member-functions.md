---
title: Fonctions membres CWinApp remplaçables
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 28ba243bd755e25db5f2cb03d08013f082fbc918
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447268"
---
# <a name="overridable-cwinapp-member-functions"></a>Fonctions membres CWinApp remplaçables

[CWinApp](../mfc/reference/cwinapp-class.md) fournit plusieurs fonctions membres substituables clés (`CWinApp` Substitue ces membres de la classe [CWinThread](../mfc/reference/cwinthread-class.md), à partir de laquelle `CWinApp` dérive) :

- [InitInstance](../mfc/initinstance-member-function.md)

- [Exécuter](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

La seule fonction membre `CWinApp` que vous devez substituer est `InitInstance`.

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)
