---
title: Éléments de liste et listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: cae387dc028df46a7891e68d49f5f0c5a89126c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571039"
---
# <a name="list-items-and-image-lists"></a>Éléments de liste et listes d'images

Un « élément » dans un contrôle de liste ([CListCtrl](../mfc/reference/clistctrl-class.md)) se compose d’une icône, une étiquette et éventuellement d’autres informations (en « sous-éléments »).

Les icônes des éléments de contrôle de liste sont contenus dans les listes d’images. Une liste d’images contient les icônes en taille réelle utilisées en mode icône. Une liste d’images deuxième, facultatif, contient les versions réduites des icônes de mêmes pour une utilisation dans d’autres vues du contrôle. Une troisième liste facultative contient des images de « état », telles que des cases à cocher, pour l’affichage devant les petites icônes dans certaines vues. Une quatrième liste facultative contient des images qui sont affichées dans les éléments d’en-tête individuels du contrôle de liste.

> [!NOTE]
>  Si un contrôle list view est créé avec le style LVS_SHAREIMAGELISTS, vous êtes responsable de la destruction des listes d’images quand ils ne sont plus en cours d’utilisation. Spécifiez ce style si vous attribuez la même image de listes à plusieurs contrôles d’affichage de liste ; Sinon, plusieurs contrôles peuvent essayer de détruire la même liste d’images.

Pour plus d’informations sur les éléments de liste, consultez [List View Image Lists](/windows/desktop/Controls/using-list-view-controls) et [éléments et sous-éléments](/windows/desktop/Controls/using-list-view-controls) dans le SDK Windows. Consultez également la classe [CImageList](../mfc/reference/cimagelist-class.md) dans le *référence MFC* et [utilisation de CImageList](../mfc/using-cimagelist.md) dans cette série d’articles.

Pour créer un contrôle de liste, vous devez fournir des listes d’images à utiliser lorsque vous insérez des nouveaux éléments dans la liste. L’exemple suivant illustre cette procédure, où *lequel m_pImagelist* est un pointeur de type `CImageList` et *m_listctrl* est un `CListCtrl` membre de données.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Toutefois, si vous ne souhaitez pas afficher des icônes dans votre affichage de liste ou d’un contrôle de liste, vous n’avez pas besoin listes d’images.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

