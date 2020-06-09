---
title: Fonctions membres CWinApp remplaçables
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 7ae72a52c37582f8398ebc03f404ff105fe14650
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624013"
---
# <a name="overridable-cwinapp-member-functions"></a>Fonctions membres CWinApp remplaçables

[CWinApp](reference/cwinapp-class.md) fournit plusieurs fonctions membres substituables clés ( `CWinApp` substitue ces membres de la classe [CWinThread](reference/cwinthread-class.md), à partir duquel `CWinApp` dérive) :

- [InitInstance](initinstance-member-function.md)

- [Exécuter](run-member-function.md)

- [ExitInstance](exitinstance-member-function.md)

- [OnIdle](onidle-member-function.md)

La seule `CWinApp` fonction membre que vous devez substituer est `InitInstance` .

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](cwinapp-the-application-class.md)
