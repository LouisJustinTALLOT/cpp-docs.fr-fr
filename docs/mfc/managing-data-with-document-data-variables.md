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
ms.openlocfilehash: dc21bd4b3dbe7609a33af4b4f93f15a3f5c9a64e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151993"
---
# <a name="managing-data-with-document-data-variables"></a>Gestion des données avec variables de données de document

Implémenter des données de votre document en tant que variables membres de votre classe de document. Par exemple, le programme Scribble déclare un membre de données de type `CObList` — une liste liée qui stocke des pointeurs vers `CObject` objets. Cette liste est utilisée pour stocker des tableaux de points qui composent un dessin à main levée.

Façon dont vous implémentez les données membres de votre document dépend de la nature de votre application. Pour vous aider, MFC fournit un groupe de « classes de collections » — tableaux, listes et mappages (dictionnaires), y compris les collections basées sur les modèles C++, ainsi que des classes qui encapsulent une variété de types de données courants tels que `CString`, `CRect`, `CPoint`, `CSize`, et `CTime`. Pour plus d’informations sur ces classes, consultez le [vue d’ensemble de la bibliothèque de classes](../mfc/class-library-overview.md) dans le *référence MFC*.

Lorsque vous définissez les données membres de votre document, vous allez ajouter généralement les fonctions membres à la classe de document pour définir et obtenir les éléments de données et effectuer d’autres opérations utiles sur ces derniers.

Les vues d’accéder à l’objet de document à l’aide du pointeur de la vue au document, installé dans la vue au moment de la création. Vous pouvez récupérer ce pointeur dans les fonctions de membre d’une vue en appelant le `CView` fonction membre `GetDocument`. Veillez à effectuer un cast de ce pointeur vers votre propre type de document. Ensuite, vous pouvez accéder membres de documents publics via le pointeur.

Si le transfert fréquent de données nécessite un accès direct ou si vous souhaitez utiliser les membres non publics de la classe de document, vous souhaiterez que votre affichage de classe friend (en termes de C++) de la classe de document.

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](../mfc/using-documents.md)
