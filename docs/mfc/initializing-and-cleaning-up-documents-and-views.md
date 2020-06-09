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
ms.openlocfilehash: c5beed5618d4fa991160ad1688a5a686aeaa842f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626364"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Initialisation et nettoyage des documents et vues

Utilisez les instructions suivantes pour initialiser et nettoyer après vos documents et vues :

- L’infrastructure MFC initialise les documents et les vues ; vous initialisez toutes les données que vous y ajoutez.

- L’infrastructure nettoie les documents et les vues. vous devez libérer toute mémoire que vous avez allouée sur le tas à partir des fonctions membres de ces documents et vues.

> [!NOTE]
> Rappelez-vous que l’initialisation de l’application entière est effectuée au mieux dans votre remplacement de la fonction membre [InitInstance](reference/cwinapp-class.md#initinstance) de la classe `CWinApp` , et que le nettoyage de l’application entière s’effectue de manière optimale dans votre remplacement de la `CWinApp` fonction membre [ExitInstance](reference/cwinapp-class.md#exitinstance).

Le cycle de vie d’un document (et de sa fenêtre frame et de sa vue ou de ses vues) dans une application MDI est le suivant :

1. Pendant la création dynamique, le constructeur de document est appelé.

1. Pour chaque nouveau document, le [OnNewDocument](reference/cdocument-class.md#onnewdocument) ou [OnOpenDocument](reference/cdocument-class.md#onopendocument) du document est appelé.

1. L’utilisateur interagit avec le document tout au long de sa durée de vie. En général, cela se produit lorsque l’utilisateur travaille sur des données de document via la vue, en sélectionnant et en modifiant les données. La vue transmet les modifications apportées au document pour le stockage et la mise à jour d’autres vues. Pendant ce temps, le document et la vue peuvent traiter les commandes.

1. L’infrastructure appelle [DeleteContents](reference/cdocument-class.md#deletecontents) pour supprimer des données spécifiques à un document.

1. Le destructeur du document est appelé.

Dans une application SDI, l’étape 1 est exécutée une seule fois, lors de la création du document. Les étapes 2 à 4 sont ensuite exécutées à plusieurs reprises à chaque fois qu’un nouveau document est ouvert. Le nouveau document réutilise l’objet de document existant. Enfin, l’étape 5 est exécutée lorsque l’application se termine.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Initialisation des documents et vues](initializing-documents-and-views.md)

- [Nettoyage des documents et vues](cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](document-view-architecture.md)
