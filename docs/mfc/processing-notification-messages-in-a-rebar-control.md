---
title: Traitement des messages de notification dans un contrôle rebar
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: e1e1aaa5056b43f0dd23976fead94bc800163613
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625189"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Traitement des messages de notification dans un contrôle rebar

Dans la classe parente du contrôle rebar, créez une `OnChildNotify` fonction de gestionnaire avec une instruction switch pour tous les messages de notification de contrôle rebar ( `CReBarCtrl` ) que vous souhaitez gérer. Les notifications sont envoyées à la fenêtre parente lorsque l’utilisateur fait glisser des objets sur le contrôle rebar, modifie la disposition des bandes rebar, supprime les bandes du contrôle rebar, et ainsi de suite.

Les messages de notification suivants peuvent être envoyés par l’objet de contrôle rebar :

- RBN_AUTOSIZE envoyé par un contrôle rebar (créé avec le style RBS_AUTOSIZE) quand le rebar se redimensionne automatiquement.

- RBN_BEGINDRAG Envoyé par un contrôle rebar lorsque l’utilisateur commence à faire glisser une bande.

- RBN_CHILDSIZE envoyé par un contrôle rebar lorsque la fenêtre enfant d’une bande est redimensionnée.

- RBN_DELETEDBAND envoyé par un contrôle rebar après la suppression d’une bande.

- RBN_DELETINGBAND Envoyé par un contrôle rebar quand une bande va être supprimée.

- RBN_ENDDRAG envoyé par un contrôle rebar lorsque l’utilisateur arrête de faire glisser une bande.

- RBN_GETOBJECT envoyé par un contrôle rebar (créé avec le style RBS_REGISTERDROP) quand un objet est glissé sur une bande dans le contrôle.

- RBN_HEIGHTCHANGE envoyé par un contrôle rebar lorsque sa hauteur a changé.

- RBN_LAYOUTCHANGED envoyé par un contrôle rebar lorsque l’utilisateur modifie la disposition des bandes du contrôle.

Pour plus d’informations sur ces notifications, consultez [Rebar Control Reference](/windows/win32/controls/rebar-control-reference) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](using-crebarctrl.md)<br/>
[Commandes](controls-mfc.md)
