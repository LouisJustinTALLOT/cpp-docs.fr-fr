---
description: 'En savoir plus sur : macro ON_UPDATE_COMMAND_UI'
title: ON_UPDATE_COMMAND_UI, macro
ms.date: 09/06/2019
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 394ee2679e84c09223f61d485fac3e628dec7145
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112165"
---
# <a name="on_update_command_ui-macro"></a>ON_UPDATE_COMMAND_UI, macro

Pour connecter un objet d’interface utilisateur à un gestionnaire de mise à jour de commande dans un objet cible de commande, ouvrez **affichage de classes**, cliquez avec le bouton droit sur la classe à laquelle le gestionnaire sera ajouté, puis choisissez **Assistant classe**. Recherchez l’ID de l’objet d’interface utilisateur dans la liste située à gauche, puis choisissez **UPDATE_COMMAND_UI** dans le volet droit, puis cliquez sur **Ajouter un gestionnaire**. Cela crée une fonction de gestionnaire dans la classe et ajoute l’entrée appropriée dans la table des messages. Pour plus d’informations, consultez [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md) . Vous pouvez spécifier des messages supplémentaires à gérer dans le volet **messages** .

Par exemple, pour mettre à jour une commande Clear All dans le menu Edition de votre programme, utilisez l' **Assistant classe** pour ajouter une entrée de table des messages dans la classe sélectionnée, une déclaration de fonction pour un gestionnaire de mise à jour de commande appelé `OnUpdateEditClearAll` dans la déclaration de classe et un modèle de fonction vide dans le fichier d’implémentation de la classe. Le prototype de la fonction se présente comme suit :

[!code-cpp[NVC_MFCDocView#2](codesnippet/cpp/on-update-command-ui-macro_1.h)]

Comme tous les gestionnaires, la déclaration de fonction affiche le mot clé **afx_msg** . Comme tous les gestionnaires de mise à jour, il accepte un argument, un pointeur vers un `CCmdUI` objet.

## <a name="see-also"></a>Voir aussi

[Comment : mettre à jour des objets User-Interface](how-to-update-user-interface-objects.md)
