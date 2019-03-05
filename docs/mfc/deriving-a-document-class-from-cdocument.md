---
title: Dérivation d'une classe de document de CDocument
ms.date: 11/04/2016
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
ms.openlocfilehash: 5998d5707eb741be0e8ac270f6ac5ce77a9ff8d8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272059"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Dérivation d'une classe de document de CDocument

Les documents contiennent et gérer les données de votre application. Pour utiliser la classe de document fournie par l’Assistant Application MFC, vous devez procédez comme suit :

- Dérivez une classe de `CDocument` pour chaque type de document.

- Ajoutez des variables membres pour stocker les données de chaque document.

- Substituer `CDocument`de `Serialize` fonction membre dans votre classe de document. `Serialize` écrit et lit les données du document vers et depuis le disque.

## <a name="other-document-functions-often-overridden"></a>Autres fonctions de Document souvent remplacées

Vous pouvez également remplacer d’autres `CDocument` fonctions membres. En particulier, vous devrez souvent substituer [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) et [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) pour initialiser les membres de données du document et [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) à détruire données allouées dynamiquement. Pour plus d’informations sur les membres substituables, consultez la classe [CDocument](../mfc/reference/cdocument-class.md) dans le *référence MFC*.

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](../mfc/using-documents.md)
