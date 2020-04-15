---
title: Initialisation et nettoyage des documents et vues
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
ms.openlocfilehash: 3c92d60941cd6542bd0d6c27e8a879dc85e3a3d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377203"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Initialisation et nettoyage des documents et vues

Utilisez les lignes directrices suivantes pour l’initialisation et le nettoyage après vos documents et points de vue :

- Le cadre MFC initialise les documents et les points de vue; vous initialisez toutes les données que vous y ajoutez.

- Le cadre se nettoie à mesure que les documents et les points de vue sont proches; vous devez traiter de toute mémoire que vous avez allouée sur le tas à partir des fonctions membres de ces documents et vues.

> [!NOTE]
> Rappelez-vous que l’initialisation pour l’ensemble de l’application est préférable `CWinApp`dans votre remplacement de la fonction membre [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) de la classe , et le nettoyage pour l’ensemble de l’application est préférable dans votre remplacement de la `CWinApp` fonction membre [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).

Le cycle de vie d’un document (et sa fenêtre de cadre et de vue ou vues) dans une application MDI est le suivant:

1. Lors de la création dynamique, le constructeur de documents est appelé.

1. Pour chaque nouveau document, on [s’appelle OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) ou [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) du document.

1. L’utilisateur interagit avec le document tout au long de sa vie. En règle générale, cela se produit lorsque l’utilisateur travaille sur les données du document à travers la vue, en sélectionnant et en modifiant les données. La vue transmet les modifications au document pour le stockage et la mise à jour d’autres vues. Pendant ce temps, le document et la vue peuvent gérer les commandes.

1. Le cadre appelle [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) à supprimer les données spécifiques à un document.

1. Le destructeur du document est appelé.

Dans une application SDI, l’étape 1 est effectuée une fois, lorsque le document est créé pour la première fois. Ensuite, les étapes 2 à 4 sont effectuées à plusieurs reprises chaque fois qu’un nouveau document est ouvert. Le nouveau document réutilise l’objet document existant. Enfin, l’étape 5 est effectuée à la fin de l’application.

## <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Initialisation des documents et vues](../mfc/initializing-documents-and-views.md)

- [Nettoyage des documents et vues](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Voir aussi

[Document/Afficher l’architecture](../mfc/document-view-architecture.md)
