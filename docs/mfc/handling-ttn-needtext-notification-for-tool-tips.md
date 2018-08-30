---
title: Gestion de la Notification TTN_NEEDTEXT pour les info-bulles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TTN_NEEDTEXT
dev_langs:
- C++
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65278571fabf24011960ad577461347f1dfebf73
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200516"
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>Gestion de la notification TTN_NEEDTEXT pour les info-bulles
Dans le cadre de [l’activation des info-bulles](../mfc/enabling-tool-tips.md), vous gérez le **TTN_NEEDTEXT** message en ajoutant l’entrée suivante à la table des messages de votre fenêtre propriétaire :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
 `memberFxn`  
 La fonction membre à appeler lorsque le texte est nécessaire pour ce bouton.  
  
 Notez que l’ID d’une info-bulle est toujours 0.  
  
 Déclarez votre fonction de gestionnaire dans la définition de classe comme suit :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 où les paramètres en italique sont :  
  
 `id`  
 Identificateur du contrôle qui a envoyé la notification. Non utilisé. L’id de contrôle provient de la **NMHDR** structure.  
  
 `pNMHDR`  
 Un pointeur vers le [structure NMTTDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagnmttdispinfoa) structure. Cette structure est également abordée plus en détail dans [ToolTipText, Structure](../mfc/tooltiptext-structure.md).  
  
 `pResult`  
 Un pointeur vers le code de résultat, vous pouvez définir avant de retourner. **TTN_NEEDTEXT** gestionnaires peuvent ignorer le *pResult* paramètre.  
  
 Voici un exemple d’un gestionnaire de notification en mode formulaire :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 Appelez `EnableToolTips` (ce fragment proviennent `OnInitDialog`) :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Info-bulles dans les fenêtres non dérivées de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

