---
description: 'En savoir plus sur : fonctions membres CWinApp Overridable'
title: Fonctions membres CWinApp remplaçables
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 3958ad0edc1fbdb77e1f6ce3252fd03d7595344a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330099"
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
