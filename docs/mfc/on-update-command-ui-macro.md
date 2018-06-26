---
title: ON_UPDATE_COMMAND_UI (macro) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_UPDATE_COMMAND_UI
dev_langs:
- C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43caffe53be180221b4145a03df7cfc41c31828e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928636"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI, macro
Utilisez le **propriétés** fenêtre pour connecter un objet d’interface utilisateur à un gestionnaire de mise à jour de la commande dans un objet cible de commande. Il sera automatiquement connecter des ID de l’objet de l’interface utilisateur à la macro ON_UPDATE_COMMAND_UI et créer un gestionnaire dans l’objet qui gère la mise à jour. Consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md) pour plus d’informations.  
  
 Par exemple, pour mettre à jour une commande Effacer tout dans le menu Edition de votre programme, utilisez la **propriétés** fenêtre pour ajouter une entrée de table des messages dans la classe choisie, une déclaration de fonction pour un gestionnaire de mise à jour de la commande appelée `OnUpdateEditClearAll` dans la classe déclaration et un modèle de fonction vide dans le fichier d’implémentation de la classe. Le prototype de fonction ressemble à ceci :  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]  
  
 Comme tous les gestionnaires, la fonction affiche les **afx_msg** (mot clé). Comme le gestionnaires de mise à jour, il prend un seul argument, un pointeur vers un `CCmdUI` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour mettre à jour des objets d’interface utilisateur](../mfc/how-to-update-user-interface-objects.md)

