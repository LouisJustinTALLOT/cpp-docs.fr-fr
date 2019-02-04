---
title: Création de Menus contextuels (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
ms.openlocfilehash: cf2e3578f49cb6b4af8797052273211f699a6b4f
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702828"
---
# <a name="creating-pop-up-menus-c"></a>Création de Menus contextuels (C++)

Les[menus contextuels](../mfc/menus-mfc.md) affichent les commandes fréquemment utilisées. Ils dépendent du contexte selon l'emplacement du pointeur. L'utilisation de menus contextuels dans votre application nécessite la création du menu en question, puis sa connexion au code de l'application.

Une fois que vous avez créé la ressource de menu, votre code d’application doit charger cette ressource et utiliser [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) pour faire apparaître le menu. Une fois que l’utilisateur a fermé le menu contextuel en sélectionnant à l’extérieur ou qu’il a sélectionné une commande, cette fonction est retournée. Si l'utilisateur choisit une commande, ce message de commande est envoyé à la fenêtre dont le handle a été passé.

## <a name="to-create-a-pop-up-menu"></a>Pour créer un menu contextuel

1. [Créez un menu](../windows/creating-a-menu.md) avec un titre vide (ne fournissez pas de **légende**).

1. [Ajoutez une commande de menu au nouveau menu](../windows/adding-commands-to-a-menu.md). Déplacer vers la première commande de menu sous le titre de menu vide (la légende temporaire indique `Type Here`). Tapez une **légende** et les autres informations appropriées.

   Répétez ce processus pour les autres commandes de menu du menu contextuel.

1. Enregistrez la ressource de menu.

## <a name="to-connect-a-pop-up-menu-to-your-application"></a>Pour connecter un menu contextuel à votre application

1. Ajoutez un gestionnaire de messages pour WM_CONTEXTMENU (par exemple). Pour plus d’informations, consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).

1. Ajoutez le code suivant au gestionnaire de messages :

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > Le [CPoint](../atl-mfc-shared/reference/cpoint-class.md) passé par le message gestionnaire est en coordonnées d’écran.

   > [!NOTE]
   > Connexion d’un menu contextuel à votre application nécessite des MFC.

## <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>Pour afficher une ressource de menu sous forme de menu contextuel

Normalement, lorsque vous travaillez dans le **Menu** éditeur, une ressource de menu s’affiche comme une barre de menus. Toutefois, il est possible que des ressources de menu soient ajoutées à la barre de menus de l'application pendant l'exécution du programme.

Le menu contextuel et choisissez **afficher comme Popup** dans le menu contextuel.

   Cette option est uniquement une préférence d’affichage et ne peut pas modifier votre menu.

   > [!NOTE]
   > Pour revenir à la vue de la barre de menus, cliquez sur **afficher comme Popup** à nouveau (ce qui supprime la coche et retourne l’affichage de la barre de menus).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)
