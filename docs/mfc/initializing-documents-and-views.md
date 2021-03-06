---
description: 'En savoir plus sur : initialisation des documents et des vues'
title: Initialisation des documents et vues
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: ea0840faefac0ae5a8b4cee0fe3b707a92737c70
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208032"
---
# <a name="initializing-documents-and-views"></a>Initialisation des documents et vues

Les documents étant créés de deux manières différentes, votre classe de document doit prendre en charge les deux. Tout d’abord, l’utilisateur peut créer un nouveau document vide avec la commande fichier nouveau. Dans ce cas, initialisez le document dans votre remplacement de la fonction membre [OnNewDocument](reference/cdocument-class.md#onnewdocument) de la classe [CDocument](reference/cdocument-class.md). Deuxièmement, l’utilisateur peut utiliser la commande ouvrir du menu fichier pour créer un nouveau document dont le contenu est lu à partir d’un fichier. Dans ce cas, initialisez le document dans votre remplacement de la fonction membre [OnOpenDocument](reference/cdocument-class.md#onopendocument) de la classe `CDocument` . Si les deux initialisations sont identiques, vous pouvez appeler une fonction membre commune à partir des deux substitutions, ou `OnOpenDocument` appeler `OnNewDocument` pour initialiser un document propre, puis terminer l’opération d’ouverture.

Les vues sont créées après la création de leurs documents. Le meilleur moment pour initialiser une vue est une fois que l’infrastructure a fini de créer le document, la fenêtre frame et la vue. Vous pouvez initialiser votre vue en remplaçant la fonction membre [OnInitialUpdate](reference/cview-class.md#oninitialupdate) de [CView](reference/cview-class.md). Si vous devez réinitialiser ou ajuster tout ce qui se passe chaque fois que le document change, vous pouvez remplacer [OnUpdate](reference/cview-class.md#onupdate).

## <a name="see-also"></a>Voir aussi

[Initialisation et nettoyage des documents et des vues](initializing-and-cleaning-up-documents-and-views.md)
