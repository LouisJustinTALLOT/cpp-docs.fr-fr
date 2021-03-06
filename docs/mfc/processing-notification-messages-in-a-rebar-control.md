---
description: 'En savoir plus sur : traitement des messages de notification dans un contrôle rebar'
title: Traitement des messages de notification dans un contrôle rebar
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 6255f10068072f75f556cf1c8576008ab821ed27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154836"
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
[Contrôles](controls-mfc.md)
