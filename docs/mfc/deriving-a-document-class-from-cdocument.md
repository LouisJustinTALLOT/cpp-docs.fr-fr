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
ms.openlocfilehash: 399230446977636cc8769efe32b8f86fad466b83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616116"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Dérivation d'une classe de document de CDocument

Les documents contiennent et gèrent les données de votre application. Pour utiliser la classe de document fournie par l’Assistant Application MFC, vous devez effectuer les opérations suivantes :

- Dérivez une classe de `CDocument` pour chaque type de document.

- Ajoutez des variables membres pour stocker les données de chaque document.

- `CDocument` `Serialize` Fonction membre de remplacement dans votre classe de document. `Serialize`écrit et lit les données du document vers et depuis le disque.

## <a name="other-document-functions-often-overridden"></a>Autres fonctions de document souvent remplacées

Vous pouvez également remplacer d’autres `CDocument` fonctions membres. En particulier, vous devez souvent remplacer [OnNewDocument](reference/cdocument-class.md#onnewdocument) et [OnOpenDocument](reference/cdocument-class.md#onopendocument) pour initialiser les membres de données et les [DeleteContents](reference/cdocument-class.md#deletecontents) du document afin de détruire des données allouées dynamiquement. Pour plus d’informations sur les membres substituables, consultez la classe [CDocument](reference/cdocument-class.md) dans la *référence MFC*.

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](using-documents.md)
