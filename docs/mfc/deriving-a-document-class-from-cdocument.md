---
title: Dérivation d’une classe de Document de CDocument | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b45dadbc062bbba61cdcb4c883f91943b1b18ba8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429823"
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

