---
description: 'En savoir plus sur : dérivation d’une classe de document à partir de CDocument'
title: Dérivation d'une classe de document de CDocument
ms.date: 11/04/2016
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
ms.openlocfilehash: 9f6dccb5400ba0e62b2f11a3c2d4074cb9bb2f25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327881"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Dérivation d'une classe de document de CDocument

Les documents contiennent et gèrent les données de votre application. Pour utiliser la classe de document fournie par l’Assistant Application MFC, vous devez effectuer les opérations suivantes :

- Dérivez une classe de `CDocument` pour chaque type de document.

- Ajoutez des variables membres pour stocker les données de chaque document.

- `CDocument` `Serialize` Fonction membre de remplacement dans votre classe de document. `Serialize` écrit et lit les données du document vers et depuis le disque.

## <a name="other-document-functions-often-overridden"></a>Autres fonctions de document souvent remplacées

Vous pouvez également remplacer d’autres `CDocument` fonctions membres. En particulier, vous devez souvent remplacer [OnNewDocument](reference/cdocument-class.md#onnewdocument) et [OnOpenDocument](reference/cdocument-class.md#onopendocument) pour initialiser les membres de données et les [DeleteContents](reference/cdocument-class.md#deletecontents) du document afin de détruire des données allouées dynamiquement. Pour plus d’informations sur les membres substituables, consultez la classe [CDocument](reference/cdocument-class.md) dans la *référence MFC*.

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](using-documents.md)
