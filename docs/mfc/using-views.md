---
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
ms.openlocfilehash: 81668f7409f2b1a4480bde958dc06ce1156e03fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411420"
---
# <a name="using-views"></a>Utilisation de vues

Les responsabilités de la vue sont pour afficher graphiquement les données du document à l’utilisateur et pour accepter et d’interpréter l’entrée d’utilisateur en tant qu’opérations sur le document. Vos tâches d’écriture de votre classe d’affichage sont :

- Écrire votre classe d’affichage [OnDraw](../mfc/reference/cview-class.md#ondraw) fonction membre, ce qui rend les données du document.

- Connecter des messages Windows appropriés et les objets d’interface utilisateur tels que des éléments de menu aux fonctions membres de gestionnaire de messages dans la classe d’affichage.

- Implémentez ces gestionnaires pour interpréter les entrées utilisateur.

En outre, vous devrez peut-être substituer d’autres `CView` fonctions membres dans votre classe d’affichage dérivé. En particulier, vous souhaitez remplacer [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) pour effectuer une initialisation spéciale pour la vue et [OnUpdate](../mfc/reference/cview-class.md#onupdate) pour effectuer tout traitement spécial nécessaire juste avant que la vue se redessine. Pour les documents multipages, vous devez également substituer [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) pour initialiser la boîte de dialogue d’impression avec le nombre de pages à imprimer et d’autres informations. Pour plus d’informations sur la substitution `CView` fonctions membres, consultez la classe [CView](../mfc/reference/cview-class.md) dans le *référence MFC*.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Classes d’affichage dérivées disponibles dans MFC](../mfc/derived-view-classes-available-in-mfc.md)

- [Dessin dans une vue](../mfc/drawing-in-a-view.md)

- [Interprétation de l’entrée utilisateur via une vue](../mfc/interpreting-user-input-through-a-view.md)

- [Le rôle de la vue dans l’impression](../mfc/role-of-the-view-in-printing.md)

- [Défilement et mise à l’échelle des vues](../mfc/scrolling-and-scaling-views.md)

- [Initialisation et nettoyage des documents et vues](../mfc/initializing-and-cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](../mfc/document-view-architecture.md)<br/>
[CFormView, classe](../mfc/reference/cformview-class.md)<br/>
[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Ignorer le mécanisme de sérialisation](../mfc/bypassing-the-serialization-mechanism.md)
