---
title: Associer des commandes de Menu avec le texte de barre d’état dans les Applications MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars [C++], associating menu items
- menus [C++], status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 16de276478485cb52b11b3f1bbb869c5b75d05a4
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316755"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Association de commandes de menu au texte de la barre d'état dans des applications MFC

Votre application MFC peut afficher un texte descriptif pour chacune des commandes de menu, qu'un utilisateur peut sélectionner. Pour cela, affectez une chaîne de texte à chaque commande de menu à l’aide de la **invite** propriété dans le **propriétés** fenêtre. Si vous avez une chaîne dans la [table de chaînes](../windows/string-editor.md) dont l'ID est identique à la commande, une application MFC affiche automatiquement cette ressource de chaîne dans la barre d'état de l'application en cours d'exécution quand un utilisateur pointe sur un élément de menu.

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Pour associer une commande de menu à une chaîne de texte de barre d'état

1. Dans l' **éditeur de menus** , sélectionnez la commande de menu.

2. Dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez le texte de barre d'état associé dans la zone **Invite** .

## <a name="requirements"></a>Configuration requise

MFC

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Ajout de commandes à un menu](../windows/adding-commands-to-a-menu.md)  
[Éditeur de menus](../windows/menu-editor.md)