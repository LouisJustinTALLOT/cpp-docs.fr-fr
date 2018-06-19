---
title: Création du contrôle Tab | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
dev_langs:
- C++
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3945d441130d723bbda3d137f2adae637d56c2b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344089"
---
# <a name="creating-the-tab-control"></a>Création du contrôle Tab
Comment le contrôle d’onglet est créé dépend de l’utilisation du contrôle dans une boîte de dialogue ou de la créer dans un autre type de fenêtre.  
  
### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Utilisation de CTabCtrl directement dans une boîte de dialogue  
  
1.  Dans l’éditeur de boîte de dialogue, ajoutez un contrôle Tab à votre ressource de modèle de boîte de dialogue. Spécifier son ID de contrôle.  
  
2.  Utilisez le [Assistant Ajout de Variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CTabCtrl](../mfc/reference/ctabctrl-class.md) avec la propriété du contrôle. Vous pouvez utiliser ce membre pour appeler `CTabCtrl` fonctions membres.  
  
3.  Mapper des fonctions de gestionnaire de la classe de boîte de dialogue pour les messages de notification de contrôle tab que vous devez gérer. Pour plus d’informations, consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).  
  
4.  Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez les styles pour le `CTabCtrl`.  
  
### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>Pour utiliser CTabCtrl dans un autre type de fenêtre  
  
1.  Définissez le contrôle dans la classe d’affichage ou de la fenêtre.  
  
2.  Appel du contrôle [créer](../mfc/reference/ctabctrl-class.md#create) fonction membre, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement en même temps que la fenêtre parente [OnCreate](../mfc/reference/cwnd-class.md#oncreate) fonction de gestionnaire (si vous êtes le sous-classement du contrôle). Définissez les styles pour le contrôle.  
  
 Après le `CTabCtrl` objet a été créé, vous pouvez définir ou désactivez les éléments suivants styles étendus :  
  
-   **TCS_EX_FLATSEPARATORS** le contrôle d’onglet dessine des séparateurs entre les éléments d’onglet. Style étendu uniquement affecte onglet contrôles ayant le **TCS_BUTTONS** et **TCS_FLATBUTTONS** styles. Par défaut, créez le contrôle onglet avec le **TCS_FLATBUTTONS** style définit ce style étendu.  
  
-   **TCS_EX_REGISTERDROP** le contrôle onglet génère **TCN_GETOBJECT** lorsqu’un objet est déplacé sur les éléments d’onglet dans le contrôle de l’objet des messages de notification pour demander une cible de dépôt.  
  
    > [!NOTE]
    >  Pour recevoir le **TCN_GETOBJECT** notification, vous devez initialiser les bibliothèques OLE avec un appel à [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).  
  
 Ces styles peuvent être récupérées et définies, une fois que le contrôle a été créé, via des appels à la [fonctions membres GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle) et [SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle) fonctions membres.  
  
 Par exemple, définissez la **TCS_EX_FLATSEPARATORS** style avec les lignes de code suivantes :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]  
  
 Désactivez le **TCS_EX_FLATSEPARATORS** style à partir d’un `CTabCtrl` objet avec les lignes de code suivantes :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]  
  
 Cela supprimera les séparateurs qui s’affichent entre les boutons de votre `CTabCtrl` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

