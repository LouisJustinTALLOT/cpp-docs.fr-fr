---
title: Gestion des notifications pour les info-bulles
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 41e3dbfc2269f5fbf3c12dc00c19f8a2253fd16a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626448"
---
# <a name="handling-tool-tip-notifications"></a>Gestion des notifications pour les info-bulles

Lorsque vous spécifiez le style de **TBSTYLE_TOOLTIPS** , la barre d’outils crée et gère un contrôle d’info-bulle. Une info-bulle est une petite fenêtre contextuelle qui contient une ligne de texte décrivant un bouton de barre d’outils. L’info-bulle est masquée, qui s’affiche uniquement lorsque l’utilisateur place le curseur sur un bouton de barre d’outils et le laisse pendant environ une demi-seconde. L’info-bulle s’affiche à côté du curseur.

Avant l’affichage de l’info-bulle, le message de notification **TTN_NEEDTEXT** est envoyé à la fenêtre propriétaire de la barre d’outils pour récupérer le texte descriptif du bouton. Si la fenêtre propriétaire de la barre d’outils est une `CFrameWnd` fenêtre, les info-bulles s’affichent sans aucun effort supplémentaire, car `CFrameWnd` dispose d’un gestionnaire par défaut pour la notification de **TTN_NEEDTEXT** . Si la fenêtre propriétaire de la barre d’outils n’est pas dérivée de `CFrameWnd` , telle qu’une boîte de dialogue ou un mode formulaire, vous devez ajouter une entrée à la table des messages de votre fenêtre propriétaire et fournir un gestionnaire de notifications dans la table des messages. L’entrée de la table des messages de votre fenêtre propriétaire est la suivante :

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>Notes

*memberFxn*<br/>
Fonction membre à appeler lorsque du texte est nécessaire pour ce bouton.

Notez que l’ID d’une info-bulle est toujours 0.

En plus de la notification de **TTN_NEEDTEXT** , un contrôle d’info-bulle peut envoyer les notifications suivantes à un contrôle de barre d’outils :

|Notification|Signification|
|------------------|-------------|
|**TTN_NEEDTEXTA**|Le contrôle d’info-bulle requiert du texte ASCII (Windows 95 uniquement)|
|**TTN_NEEDTEXTW**|Le contrôle d’info-bulle requiert du texte UNICODE (Windows NT uniquement)|
|**TBN_HOTITEMCHANGE**|Indique que l’élément réactif (en surbrillance) a changé.|
|**NM_RCLICK**|Indique que l’utilisateur a cliqué avec le bouton droit sur un bouton.|
|**TBN_DRAGOUT**|Indique que l’utilisateur a cliqué sur le bouton et a fait glisser le pointeur hors du bouton. Elle permet à une application d’implémenter le glisser-déplacer à partir d’un bouton de barre d’outils. Lors de la réception de cette notification, l’application commence l’opération de glisser-déplacer.|
|**TBN_DROPDOWN**|Indique que l’utilisateur a cliqué sur un bouton qui utilise le style **TBSTYLE_DROPDOWN** .|
|**TBN_GETOBJECT**|Indique que l’utilisateur a déplacé le pointeur sur un bouton qui utilise le style **TBSTYLE_DROPPABLE** .|

Pour obtenir un exemple de fonction de gestionnaire et des informations supplémentaires sur l’activation des info-bulles, consultez [info-bulles](tool-tips-in-windows-not-derived-from-cframewnd.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Commandes](controls-mfc.md)
