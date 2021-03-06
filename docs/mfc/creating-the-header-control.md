---
description: 'En savoir plus sur : création du contrôle header'
title: Création du contrôle Header
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: b75a21a0d855e557bf02a9144fc3712b5bb2ee35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309691"
---
# <a name="creating-the-header-control"></a>Création du contrôle Header

Le contrôle header n’est pas directement disponible dans l’éditeur de boîtes de dialogue (même si vous pouvez ajouter un contrôle List, qui comprend un contrôle header).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>Pour placer un contrôle header dans une boîte de dialogue

1. Incorporez manuellement une variable membre de type [CHeaderCtrl](reference/cheaderctrl-class.md) dans votre classe de boîte de dialogue.

1. Dans [OnInitDialog](reference/cdialog-class.md#oninitdialog), créez et définissez les styles pour le `CHeaderCtrl` , positionnez-le et affichez-le.

1. Ajoutez des éléments au contrôle header.

1. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour mapper les fonctions de gestionnaire de la classe de boîte de dialogue pour tous les messages de notification de contrôle d’en-tête que vous devez gérer (consultez [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Pour placer un contrôle header dans une vue (pas un CListView)

1. Incorporez un objet [CHeaderCtrl](reference/cheaderctrl-class.md) dans votre classe d’affichage.

1. Style, position et affiche la fenêtre de contrôle d’en-tête dans la fonction membre [OnInitialUpdate](reference/cview-class.md#oninitialupdate) de la vue.

1. Ajoutez des éléments au contrôle header.

1. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour mapper des fonctions de gestionnaire dans la classe d’affichage pour tous les messages de notification de contrôle d’en-tête que vous devez gérer (consultez [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md)).

Dans les deux cas, l’objet de contrôle incorporé est créé lors de la création de l’objet de vue ou de boîte de dialogue. Vous devez ensuite appeler [CHeaderCtrl :: Create](reference/cheaderctrl-class.md#create) pour créer la fenêtre de contrôle. Pour positionner le contrôle, appelez [CHeaderCtrl :: Layout](reference/cheaderctrl-class.md#layout) pour déterminer la taille et la position initiales du contrôle et [SetWindowPos](reference/cwnd-class.md#setwindowpos) pour définir la position de votre choix. Ajoutez ensuite des éléments comme décrit dans [Ajout d’éléments au contrôle header](adding-items-to-the-header-control.md).

Pour plus d’informations, consultez [création d’un contrôle header](/windows/win32/Controls/header-controls) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](using-cheaderctrl.md)<br/>
[Contrôles](controls-mfc.md)
