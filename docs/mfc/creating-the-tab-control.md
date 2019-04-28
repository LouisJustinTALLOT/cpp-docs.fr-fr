---
title: Création du contrôle Tab
ms.date: 11/04/2016
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
ms.openlocfilehash: 4627009e2e07d1c5692d83d8d6262a9fcd37977e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241960"
---
# <a name="creating-the-tab-control"></a>Création du contrôle Tab

Comment le contrôle d’onglet est créé dépend de si vous l’utilisation du contrôle dans une boîte de dialogue ou créée dans un autre type de fenêtre.

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Utilisation de CTabCtrl directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue, ajoutez un contrôle onglet pour votre ressource de modèle de boîte de dialogue. Spécifier son ID de contrôle.

1. Utilisez le [Assistant Ajout de Variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CTabCtrl](../mfc/reference/ctabctrl-class.md) avec la propriété du contrôle. Vous pouvez utiliser ce membre pour appeler `CTabCtrl` fonctions membres.

1. Mapper des fonctions de gestionnaire dans la classe de boîte de dialogue pour les messages de notification de contrôle tab que vous devez gérer. Pour plus d’informations, consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).

1. Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez les styles pour le `CTabCtrl`.

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>Utilisation de CTabCtrl dans un autre type de fenêtre

1. Définissez le contrôle dans la classe de vue ou de la fenêtre.

1. Le contrôle de l’appel [créer](../mfc/reference/ctabctrl-class.md#create) fonction membre, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement en même temps que la fenêtre parente [OnCreate](../mfc/reference/cwnd-class.md#oncreate) fonction de gestionnaire (si vous êtes sous-classe le contrôle). Définir les styles pour le contrôle.

Après le `CTabCtrl` objet a été créé, vous pouvez définir ou effacer ce qui suit les styles étendus :

- **TCS_EX_FLATSEPARATORS** le contrôle d’onglet dessine des séparateurs entre les éléments d’onglet. Style étendu uniquement affecte l’onglet des contrôles qui ont le **TCS_BUTTONS** et **TCS_FLATBUTTONS** styles. Par défaut, création d’un contrôle onglet avec le **TCS_FLATBUTTONS** style définit ce style étendu.

- **TCS_EX_REGISTERDROP** génère le contrôle onglet **TCN_GETOBJECT** lorsqu’un objet est glissé par-dessus les onglets dans le contrôle de l’objet des messages de notification pour demander une cible de dépôt.

    > [!NOTE]
    >  Pour recevoir le **TCN_GETOBJECT** notification, vous devez initialiser les bibliothèques OLE avec un appel à [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

Ces styles peuvent être récupérées et définis, une fois que le contrôle a été créé, via des appels à la [fonctions membres GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle) et [SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle) fonctions membres.

Par exemple, définissez la **TCS_EX_FLATSEPARATORS** style avec les lignes de code suivantes :

[!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]

Effacer la **TCS_EX_FLATSEPARATORS** appliquer un style à partir d’un `CTabCtrl` objet avec les lignes de code suivantes :

[!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]

Cela supprimera les séparateurs qui apparaissent entre les boutons de votre `CTabCtrl` objet.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
