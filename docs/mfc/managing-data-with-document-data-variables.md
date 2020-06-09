---
title: Gestion des données avec variables de données de document
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
ms.openlocfilehash: 3d845b0fc3d00369d44c21c04a3fb7e3b8d6189e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618323"
---
# <a name="managing-data-with-document-data-variables"></a>Gestion des données avec variables de données de document

Implémentez les données de votre document en tant que variables membres de votre classe de document. Par exemple, le programme Scribble déclare un membre de données de type `CObList` , une liste liée qui stocke des pointeurs vers des `CObject` objets. Cette liste est utilisée pour stocker des tableaux de points qui composent un dessin de ligne à main levée.

La façon dont vous implémentez les données membres de votre document dépend de la nature de votre application. Pour vous aider, MFC fournit un groupe de « classes de collection » (tableaux, listes et mappages), y compris des collections basées sur des modèles C++, ainsi que des classes qui encapsulent un large éventail de types de données courants tels que,,, `CString` `CRect` `CPoint` `CSize` et `CTime` . Pour plus d’informations sur ces classes, consultez la [vue d’ensemble](class-library-overview.md) de la bibliothèque de classes dans la *référence MFC*.

Lorsque vous définissez les données de membre de votre document, vous ajoutez généralement des fonctions membres à la classe de document pour définir et récupérer des éléments de données et effectuer d’autres opérations utiles sur ceux-ci.

Vos vues accèdent à l’objet document à l’aide du pointeur de la vue sur le document, installé dans la vue au moment de la création. Vous pouvez récupérer ce pointeur dans les fonctions membres d’une vue en appelant la `CView` fonction membre `GetDocument` . Veillez à effectuer un cast de ce pointeur vers votre propre type de document. Vous pouvez ensuite accéder aux membres du document public par le biais du pointeur.

Si le transfert de données fréquent requiert un accès direct ou si vous souhaitez utiliser les membres non publics de la classe de document, vous souhaiterez peut-être que votre vue classe un ami (en termes C++) de la classe de document.

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](using-documents.md)
