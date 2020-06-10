---
title: Gestion de la notification TTN_NEEDTEXT pour les info-bulles
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: 75850dbf92587cf654d4f7a39ea54af1fd9dd5bd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620080"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>Gestion de la notification TTN_NEEDTEXT pour les info-bulles

Dans le cadre de [l’activation des info-bulles](enabling-tool-tips.md), vous gérez le message **TTN_NEEDTEXT** en ajoutant l’entrée suivante à la table des messages de votre fenêtre propriétaire :

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
Fonction membre à appeler lorsque du texte est nécessaire pour ce bouton.

Notez que l’ID d’une info-bulle est toujours 0.

Déclarez votre fonction de gestionnaire dans la définition de classe comme suit :

[!code-cpp[NVC_MFCControlLadenDialog#53](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

où les paramètres en italique sont :

*id*<br/>
Identificateur du contrôle qui a envoyé la notification. Non utilisé. L’ID de contrôle provient de la structure **NMHDR** .

*pNMHDR*<br/>
Pointeur vers la structure [NMTTDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow) . Cette structure est également traitée plus en détail dans [la structure ToolTipText](tooltiptext-structure.md).

*pResult*<br/>
Pointeur désignant le code de résultat que vous pouvez définir avant de retourner. Les gestionnaires de **TTN_NEEDTEXT** peuvent ignorer le paramètre *pResult* .

Voici un exemple de gestionnaire de notification de vue de formulaire :

[!code-cpp[NVC_MFCControlLadenDialog#54](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

Appel `EnableToolTips` (ce fragment extrait de `OnInitDialog` ) :

[!code-cpp[NVC_MFCControlLadenDialog#55](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Info-bulles dans les fenêtres non dérivées de CFrameWnd](tool-tips-in-windows-not-derived-from-cframewnd.md)
