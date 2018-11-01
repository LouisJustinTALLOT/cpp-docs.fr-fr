---
title: ON_UPDATE_COMMAND_UI, macro
ms.date: 11/04/2016
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: d0487f6a69d144e46adab496f3fd21696b5b434b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594103"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI, macro

Utilisez le **propriétés** fenêtre pour connecter un objet d’interface utilisateur à un gestionnaire de mise à jour de la commande dans un objet cible de commande. Il sera automatiquement connect-ID de l’objet d’interface utilisateur dans la macro ON_UPDATE_COMMAND_UI et créer un gestionnaire dans l’objet qui gère la mise à jour. Consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md) pour plus d’informations.

Par exemple, pour mettre à jour une commande Effacer tout dans le menu Edition de votre programme, utilisez la **propriétés** fenêtre pour ajouter une entrée de table des messages dans la classe choisie, une déclaration de fonction pour un gestionnaire de mise à jour de la commande appelée `OnUpdateEditClearAll` dans la classe déclaration et un modèle de fonction vide dans le fichier d’implémentation de la classe. Le prototype de fonction ressemble à ceci :

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

Comme tous les gestionnaires, la fonction montre le **afx_msg** mot clé. Comme les gestionnaires de mise à jour, il prend un seul argument, un pointeur vers un `CCmdUI` objet.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour mettre à jour des objets d’interface utilisateur](../mfc/how-to-update-user-interface-objects.md)

