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
ms.openlocfilehash: 6d5aa6873966ecb4c845f1c503b24c07b6c0c7a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619608"
---
# <a name="creating-the-tab-control"></a>Création du contrôle Tab

La façon dont le contrôle onglet est créé varie selon que vous utilisez le contrôle dans une boîte de dialogue ou que vous le créez dans une fenêtre qui n’est pas une boîte de dialogue.

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Pour utiliser CTabCtrl directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue, ajoutez un contrôle onglet à votre ressource de modèle de boîte de dialogue. Spécifiez son ID de contrôle.

1. Utilisez l' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CTabCtrl](reference/ctabctrl-class.md) avec la propriété Control. Vous pouvez utiliser ce membre pour appeler des `CTabCtrl` fonctions membres.

1. Mappez les fonctions de gestionnaire dans la classe de boîte de dialogue pour tous les messages de notification de contrôle d’onglet que vous devez gérer. Pour plus d’informations, consultez [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md).

1. Dans [OnInitDialog](reference/cdialog-class.md#oninitdialog), définissez les styles pour le `CTabCtrl` .

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>Pour utiliser CTabCtrl dans une fenêtre qui n’est pas une boîte de dialogue

1. Définissez le contrôle dans la vue ou la classe de fenêtre.

1. Appelez la fonction membre [Create](reference/ctabctrl-class.md#create) du contrôle, éventuellement dans [OnInitialUpdate](reference/cview-class.md#oninitialupdate), éventuellement aussi tôt que la fonction gestionnaire [OnCreate](reference/cwnd-class.md#oncreate) de la fenêtre parente (si vous sous-classez le contrôle). Définissez les styles pour le contrôle.

Une fois l' `CTabCtrl` objet créé, vous pouvez définir ou désactiver les styles étendus suivants :

- **TCS_EX_FLATSEPARATORS** Le contrôle onglet dessine des séparateurs entre les éléments d’onglet. Ce style étendu affecte uniquement les contrôles d’onglet qui ont les styles **TCS_BUTTONS** et **TCS_FLATBUTTONS** . Par défaut, la création du contrôle onglet avec le style **TCS_FLATBUTTONS** définit ce style étendu.

- **TCS_EX_REGISTERDROP** Le contrôle onglet génère des messages de notification **TCN_GETOBJECT** pour demander un objet cible de déplacement lorsqu’un objet est glissé sur les éléments d’onglet dans le contrôle.

    > [!NOTE]
    >  Pour recevoir la notification **TCN_GETOBJECT** , vous devez initialiser les bibliothèques OLE avec un appel à [AfxOLEInit](reference/ole-initialization.md#afxoleinit).

Ces styles peuvent être récupérés et définis, une fois le contrôle créé, avec les appels respectifs aux fonctions membres [GetExtendedStyle](reference/ctabctrl-class.md#getextendedstyle) et [SetExtendedStyle](reference/ctabctrl-class.md#setextendedstyle) .

Par exemple, définissez le style de **TCS_EX_FLATSEPARATORS** avec les lignes de code suivantes :

[!code-cpp[NVC_MFCControlLadenDialog#33](codesnippet/cpp/creating-the-tab-control_1.cpp)]

Effacez le style de **TCS_EX_FLATSEPARATORS** d’un `CTabCtrl` objet à l’aide des lignes de code suivantes :

[!code-cpp[NVC_MFCControlLadenDialog#34](codesnippet/cpp/creating-the-tab-control_2.cpp)]

Cela supprimera les séparateurs qui apparaissent entre les boutons de votre `CTabCtrl` objet.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](using-ctabctrl.md)<br/>
[Commandes](controls-mfc.md)
