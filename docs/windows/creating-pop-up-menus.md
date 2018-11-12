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
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
ms.openlocfilehash: 243a2489918f74243ce3b2268ec44c4fe4c1b566
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506780"
---
# <a name="creating-pop-up-menus-c"></a>Création de Menus contextuels (C++)

Les[menus contextuels](../mfc/menus-mfc.md) affichent les commandes fréquemment utilisées. Ils dépendent du contexte selon l'emplacement du pointeur. L'utilisation de menus contextuels dans votre application nécessite la création du menu en question, puis sa connexion au code de l'application.

Une fois que vous avez créé la ressource de menu, votre code d’application doit charger cette ressource et utiliser [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) pour faire apparaître le menu. Une fois que l'utilisateur a fermé le menu contextuel en cliquant hors de ce dernier, ou qu'il a cliqué sur une commande, cette fonction est retournée. Si l'utilisateur choisit une commande, ce message de commande est envoyé à la fenêtre dont le handle a été passé.

### <a name="to-create-a-pop-up-menu"></a>Pour créer un menu contextuel

1. [Créez un menu](../windows/creating-a-menu.md) avec un titre vide (ne fournissez pas de **légende**).

2. [Ajoutez une commande de menu au nouveau menu](../windows/adding-commands-to-a-menu.md). Déplacer vers la première commande de menu sous le titre de menu vide (la légende temporaire indique `Type Here`). Tapez une **légende** et les autres informations appropriées.

   Répétez ce processus pour les autres commandes de menu du menu contextuel.

3. Enregistrez la ressource de menu.

   > [!TIP]
   > Pour plus d'informations sur l'affichage du menu contextuel, voir [Affichage d'un menu sous la forme d'un menu contextuel](../windows/viewing-a-menu-as-a-pop-up-menu.md).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Connexion d’un menu contextuel à votre application](../windows/connecting-a-pop-up-menu-to-your-application.md)<br/>
[Éditeur de menus](../windows/menu-editor.md)