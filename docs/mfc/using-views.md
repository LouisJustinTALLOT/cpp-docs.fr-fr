---
description: 'En savoir plus sur : utilisation des vues'
title: Utilisation de vues
ms.date: 11/04/2016
helpviewer_keywords:
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
ms.openlocfilehash: f17855c1389da44630a21830033c4457db6e3703
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236644"
---
# <a name="using-views"></a>Utilisation de vues

Les responsabilités de la vue sont d’afficher graphiquement les données du document pour l’utilisateur et d’accepter et d’interpréter les entrées d’utilisateur en tant qu’opérations sur le document. Vos tâches d’écriture dans votre classe d’affichage sont les suivantes :

- Écrivez la fonction membre [OnDraw](../mfc/reference/cview-class.md#ondraw) de votre classe d’affichage, qui restitue les données du document.

- Connectez les messages Windows appropriés et les objets d’interface utilisateur tels que les éléments de menu aux fonctions membres du gestionnaire de messages dans la classe de vue.

- Implémentez ces gestionnaires pour interpréter l’entrée d’utilisateur.

En outre, vous devrez peut-être substituer d’autres `CView` fonctions membres dans votre classe de vue dérivée. En particulier, vous souhaiterez peut-être remplacer [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) pour effectuer une initialisation spéciale pour la vue et [OnUpdate](../mfc/reference/cview-class.md#onupdate) pour effectuer tout traitement spécial nécessaire juste avant que la vue ne se redessine lui-même. Pour les documents multipages, vous devez également remplacer [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) pour initialiser la boîte de dialogue Imprimer avec le nombre de pages à imprimer et d’autres informations. Pour plus d’informations sur la substitution des `CView` fonctions membres, consultez la classe [CView](../mfc/reference/cview-class.md) dans la *référence MFC*.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Classes d'affichage dérivées disponibles dans MFC](../mfc/derived-view-classes-available-in-mfc.md)

- [Dessiner dans un affichage](../mfc/drawing-in-a-view.md)

- [Interprétation de l'entrée utilisateur via un affichage](../mfc/interpreting-user-input-through-a-view.md)

- [Rôle de la vue dans l’impression](../mfc/role-of-the-view-in-printing.md)

- [Défilement et mise à l'échelle des affichages](../mfc/scrolling-and-scaling-views.md)

- [Initialisation et nettoyage des documents et affichages](../mfc/initializing-and-cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](../mfc/document-view-architecture.md)<br/>
[CFormView, classe](../mfc/reference/cformview-class.md)<br/>
[Vues des enregistrements (accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Contournement du mécanisme de sérialisation](../mfc/bypassing-the-serialization-mechanism.md)
