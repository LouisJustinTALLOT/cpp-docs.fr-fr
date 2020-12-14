---
description: 'En savoir plus sur : utilisation de contrôles communs dans une boîte de dialogue'
title: Utilisation de contrôles communs dans une boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
ms.openlocfilehash: 73395ae5b3542f338f3783fd5f0c41116821fed6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202403"
---
# <a name="using-common-controls-in-a-dialog-box"></a>Utilisation de contrôles communs dans une boîte de dialogue

Les contrôles communs Windows peuvent être utilisés dans les [boîtes de dialogue](../mfc/dialog-boxes.md), les affichages de formulaire, les vues d’enregistrement et toute autre fenêtre basée sur un modèle de boîte de dialogue. La procédure suivante, avec quelques modifications mineures, fonctionne également pour les formes.

## <a name="procedures"></a>Procédures

#### <a name="to-use-a-common-control-in-a-dialog-box"></a>Pour utiliser un contrôle commun dans une boîte de dialogue

1. Placez le contrôle sur le modèle de boîte de dialogue [à l’aide de l’éditeur de boîtes de dialogue](../mfc/using-the-dialog-editor-to-add-controls.md).

1. Ajoutez une variable membre qui représente le contrôle à une classe de boîte de dialogue. Dans la boîte de dialogue **Ajouter une variable membre** , cochez la case **contrôle variable** et vérifiez que l’option **contrôle** est sélectionnée pour la **catégorie**.

1. Si ce contrôle commun fournit des données au programme, déclarez la variable membre supplémentaire dans la classe de la boîte de dialogue pour gérer les valeurs d'entrée.

    > [!NOTE]
    >  Vous pouvez ajouter ces variables membres à l’aide du menu contextuel de Affichage de classes (consultez [Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md)).

1. Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) pour votre classe de boîte de dialogue, définissez les conditions initiales du contrôle commun. Grâce à la variable membre créée à l'étape précédente, utilisez les fonctions membres pour définir la valeur initiale et d'autres paramètres. Consultez les descriptions suivantes des contrôles pour plus d'informations sur les paramètres.

   Vous pouvez également utiliser l' [échange de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md) (DDX) pour initialiser des contrôles dans une boîte de dialogue.

1. Dans les gestionnaires des contrôles de la boîte de dialogue, utilisez la variable membre pour manipuler le contrôle. Consultez les descriptions suivantes des contrôles pour plus d'informations sur les méthodes.

    > [!NOTE]
    >  La variable membre existe uniquement si la boîte de dialogue existe. Vous ne pouvez pas interroger le contrôle sur les valeurs d'entrée après la fermeture de la boîte de dialogue. Pour utiliser les valeurs d'entrée d'un contrôle commun, substituez `OnOK` dans la classe de la boîte de dialogue. Dans votre fichier, interrogez le contrôle des valeurs d'entrée et stockez les valeurs des variables membres de la classe de boîte de dialogue.

    > [!NOTE]
    >  Vous pouvez également utiliser l'échange de données de boîtes de dialogue pour définir et récupérer des valeurs de contrôles dans une boîte de dialogue.

## <a name="remarks"></a>Notes

L'ajout des contrôles communs à une boîte de dialogue entraîne le non fonctionnement de la boîte de dialogue. Pour plus d’informations sur la gestion de cette situation, reportez-vous à [la boîte de dialogue Ajout de contrôles à une boîte](../windows/adding-editing-or-deleting-controls.md) de dialogue.

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

- [Ajout manuel de contrôles à une boîte de dialogue au lieu d'utiliser l'éditeur de boîtes de dialogue](../mfc/adding-controls-by-hand.md)

- [Dérivation de mon contrôle à partir de l'un des contrôles communs Windows standard](../mfc/deriving-controls-from-a-standard-control.md)

- [Utilisation d'un contrôle commun en tant que fenêtre enfant](../mfc/using-a-common-control-as-a-child-window.md)

- [Réception de messages de notification à partir d'un contrôle](../mfc/receiving-notification-from-common-controls.md)

- [Utilisation de l'échange de données de boîtes de dialogue (DDX)](../mfc/dialog-data-exchange-and-validation.md)

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](../mfc/making-and-using-controls.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
